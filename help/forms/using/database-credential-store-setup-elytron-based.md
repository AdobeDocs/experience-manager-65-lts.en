---
title: Database Credential Store Setup (Elytron-based)
description: JBoss EAP 8 supports Elytron credential stores for secure database password management in AEM Forms for domain mode setup.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: d7a9502b-8d6a-4d83-9b1f-0c82cbf34b70
---
# Database Credential Store Setup (Elytron-based)

## Configure Database Credential Store Using Elytron

JBoss EAP 8 uses **Elytron credential stores** to securely manage database passwords for AEM Forms deployments. Adobe provides **automated scripts** to simplify the creation and configuration of the Elytron-based credential store in domain mode.


This setup must be completed **before starting the JBoss Domain Controller**.

### Prerequisites

* The **JBoss server must be completely stopped** before running the credential store creation script.
* Credential store creation must be performed in **offline mode only**.

To stop JBoss if it is running:

* **Windows**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux / UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

### Download Scripts

Download the appropriate script based on your operating system:

| Script Name                      | Operating System |
| -------------------------------- | ---------------- |
| `create-elytron-cred-domain.bat` | Windows          |
| `create-elytron-cred-domain.sh`  | Linux / UNIX     |

For Linux, make the script executable:

```
chmod +x create-elytron-cred-domain.sh
```

### Configuration Steps

#### Step 1: Download and Place the Script

Download the appropriate script and place it in the following directory:

```
<JBOSS_HOME>/bin
```

#### Step 2: Run the Script

* **Windows**

  ```
  cd <JBOSS_HOME>\bin
  create-elytron-cred-domain.bat
  ```

* **Linux / UNIX**

  ```
  cd <JBOSS_HOME>/bin
  ./create-elytron-cred-domain.sh
  ```

#### Step 3: Provide Required Information

During execution, the script prompts for the following inputs:

1. **JBOSS_HOME Path**
   Enter the full path to the JBoss installation directory.

2. **Database Configuration File Name**
   Enter one of the following based on your database:

   * `domain_oracle.xml`
   * `domain_mysql.xml`
   * `domain_mssql.xml`

3. **Credential Store Password**
   Enter a strong password to protect the credential store.

   > This password is hidden during input and must be remembered for later steps.

4. **Database Password**
   Enter the actual database connection password.

#### Step 4: Script Execution and Validation

The script performs the following actions automatically:

* Creates `cred-store.p12` in:

  ```
  <JBOSS_HOME>/domain/configuration/
  ```

* Creates the following credential aliases:

  * `EncryptDBPassword`
  * `EncryptDBPassword_IDP_DS`
  * `EncryptDBPassword_EDC_DS`
  * `EncryptDBPassword_AEM_DS`
* Verifies that all aliases are added successfully

Successful execution confirms credential store creation and alias verification.

#### Step 5: Configure JVM Options

Update the JBoss domain startup configuration to provide the credential store password.

* **Linux**
  Edit:

  ```
  <JBOSS_HOME>/bin/domain.conf
  ```

  Add:

  ```
  JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourCredStorePassword"
  ```

* **Windows**
  Edit:

  ```
  <JBOSS_HOME>/bin/domain.conf.bat
  ```

  Add:

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourCredStorePassword"
  ```

Replace `YourCredStorePassword` with the password entered during credential store creation.

The domain configuration files reference this value using the `${CS_PASS}` variable.


#### Step 6: Verify Domain Configuration

Open the database domain configuration file:

```
<JBOSS_HOME>/domain/configuration/<domain_*.xml>
```

Verify that datasources reference the Elytron credential store:

```xml
<security>
    <user-name>your_database_username</user-name>
    <credential-reference store="db-creds" alias="EncryptDBPassword_IDP_DS"/>
</security>
```

Each datasource uses a specific alias:

* **IDP_DS:** `EncryptDBPassword_IDP_DS`
* **EDC_DS:** `EncryptDBPassword_EDC_DS`
* **AEM_DS:** `EncryptDBPassword_AEM_DS`
* **DefaultDS / ExampleDS:** `EncryptDBPassword`

All aliases reference the same database password stored in the credential store.

>[!NOTE]
>
>* Configure the credential store only on the primary node.
>* Secondary nodes automatically use the domain configuration synchronized from the primary node.
