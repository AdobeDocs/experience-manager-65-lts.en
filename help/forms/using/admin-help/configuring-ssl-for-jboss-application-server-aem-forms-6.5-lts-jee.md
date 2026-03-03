---
title: Configuring SSL for JBoss Application Server (AEM 6.5 LTS JEE)
description: Learn how to configure SSL for JBoss Application Server.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
---

# Configuring SSL for JBoss Application Server (AEM 6.5 LTS JEE)

## Overview

To configure SSL on the JBoss Application Server for Adobe Experience Manager (AEM) 6.5 LTS running on Java EE, you must enable secure HTTPS communication. Enabling SSL encrypts data exchanged between clients and the server, making it a critical security requirement for any production AEM Forms deployment.

The process involves two main stages:

- **Obtaining an SSL credential** — either by generating a self-signed certificate or requesting one from a Certificate Authority (CA).
- **Enabling SSL on JBoss** — using the Elytron subsystem via JBoss CLI commands.

Throughout this guide, the following placeholder values are used:

- `[appserver root]` — the home directory of the JBoss application server running AEM Forms.
- `[type]` — a folder name that varies depending on the type of installation performed.
- `[JAVA_HOME]` — the directory where the JDK is installed.

## Part 1: Create an SSL Credential (Self-Signed)

If you do not have a certificate from a CA, you can generate a self-signed SSL credential using the Java `keytool` utility. This is suitable for development or testing environments.

### Step 1 — Generate the Keystore

Navigate to `[JAVA_HOME]/bin` in a command prompt and run the following command, replacing the values with those appropriate for your environment. The Host Name must be the fully qualified domain name (FQDN) of your application server:

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

When prompted, enter the `keystore_password`. Note that the password for the keystore and the key must be identical.

### Step 2 — Copy the Keystore to the Configuration Directory

Copy the generated keystore to the appropriate configuration folder for your installation type:

```bash
# Windows Single Server
copy keystorename.keystore [appserver root]\standalone\configuration

# Windows Server Cluster
copy keystorename.keystore [appserver root]\domain\configuration

# Linux Single Server
cp keystorename.keystore [appserver root]/standalone/configuration

# Linux Server Cluster
cp keystorename.keystore [appserver root]/domain/configuration
```

### Step 3 — Export the Certificate File

Export the certificate from the keystore using one of the following commands:

```bash
# Single Server
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/standalone/configuration/keystorename.keystore

# Server Cluster
keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [appserver root]/domain/configuration/keystorename.keystore
```

Enter the `keystore_password` when prompted.

### Step 4 — Copy and Verify the Certificate

Copy `AEMForms_cert.cer` to the configuration directory, then verify its contents:

```bash
# Copy (Linux Single Server example)
cp AEMForms_cert.cer [appserver root]/standalone/configuration

# Verify certificate contents (Single Server)
keytool -printcert -v -file [appserver root]/standalone/configuration/AEMForms_cert.cer

# Verify certificate contents (Server Cluster)
keytool -printcert -v -file [appserver root]/domain/configuration/AEMForms_cert.cer
```

### Step 5 — Import the Certificate into the Java Truststore

Before importing, ensure the `cacerts` file is writable:

```bash
# Windows: Right-click cacerts → Properties → deselect Read-only

# Linux:
chmod 777 [JAVA_HOME]/jre/lib/security/cacerts
```

Then import the certificate:

```bash
keytool -import -alias "AEMForms Cert" -file AEMForms_cert.cer \
  -keystore [JAVA_HOME]/jre/lib/security/cacerts
```

When prompted for the password, type `changeit` (the default Java truststore password — check with your administrator if this has been changed). When asked **Trust this certificate? [no]**, type `yes`. You should see a confirmation message: *"Certificate was added to keystore."*

>[!NOTE]
>
> If you are connecting to AEM Forms over SSL from Workbench, you must also install the certificate on the Workbench computer.

## Part 2: Enable SSL on JBoss Using the Elytron Subsystem

With the SSL credential in place, you can now enable HTTPS on JBoss using its Elytron security subsystem via the JBoss CLI. Ensure your keystore file is located in the appropriate configuration directory before proceeding.

