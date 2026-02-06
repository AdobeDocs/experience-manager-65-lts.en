---
title: Upgrade Steps for Application Server Installations (Tomcat)
description: Learn how to upgrade instances of AEM that are deployed via Tomcat.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 7f8de16f-9e9a-4d37-9978-d26c496b911c
---
# Upgrade Steps for Application Server Installations (Tomcat - Inplace upgrade) {#upgrade-steps-for-application-server-installations-tomcat-inplace}

>[!NOTE]
>
>This page outlines the upgrade procedure (Inplace upgrade) from AEM 6.5 LTS to AEM 6.5 LTS Servicepack on Tomcat. For upgrading from AEM 6.5 to 6.5 LTS, [refer here](/help/sites-deploying/app-server-upgrade-tomcat.md).

## Pre-Upgrade Steps {#pre-upgrade-steps}

Before executing your upgrade, there are several steps that must be completed. See [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) for more information. Additionally, make sure that your system meets the [requirements for AEM 6.5 LTS Servicepack](/help/sites-deploying/technical-requirements.md) and see [upgrade planning considerations](/help/sites-deploying/upgrade-planning.md).


### Migration Prerequisites {#migration-prerequisites}

* **Minimum Required Java version**: Make sure you have installed Oracle&reg; JRE 17/21 on your Tomcat server. 
* **Tomcat server**: The supported versions of the Tomcat server for AEM 6.5 LTS and its ServicePacks are **10.0.x** and **10.1.x**.

### Performing the Upgrade {#performing-the-upgrade}

All the examples in this procedure use Tomcat as the Application Server and imply that you have a working version of AEM 6.5 LTS already deployed. The procedure is meant to document upgrades performed from AEM version **6.5** LTS to **6.5 LTS** Servicepack. 

1. If AEM 6.5 LTS is already deployed, check that the bundles are functioning correctly by accessing: *`https://<serveraddress:port>/system/console/bundles`*
1. Next, stop AEM 6.5 LTS. This can be done from the Tomcat App Manager at: *`https://<serveraddress:port>/manager/html`*
1. Make sure that you have completed the [pre-upgrade](#pre-upgrade-steps) activities like backup of AEM 6.5 LTS server before performing any upgrade activity
1. Stop the AEM 6.5 LTS Tomcat server. In most situations, you can do this by running the `./catalina.sh` script, by running this command from the terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Remove the files and folders that are no longer necessary. The items you need to specifically remove are:

   * The **cq-quickstart-65.war** file and the `cq-quickstart-65` folder from `webapps` folder typically located at `<path-to-aem-server>/webapps`
   * The `launchpad/startup` folder. You can delete it by running the following command in the terminal assuming you are in the server folder:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/startup
     ```

   * The `base.jar` file. You can do this by running the following commands:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ``` 

   * The `BootstrapCommandFile_timestamp.txt` file:

      ```shell
      rm -f <path-to-aem-server>/bin/crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
      ```

   * Remove the `sling.options` file by running:

      ```shell
      find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
      ```

   * Remove the `sling.bootstrap.txt` file:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Make a backup of the `sling.properties` file (usually present in `<path-to-aem-server>/bin/crx-quickstart/launchpad/`) and delete it
1. Copy the AEM 6.5 LTS Servicepack war file into `<path-to-aem-server>/webapps` folder
1. Start the AEM 6.5 LTS Tomcat server by running:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Monitor the error logs while AEM starts up to check that there are no errors and AEM is running smoothly
1. Once AEM 6.5 LTS has started, check that the bundles are functioning correctly by accessing: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Perform Post-Upgrade-Checks-And-Troubleshooting {#perform-post-upgrade-checks-and-troubleshooting}

See [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) for more information.
