---
title: Upgrade Steps for Application Server Installations (WLP)
description: Learn how to upgrade instances of AEM that are deployed via Webspehere Liberty.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
---
# Upgrade Steps for Application Server Installations (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>This page outlines the upgrade procedure for the AEM 6.5 LTS on WLP (WebSphere&reg; Liberty).

## Pre-Upgrade Steps {#pre-upgrade-steps}

Before executing your upgrade, there are several steps that must be completed. See [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md) and [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) for more information. Additionally, make sure that your system meets the [requirements for AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md).

Check [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md) and how the [AEM Analyzer](/help/sites-deploying/pattern-detector.md) can help you estimate the complexity around upgrading AEM.

### Migration Prerequisites {#migration-prerequisites}

* **Minimum Required Java version**: Make sure you have installed IBM&reg; Sumeru JRE 17 on your WLP server.

### Performing the Upgrade {#performing-the-upgrade}

1. Make sure that you have completed the [pre-upgrade](#pre-upgrade-steps) activities like backup of AEM 6.5 server before performing any upgrade activity
1. Depending on your requirements, choose one of the following upgrade paths:
   1. In-Place Upgrade: If your current WLP server supports Servlet 6, you can perform an in-place upgrade and continue with step 3.
   1. Sidegrade: If you prefer a fresh setup or if your WLP server does not support Servlet 6, set up a new WLP instance with AEM 6.5 LTS and migrate the content using the [AEM 6.5 to AEM 6.5 LTS Content Migration Using Oak-upgrade](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md) guide and skip to [Deploy Upgraded Codebase](#deploy-upgraded-codebase) section.

1. Stop the AEM instance. It can typically be done by using this command:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Remove the files and folders that are no longer necessary. The items you need to specifically remove are:

   * The **cq-quickstart-65.war** from the `dropins` folder and the `expanded` folder typically located at `<path-to-aem-server>/dropins/cq-quickstart-65.war` and `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war` respectively
   * The `launchpad/startup` folder. You can delete it by running the following command in the terminal assuming you are in the server folder: 
   
     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * The `base.jar` file. You can do this by running the following commands:

     ```shell
     find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
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
1. Install Java 17 and make sure that it is correctly installed by running: 

   ```shell
   java -version
   ```
   
1. Review the start parameters for the AEM server and make sure to update the parameters accoding to the system requirements. See [Java 17 Considerations](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations) for more information
1. Download the new 6.5 LTS war and copy it to dropins folder located at: `/<path-to-aem-server>/dropins/`
1. Start AEM instance: It can be done typically by using this command:
 
   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```
    
1. In case you have custom changes in `sling.properties`, please follow the below instructions:

   1. Stop the AEM instance by running `<path-to-wlp-directory>/bin/server stop server_name`
   1. Apply your custom `sling.properties` changes to newly generated `sling.properties` file (by referring the backup file created at step 5)
   1. Start the AEM instance. It can be done typically by running: `<path-to-wlp-directory>/bin/server start server_name`

## Deploy Upgraded Codebase {#deploy-upgraded-codebase}

Once the upgrade process has been completed, the updated code base should be deployed. Steps for updating the code base to work in the target version of AEM can be found in [Upgrade Code and Customizations page](/help/sites-deploying/upgrading-code-and-customizations.md).

## Perform Post-Upgrade-Checks-And-Troubleshooting {#perform-post-upgrade-checks-and-troubleshooting}

See [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