>[!NOTE]
>
> On Windows, each CLI command must be entered as a single line with no line breaks. Replace `keystorename.keystore` with your actual filename, and `changeit` with your keystore/key password.

### Step 6a — Create an Elytron Key-Store

```bash
/subsystem=elytron/key-store=aemKeyStore:add(
  path="keystorename.keystore",
  relative-to=jboss.server.config.dir,
  type="JKS",
  credential-reference={clear-text="changeit"})
```

Replace `JKS` with `PKCS12` if your keystore uses that format.

### Step 6b — Create the Elytron Key-Manager

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  credential-reference={clear-text="changeit"})
```

If your keystore contains multiple certificate entries, explicitly specify the alias:

```bash
/subsystem=elytron/key-manager=aemKeyManager:add(
  key-store=aemKeyStore,
  alias="AEMForms Cert",
  credential-reference={clear-text="changeit"})
```

### Step 6c — Update the Server SSL Context

```bash
/subsystem=elytron/server-ssl-context=applicationSSC:write-attribute(
  name=key-manager,
  value=aemKeyManager)
```

### Step 6d — Configure the Undertow HTTPS Listener

Wire the SSL context into Undertow (the JBoss web server) to enable the HTTPS listener:

```bash
/subsystem=undertow/server=default-server/https-listener=https:add(
  socket-binding=https,
  ssl-context=applicationSSC)
```

## Part 3: Restart the Application Server

After completing the Elytron configuration, restart JBoss to apply the changes.

### Turnkey Installations (Windows Services)

- Open **Control Panel > Administrative Tools > Services**.
- Select **JBoss for Adobe Experience Manager forms**.
- Select **Action > Stop** and wait for the service to stop.
- Select **Action > Start**.

### Pre-configured or Manual JBoss Installations

From a command prompt, navigate to `[appserver root]/bin`:

```bash
# Stop the server
Windows: shutdown.bat -S
Linux:   ./shutdown.sh -S

# Wait until JBoss fully shuts down, then start the server
Windows: run.bat -c <profile>
Linux:   ./run.sh -c <profile>
```

## Part 4: Request a Credential from a Certificate Authority

For production environments, you should use a certificate issued by a trusted Certificate Authority (CA). The process involves generating a key pair, creating a Certificate Signing Request (CSR), and then importing the CA-signed certificate.

### Generate the Keystore and Create a CSR

Navigate to `[JAVA_HOME]/bin` and generate the keystore:

```bash
keytool -genkey -dname "CN=Host Name, OU=Group Name, O=Company Name, L=City Name, S=State, C=Country Code" \
  -alias "AEMForms Cert" -keyalg RSA \
  -keypass key_password -keystore keystorename.keystore
```

Then generate the CSR to submit to your CA:

```bash
keytool -certreq -alias "AEMForms Cert" \
  -keystore keystorename.keystore \
  -file AEMFormscertRequest.csr
```

Submit the `.csr` file to your CA. Once you receive the signed certificate back, follow the steps below.

### Import the CA-Signed Certificate

Import the CA root certificate first:

```bash
keytool -import -trustcacerts -file rootcert.pem \
  -keystore keystorename.keystore -alias root
```

If the root certificate is not already trusted by the browser, import it there as well. Then import the CA-signed certificate:

```bash
keytool -import -trustcacerts -file CACertificateName.crt \
  -keystore keystorename.keystore
```

>[!NOTE]
>
> The imported CA-signed certificate will replace any existing self-signed public certificate if one is present in the keystore.

Once the CA certificate is imported, proceed with **Steps 6a–6d** in Part 2 (Elytron configuration), restart the server (Part 3), and verify SSL access.

## Verify SSL Access

After restarting the server, verify that SSL is working correctly by accessing the AEM Forms administration console over HTTPS. The default SSL port for JBoss is `8443`:

```
https://[host name]:8443/adminui
```

If the administration console loads successfully over HTTPS, SSL has been configured correctly. Use port `8443` for all subsequent SSL connections to AEM Forms.
