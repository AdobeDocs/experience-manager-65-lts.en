---
title: Upgrade Steps for Application Server Installations
description: Learn how to upgrade instances of AEM that are deployed via Application Servers.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
---
# Upgrade Steps for Application Server Installations {#upgrade-steps-for-application-server-installations}

>[!NOTE]
>
>This page outlines the upgrade procedure for the AEM 6.5 LTS war on WLP (WebSphere Liberty).

## Pre-Upgrade Steps {#pre-upgrade-steps}

Before executing your upgrade, there are several steps that must be completed. See [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md) and [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) for more information. Additionally, make sure that your system meets the requirements for AEM 6.5 LTS. See how Analyzer can help you estimate the complexity of your upgrade and also see make a plan for the upgrade (see [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md) for more information). 

### Migration Prerequisites {#migration-prerequisites}

* **Minimum Required Java version**: Make sure you have installed IBM Sumeru JRE 17 on your WLP server.

### Performing the Upgrade {#performing-the-upgrade}

1. Perform a backup of your instance before starting any upgrade activity.
1. Identify if you need in-place upgrade or sidegrade depending on the version of WLP server that you are using. If your current WLP server supports Servlet 6, then you can perform in-place upgrade and continue with this documentation. Otherwise, you need to perform sidegrade. For the sidegrade, please follow the Content Migration with Oak-Upgrade documentation - [TBD link to be added]
1. Stop the AEM instance. It can typically be done by using this command:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Remove the files and folders that are no longer necessary. The items you need to specifically remove are:

   * The `cq-quickstart-65.war` from the `dropins` folder and the expanded folder typically located at `<path-to-aem-server>/dropins/cq-quickstart-65.war` and `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war` respectively
   * The `launchpad/startup` folder. You can delete it by running the following command in the terminal assuming you are in the server folder: 
   
     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * The `base.jar` file. You can do this by running the following commands:

     ```shell
     find crx-quickstart/launchpad -type f -name 
     "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ``` 

   * The `BootstrapCommandFile_timestamp.txt` file:

      ```shell
      rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
      ```

   * Remove the `sling.options` file by running:

      ```shell
      find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
      ```

   * Remove the `sling.bootstrap.txt` file:

     ```shell
     rm -rf crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Make a backup of the `sling.properties` file (usually present in `crx-quickstart/conf/`) and delete it
1. Change the version of servlet to **6.0** in the `server.xml` file
1. Review the start parameters for the AEM server and make sure to update the parameters according to your system requirements. See [Custom Standalone Install](/help/sites-deploying/custom-standalone-install.md) for more information
1. Install Java 17 and make sure that it is correctly installed by running: 

   ```shell
   java -version
   ```

1. Download the new war 6.5 LTS from Software distribution and copy it to dropins folder located at: `/<path-to-aem-server>/dropins/`
1. Start AEM instance: It can be done typically by using this command:
 
   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```
    
1. In case you have custom changes in `sling.properties`, please follow the below instructions:

   1. Stop the AEM instance by running `<path-to-wlp-directory>/bin/server stop server_name`
   1. Apply your custom `sling.properties` changes to newly generated `sling.properties` file (by referring the backup file created at step 6)
   1. Start the AEM instance. It can be done typically by running: `<path-to-wlp-directory>/bin/server start server_name`

## Deploy Upgraded Codebase {#deploy-upgraded-codebase}

Once the in-place upgrade process has been completed, the updated code base should be deployed. Steps for updating the code base to work in the target version of AEM can be found in the [Upgrade Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md) page.

## Perform Post-Upgrade-Checks-And-Troubleshooting {#perform-post-upgrade-checks-and-troubleshooting}

See [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) for more information.