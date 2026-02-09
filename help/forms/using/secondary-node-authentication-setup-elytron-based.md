---
title: Secondary Node Authentication Setup (Elytron-based)
description: JBoss EAP 8 uses Elytron to enable secure communication and registration of secondary nodes with the primary Domain Controller.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 212aa75c-7f2a-4140-8051-77643065e429
---
# Secondary Node Authentication Setup (Elytron-based)

## Configure Secondary Node Authentication Using Elytron

JBoss EAP 8 uses **Elytron** to authenticate communication between **primary and secondary nodes** in a clustered deployment. This configuration ensures secure registration and communication of secondary nodes with the primary Domain Controller.

Two setup options are available depending on the environment and security requirements.


## Prerequisites

* A **management user named `secondary`** must be created on the **primary node**.
* Perform this configuration **only on secondary node(s)**.
* Repeat the configuration for **each secondary node** in the cluster.
* **JBoss must be completely stopped** on both primary and secondary nodes.
* All credential store operations must be performed in **offline mode**.

To stop JBoss if it is running:

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux / UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

## Choose a Setup Option

* **Option 1: Quick Setup Using Default Credential Store**
  Recommended for lower environments and testing.

* **Option 2: Custom Credential Store Setup**
  Recommended for production and secure environments.

## Option 1: Quick Setup Using Default Credential Store

**Best suited for:** Development, testing, and quick setup scenarios.

### Overview

* A default credential store file (`cs_secondary_hc.p12`) is preconfigured.
* The default credential store password is already set in `domain.conf`.
* Only the authentication password alias needs to be added.

### Configuration Steps

#### Step 1: Verify Default Credential Store

Confirm the default credential store file exists:

* **Windows**

  ```
  <JBOSS_HOME>\domain\configuration\cs_secondary_hc.p12
  ```

* **Linux**

  ```
  <JBOSS_HOME>/domain/configuration/cs_secondary_hc.p12
  ```

If the file does not exist, use **Option 2**.

#### Step 2: Add Authentication Password Alias

Run the following command from `<JBOSS_HOME>/bin`:

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

> The secret value must match the password used when creating the `secondary` user on the primary node.

#### Step 3: Verify domain.conf Configuration

Verify that the following entry already exists (no changes required):

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=password"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=password"
  ```

#### Step 4: Start the Nodes

1. Start the **primary node** and wait for it to fully initialize.
2. Start the **secondary node**.

### Verification

Check the logs:

* **Primary Node**

  ```
  <JBOSS_HOME>/domain/log/host-controller.log
  ```

  ```
  Registered remote secondary host "secondary"
  ```

* **Secondary Node**

  ```
  Connected to primary host controller
  ```

## Option 2: Custom Credential Store Setup (Production)

**Best suited for:** Production environments requiring enhanced security.

### Configuration Steps

#### Step 1: Remove Default Credential Store (If Present)

If the default credential store exists, rename it:

* **Windows**

  ```
  rename cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

* **Linux**

  ```
  mv cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

#### Step 2: Create Custom Credential Store

From `<JBOSS_HOME>/bin`:

* **Windows**

  ```
  elytron-tool.bat credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

#### Step 3: Add Authentication Password Alias

* **Windows**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

#### Step 4: Update domain.conf

Update the credential store password reference:

* **Windows**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=YourCustomPassword"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=YourCustomPassword"
  ```

#### Step 5: Verify XML Configuration

Ensure `host-secondary.xml` contains the configured credential store and authentication client entries.
No changes are required if the default configuration is present.


#### Step 6: Start the Nodes

1. Start the **primary node** and wait until fully started.
2. Start the **secondary node**.

### Verification

Confirm successful registration using the host-controller logs on both nodes.

## Summary

* **Option 1** provides a quick setup using a preconfigured credential store.
* **Option 2** enables stronger security using a custom credential store password.
* Configuration must be completed **on secondary nodes only**.
* Primary node configuration is reused automatically across the domain.
