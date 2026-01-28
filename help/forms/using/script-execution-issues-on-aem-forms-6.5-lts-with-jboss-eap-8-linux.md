---
title: Script Execution Fails on AEM Forms 6.5 LTS with JBoss EAP 8 (Linux)
description: Setting up JBoss EAP 8.0 on a Linux environment, you may encounter certain error while running shell scripts or startup files
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
hide: yes
index: no
hidefromtoc: yes
---

# Script Execution Fails on AEM Forms 6.5 LTS with JBoss EAP 8 (Linux)

## Issue

When setting up **JBoss EAP 8.0 (AEM Forms 6.5.1 LTS)** on a **Linux** environment, you may encounter one of the following errors while running shell scripts or startup files:

```text
/bin/sh^M: bad interpreter
$'\r': command not found
```

These errors occur when shell scripts or configuration files were created or edited on a **Windows** system and contain **CRLF (Carriage Return + Line Feed)** line endings.
Linux systems support only **LF (Line Feed)** line endings, and Windows-style line endings cause script execution failures.

## Applies To

* **JBoss EAP 8.0**
* **Linux / UNIX-based operating systems**

## Troubleshooting Steps

1. **Identify the affected file**

   * Review the error output to identify the `.sh` script or configuration file causing the failure.

2. **Convert the file to Unix format**

   * Use the `dos2unix` utility to convert Windows-style line endings to Unix format:

     ```bash
     dos2unix <file_name>
     ```
   
   * Replace `<file_name>` with the actual script or configuration file throwing the error.

3. **Repeat if required**

   * If multiple scripts are affected, repeat the conversion for all relevant `.sh` files (for example, installer, LCM, or JBoss startup scripts).

4. **Re-run the script**

   * After conversion, re-execute the script to confirm the issue is resolved.

After converting the files to Unix (LF) line endings, the `/bin/sh^M` and `$'\r': command not found` errors are resolved, and JBoss scripts execute successfully on Linux.
