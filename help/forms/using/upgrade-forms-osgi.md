---
title: Upgrade to AEM 6.5 Forms LTS on OSGi
description: You can perform a direct upgrade from AEM 6.5.22.0 Forms  to AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
---
# Upgrade to AEM 6.5 Forms LTS on OSGi {#upgrade-to-aem-forms-osgi}

After [upgrading from AEM 6.5 to AEM 6.5 LTS](/help/sites-deploying/upgrade.md), you can upgrade your AEM 6.5.22.0 Forms version. A direct upgrade is supported from AEM 6.5.22.0 to AEM 6.5 Forms LTS.  

If you are using AEM 6.0 Forms, AEM 6.1 Forms, or AEM 6.2 Forms, a direct upgrade to AEM 6.5 Forms is not available. You must first upgrade to AEM 6.2 Forms, then proceed to AEM 6.3 Forms or AEM 6.4 Forms before upgrading to AEM 6.5 Forms. For detailed upgrade steps, refer to the [Previous Upgrades](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/upgrade-aem-forms/upgrade) documentation.  

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

1. Restart the AEM instance.

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
