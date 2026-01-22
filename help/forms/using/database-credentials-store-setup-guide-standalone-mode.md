---
title: Database Credential Store Setup Guide (Standalone Mode)
description: Find the database credential store setup for AEM Forms JEE on JBoss/Red Hat EAP in standalone mode.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
hide: yes
index: no
hidefromtoc: yes
---

# Database Credential Store Setup Guide (Standalone Mode)

## Overview

This guide covers the **database credential store setup** for AEM Forms JEE on JBoss/Red Hat EAP in **standalone mode**. This is required when performing manual installation.

**This guide covers:**

- Creating the database credential store (`cred-store.p12`)
- Adding database password aliases securely
- Configuring JBoss to use the credential store

**CRITICAL:** These scripts operate in **OFFLINE MODE ONLY**. JBoss must be stopped before running these scripts. The scripts use `embed-server` mode which requires the server to be stopped.

**Note:** This is **not** a complete standalone installation guide. This document assumes:

- JBoss is already installed
- Standalone configuration files (`lc_oracle.xml`, `lc_mysql.xml`, or `lc_mssql.xml`) are already configured
- Database is set up and accessible

If you need complete standalone installation instructions, please refer to the main installation guide.

## Prerequisites

Before running these scripts, ensure:

1. **JBoss MUST be stopped**
   - These scripts work in **OFFLINE MODE ONLY**
   - The scripts use `embed-server` which requires the server to be stopped
   - If JBoss is running, the scripts will fail
   - Check if JBoss is running:
     - Windows: Check Task Manager for `java.exe` process
     - Linux: `ps aux | grep jboss` or `ps aux | grep java`
   - Stop JBoss if running:
     - Press `Ctrl+C` in the terminal where JBoss is running
     - Or kill the process manually

2. **You have the database password ready**

3. **You have decided on a secure password for the credential store**

4. **You know which database configuration file you are using:**
   - `lc_oracle.xml` (for Oracle database)
   - `lc_mysql.xml` (for MySQL database)
   - `lc_mssql.xml` (for Microsoft SQL Server database)

## Setup Steps

### Step 1: Create Database Credential Store

Use the provided scripts to create the database credential store and add all required password aliases.

#### On Windows:

**Script Location:** `create-elytron-cred-standalone.bat`

`batch cd path\to\script\location create-elytron-cred-standalone.bat`

**The script will prompt you for:**
1. **JBOSS_HOME path** (e.g., `C:\Adobe\Adobe_Experience_Manager_Forms\jboss`)
2. **Configuration file name** (e.g., `lc_oracle.xml`, `lc_mysql.xml`, or `lc_mssql.xml`)
3. **Credential store password** (this protects the keystore file - remember this password)
4. **Database password** (your actual database password)

**What the script does:**

- Creates credential store at: `JBOSS_HOME\standalone\configuration\cred-store.p12`
- Temporarily modifies the configuration file to enable credential store creation
- Adds the following aliases with your database password:
  - `EncryptDBPassword`
  - `EncryptDBPassword_IDP_DS`
  - `EncryptDBPassword_EDC_DS`
  - `EncryptDBPassword_AEM_DS`
- Restores the configuration file to its original state
- Verifies all aliases were added successfully

#### On Linux:

**Script Location:** `create-elytron-cred-standalone.sh`

`bash cd /path/to/script/location chmod +x create-elytron-cred-standalone.sh./create-elytron-cred-standalone.sh`

**The script will prompt you for:**

1. **JBOSS_HOME path** (e.g., `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss`)
2. **Configuration file name** (e.g., `lc_oracle.xml`, `lc_mysql.xml`, or `lc_mssql.xml`)
3. **Credential store password** (this protects the keystore file - remember this password)
4. **Database password** (your actual database password)

**What the script does:**

- Creates credential store at: `JBOSS_HOME/standalone/configuration/cred-store.p12`
- Temporarily modifies the configuration file to enable credential store creation
- Adds the following aliases with your database password:
  - `EncryptDBPassword`
  - `EncryptDBPassword_IDP_DS`
  - `EncryptDBPassword_EDC_DS`
  - `EncryptDBPassword_AEM_DS`
- Restores the configuration file to its original state
- Verifies all aliases were added successfully

**Expected Output:**

