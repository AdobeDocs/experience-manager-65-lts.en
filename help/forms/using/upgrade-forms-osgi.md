---
title: Upgrade to AEM 6.5 Forms LTS on OSGi
description: You can perform a direct upgrade from AEM 6.5.22.0 Forms  to AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
---
# Upgrade to AEM 6.5 Forms LTS on OSGi {#upgrade-to-aem-forms-osgi}

To [upgrade from AEM 6.5 to AEM 6.5 LTS](/help/sites-deploying/upgrade.md), upgrade to AEM 6.5.22.0 Forms or later. A direct upgrade from AEM 6.5.22.0 to AEM 6.5 Forms LTS is supported.  

If you are using AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms or AEM 6.5 Forms, a direct upgrade to AEM 6.5 Forms LTS is not available. For detailed upgrade paths, refer to the [Upgrade Paths](/help/forms/using/upgrade.md) documentation.  

After upgrading to service pack AEM Forms 6.5.22.0, follow these steps to upgrade to AEM 6.5 LTS Forms:

1. Install AEM Forms add-on package. The steps are listed below:

    1. Open [Software Distribution](https://experience.adobe.com/downloads). You require an Adobe ID to log in to the Software Distribution.
    1. Select **[!UICONTROL Adobe Experience Manager]** available in the header menu.
    1. In the **[!UICONTROL Filters]** section:
       1. Select **[!UICONTROL Forms]** from the **[!UICONTROL Solution]** drop-down list.
       1. Select the version and type for the package. You can also use the **[!UICONTROL Search Downloads]** option to filter the results.
    1. Select the package name applicable to your operating system, select **[!UICONTROL Accept EULA Terms]**, and select **[!UICONTROL Download]**.
    1. Open [Package Manager](/help/sites-administering/package-manager.md)  and click **[!UICONTROL Upload Package]** to upload the package.
    1. Select the package and click **[!UICONTROL Install]**.

       You can also download the package using the direct link listed in [AEM Forms releases](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) article.
       
       After the package is installed, you are prompted to restart the AEM instance. **Do not immediately stop the server.** Before stopping the AEM Forms server, wait until the ServiceEvent REGISTERED and ServiceEvent UNREGISTERED messages stop appearing in the &lt;crx-repository&gt;/error.log file and the log is stable. Also note, a few packages can remain in the installed state. You can safely ignore the state of these packages.


       **Restart the AEM instance with the following additional JVM command-line parameters**:
       `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`
       
       If the server is started via a script or service, update it accordingly to include the above so that these are effective after subsequent restarts as well.

        >[!NOTE]
        >
        > It is recommended to use the 'Ctrl + C' command to restart the SDK. Restarting the AEM SDK using alternative methods, for example, stopping Java processes, may lead to inconsistencies in the AEM development environment.

1. Perform post-installation activities.

    * **Run Migration Utility**

      The migration utility makes the adaptive forms and correspondence management assets of earlier versions compatible with AEM 6.5 forms. You can download the utility from AEM Software Distribution. For step-by-step information to configure and use the migration utility, see [migration utility](../../forms/using/migration-utility.md).

      If you are using [Sample for integrating drafts & submissions component](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) with the database and upgrading from a previous version, then run the following SQL queries after performing the upgrade:

      ```sql
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'

      ```

      ```sql
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'

      ```

    * **(If upgrading from AEM 6.2 Forms or previous versions only) Reconfigure Adobe Sign**

      If you had Adobe Sign configured in the previous version of AEM Forms, then reconfigure Adobe Sign from AEM Cloud services. For more details, see [Integrate Adobe Sign with AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md).

    * **Support for jQuery**

      In AEM 6.5 Forms, version of jQuery is updated to 3.2.1 and jQuery UI version is updated to 1.12.1. AEM Form uses JQuery in **noConflict** mode. So, if you are using any other jQuery version, no issues are displayed while performing an upgrade. However, when you upgrade to AEM 6.5 Forms:

        * Ensure that your custom components, if any, are compatible with supported jQuery versions.
        * Remove unsupported APIs from the custom components. See [upgrade guide](https://jquery.com/upgrade-guide/3.0/) for the list of removed APIs. For example, support for the load(), .unload(), and .error() APIs is removed. Use the .on() method in place of aforementioned APIs. For example, change $("img").load(fn) to $("img").on("load", fn).

    * **(If upgrading from AEM 6.2 Forms or previous versions only) Reconfigure analytics and reports**

      In AEM 6.4 Forms, traffic variable for source and success event for impression are not available. So, when you upgrade from AEM 6.2 Forms or previous versions, AEM Forms stops sending data to Adobe Analytics server and analytics reports for adaptive forms are not available. Moreover, AEM 6.4 Forms introduces traffic variable for the version of form analytics and success event for the amount of time spent on a field. So, reconfigure analytics and reports for your AEM Forms environment. For detailed steps, see [Configuring analytics and reports](../../forms/using/configure-analytics-forms-documents.md).

1. Verify that the server is upgraded successfully, all the data is also migrated successfully, and it can operate normally.

    * **Verify the status of the bundles:** Ensure that all the bundles are in active state.
    * **Verify replication and reverse replication:** Publish, fill, and submit a few migrated forms. Verify the submitted data also.
    * **Verify access to admin and developer user interfaces:** Log in to AEM instance from an admin account and verify that you have access to the following URLs:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >In AEM 6.4 Forms, the structure of crx-repository has changed. If upgrade from 6.3 Forms to AEM 6.5 Forms, use the changed paths for customization that you create afresh. For the complete list of changed paths, see [Forms Repository Restructuring in AEM](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).


## Deploying AEM on JBoss EAP 8 (Windows)

### Overview

This guide provides step-by-step instructions for deploying Adobe Experience Manager (AEM) as a standalone OSGi WAR file on JBoss Enterprise Application Platform (EAP) 8 in a Windows environment using JDK 21.

### System Requirements

Before beginning the deployment process, ensure your environment meets the following requirements:

| Component | Requirement |
|-----------|-------------|
| Operating System | Windows Server 2016 or later (64-bit) |
| Java Development Kit | JDK 21 (Oracle or OpenJDK) |
| Application Server | JBoss EAP 8.x |
| AEM Distribution | AEM WAR file (obtained from Adobe) |

>[!NOTE] 
>
> Verify that the `JAVA_HOME` environment variable points to your JDK 21 installation directory.

### Step 1: Install JBoss EAP 8

#### Download JBoss EAP

1. Navigate to the Red Hat Developer portal:  
   [https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. Download the JBoss EAP 8 ZIP distribution for Windows.

#### Extract JBoss EAP

1. Extract the downloaded ZIP file to your preferred installation directory.

2. Note this directory path as `<JBOSS_HOME>` for use throughout this guide.

   **Example:**  
   ```C:\jboss-eap-8.0```

### Step 2: Prepare the AEM WAR File

#### Obtain AEM WAR

Acquire the AEM WAR file from Adobe Software Distribution or your Adobe representative.

#### Rename WAR File

Rename the WAR file to reflect your desired URL context path:

```
cq-quickstart.war
```

>[!IMPORTANT]
>
> The WAR filename determines the application's URL context. For example, `cq-quickstart.war` will be accessible at `/cq-quickstart`.


### Step 3: Configure the AEM WAR

All configuration modifications must be completed **before** deploying to JBoss.

#### Create Working Directory

1. Create a temporary working directory:

   ```
   C:\aem\war-config
   ```

2. Copy `cq-quickstart.war` into this directory.

#### Extract WAR Contents

1. Open **Command Prompt** and navigate to your working directory:

   ```cmd
   cd C:\aem\war-config
   ```

2. Extract the WAR file:

   ```cmd
   jar -xvf cq-quickstart.war
   ```

   This creates a directory structure with `WEB-INF` and other application files.

### Step 4: Configure JBoss Deployment Descriptor

#### Create Deployment Structure File

1. Navigate to the `WEB-INF` directory within your extracted WAR:

   ```cmd
   cd WEB-INF
   ```

2. Create a new file named `jboss-deployment-structure.xml`.

3. Add the following XML content:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jboss-deployment-structure xmlns="urn:jboss:deployment-structure:1.2">
       <deployment>
           <dependencies>
               <module name="jdk.unsupported" />
           </dependencies>
       </deployment>
   </jboss-deployment-structure>
   ```

4. Save and close the file.

**Purpose:** This configuration provides access to JDK internal modules required by AEM.

### Step 5: Configure Multipart Upload Settings

>[!NOTE]
>
> Step 5 is applicable only to **AEM Forms**. If you are setting up **AEM only**, you can skip this step.


#### Modify web.xml

1. Open `WEB-INF\web.xml` in a text editor.

2. Locate the `<servlet>` section containing the run mode configuration:

   ```xml
   <!-- Set the runmode per default to author -->
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

3. Replace the closing `</servlet>` tag and preceding line with:

   ```xml
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <multipart-config>
       <max-file-size>1048576000</max-file-size>
       <max-request-size>1048576000</max-request-size>
       <file-size-threshold>0</file-size-threshold>
   </multipart-config>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

4. Save and close `web.xml`.

**Purpose:** These settings enable large file uploads (up to 1 GB) for AEM Forms and Digital Asset Management.

### Step 6: Repackage the WAR File

After completing all configuration changes, repackage the WAR file.

1. Navigate back to the working directory containing the extracted contents:

   ```cmd
   cd C:\aem\war-config
   ```

2. Create the new WAR file:

   ```cmd
   jar -cvf cq-quickstart.war *
   ```

>[!IMPORTANT]
>
> Perform this step only once, after all configurations are complete.

### Step 7: Deploy and Start AEM

#### Deploy WAR to JBoss

1. Copy the repackaged `cq-quickstart.war` to the JBoss deployments directory:

   ```
   <JBOSS_HOME>\standalone\deployments
   ```

   **Example:**
   ```C:\jboss-eap-8.0\standalone\deployments```

#### Configure JVM Settings (Optional but Recommended)

Before starting JBoss, configure JVM memory settings:

1. Open `<JBOSS_HOME>\bin\standalone.conf.bat` in a text editor.

1. Modify or add the following line to set heap memory:

   ```batch
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=512m"
   ```

>[!NOTE] 
>
> Adjust memory values based on your server capacity and AEM requirements.

1. Save and close the file.

#### Start JBoss EAP

1. Open **Command Prompt** as **Administrator**.

1. Navigate to the JBoss bin directory:

   ```cmd
   cd <JBOSS_HOME>\bin
   ```

   **Example:**
   ```cmd cd C:\jboss-eap-8.0\bin```

1. Start the JBoss server:

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

   **Parameters:**
   * `-b 0.0.0.0` — Binds the server to all network interfaces
   * `-bmanagement 0.0.0.0` — Binds the management interface to all network interfaces

#### Monitor Deployment

Watch the console output for deployment messages. Successful deployment is indicated by:

```
Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
```

### Step 8: Access AEM

Once deployment is complete and AEM has fully started:

**AEM Author URL:**
```http://<server-ip>:8080/cq-quickstart```

**Default Credentials:**

* Username: `admin`
* Password: `admin`

**Important:** Change the default password immediately after first login.

### Troubleshooting

#### Common Issues

| Issue | Solution |
|-------|----------|
| Deployment fails with ClassNotFoundException | Verify `jboss-deployment-structure.xml` is properly configured |
| OutOfMemoryError during startup | Increase heap memory in `standalone.conf.bat` |
| AEM does not start after deployment | Check JBoss logs in `<JBOSS_HOME>\standalone\log\server.log` |
| Cannot access AEM in browser | Verify firewall settings allow port 8080 |

#### Log Files

* **JBoss Server Log:** `<JBOSS_HOME>\standalone\log\server.log`
* **AEM Error Log:** Available through AEM Web Console after startup at  
  `http://<server-ip>:8080/cq-quickstart/system/console`

### Additional Configuration

#### Configuring Run Modes

To change AEM run modes (author/publish), modify the `sling.run.modes` parameter in `WEB-INF\web.xml` before repackaging the WAR:

```xml
<init-param>
    <param-name>sling.run.modes</param-name>
    <param-value>publish</param-value>
</init-param>
```

#### Production Recommendations

For production environments:

* Configure SSL/TLS certificates in JBoss
* Set up AEM replication agents
* Configure dispatcher for load balancing
* Enable automated backups
* Implement monitoring and alerting

### Related Documentation

* [JBoss EAP 8 Documentation](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0)
* [Adobe Experience Manager Documentation](https://experienceleague.adobe.com/docs/experience-manager-65.html)
* [AEM Installation and Deployment Guide](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

### Document Information

| Field | Value |
|-------|-------|
| Last Updated | February 2026 |
| AEM Version | 6.5+ (LTS) |
| JBoss Version | EAP 8.x |
| JDK Version | 21 |
| Platform | Windows |