```
=== JBoss Elytron Credential Store Setup ===
Enter JBOSS_HOME path (e.g. /opt/jboss): /opt/Adobe/Adobe_Experience_Manager_Forms/jboss
Enter configuration file name (e.g. lc_oracle.xml): lc_oracle.xml
Enter credential store password: ********
Confirm credential store password: ********
Enter database password: ********
Creating credential store using JBoss CLI...
Adding aliases to credential store...
Verifying credential store aliases...

All 4 aliases verified successfully!
- EncryptDBPassword
- EncryptDBPassword_IDP_DS
- EncryptDBPassword_EDC_DS
- EncryptDBPassword_AEM_DS

Credential store setup completed successfully!
```

### Step 2: Update Standalone Configuration File

After running the script, you need to configure JBoss to read the credential store password at startup.

#### On Windows:

**File Location:** `<JBOSS_HOME>\bin\standalone.conf.bat`

Example: `C:\Adobe\Adobe_Experience_Manager_Forms\jboss\bin\standalone.conf.bat`

Add or update the following line:

```batch
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourActualPassword123"
```

Replace `YourActualPassword123` with the **credential store password** you used in Step 1.

#### On Linux:

**File Location:** `<JBOSS_HOME>/bin/standalone.conf`

Example: `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss/bin/standalone.conf`

Add or update the following line:

```bash
JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourActualPassword123"
```

Replace `YourActualPassword123` with the **credential store password** you used in Step 1.

### Step 3: Start JBoss

After completing the credential store setup, start JBoss with the appropriate configuration file.

**Note:** For the exact startup commands and procedures to start JBoss in standalone mode, please refer to the **main installation guide**. The startup commands may vary depending on your specific configuration and database type (`lc_oracle.xml`, `lc_mysql.xml`, or `lc_mssql.xml`).

## Verification

### Check Server Logs

**Log Location:**

- Windows: `<JBOSS_HOME>\standalone\log\server.log`
- Linux: `<JBOSS_HOME>/standalone/log/server.log`

**Look for successful startup messages:**

```
INFO  [org.jboss.as.server] WFLYSRV0025: JBoss EAP started
INFO  [org.jboss.as.connector.deployers.jdbc] Bound data source [java:/AdobeDataSource]
```

**No errors related to:**

- Credential store loading
- Database connection
- Missing aliases

## Troubleshooting

### Issue 1: Credential Store Not Found

**Error Message:**

```
ERROR Unable to load credential store
```

**Solution:**

1. Verify the credential store file exists:
   - Windows: `dir <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `ls -l <JBOSS_HOME>/standalone/configuration/cred-store.p12`
2. If missing, re-run the credential store creation script (Step 1)

### Issue 2: Wrong Credential Store Password

**Error Message:**

```
ERROR Unable to load credential store - Invalid password
```

**Solution:**
Verify that the password in `standalone.conf.bat` / `standalone.conf` (Step 2) matches the password used when creating the credential store (Step 1).

**To Fix:**
Edit `standalone.conf.bat` / `standalone.conf` and update the password:

```
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=CorrectPassword"
```

### Issue 3: Database Connection Failed

**Error Message:**

```
ERROR Failed to obtain connection
```

**Solution:**

1. Verify the database password used in the credential store is correct
2. Check that the datasource configuration references the correct alias
3. Verify network connectivity to the database server

**To Recreate Credential Store:**

1. Stop JBoss
2. Delete the existing credential store:
   - Windows: `del <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `rm <JBOSS_HOME>/standalone/configuration/cred-store.p12`
3. Re-run the credential store creation script with the correct database password

### Issue 4: Script Fails During Execution

**Error Message:**

```
ERROR: jboss-cli.bat is not found
```

**Solution:**
Verify that JBOSS_HOME path is correct and points to the JBoss installation directory.

**Error Message:**

```
ERROR: Configuration file not found
```

**Solution:**

1. Verify the configuration file name is correct
2. Check that the file exists in `JBOSS_HOME\standalone\configuration\` directory
3. Ensure you're using the correct database-specific configuration file

## Quick Reference

### Database Credential Store (Standalone Mode)

**Purpose:** Store database passwords securely

**Script:**

- Windows: `create-elytron-cred-standalone.bat`
- Linux: `create-elytron-cred-standalone.sh`

**Creates:**

- File: `standalone/configuration/cred-store.p12`
- Aliases: `EncryptDBPassword`, `EncryptDBPassword_IDP_DS`, `EncryptDBPassword_EDC_DS`, `EncryptDBPassword_AEM_DS`

**Configuration:**

- Variable: `-DCS_PASS=password`
- File: `standalone.conf.bat` (Windows) or `standalone.conf` (Linux)

