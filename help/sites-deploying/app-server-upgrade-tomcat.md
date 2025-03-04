---
title: Upgrade Steps for Application Server Installations (Tomcat)
description: Learn how to upgrade instances of AEM that are deployed via Tomcat.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
---
# Upgrade Steps for Application Server Installations (Tomcat) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>This page outlines the upgrade procedure for the AEM 6.5 LTS war on Tomcat.

## Pre-Upgrade Steps {#pre-upgrade-steps}

Before executing your upgrade, there are several steps that must be completed. See [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md) and [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) for more information. Additionally, make sure that your system meets the [requirements for AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) and see [upgrade planning considerations](/help/sites-deploying/upgrade-planning.md) and how [Analyzer](/help/sites-deploying/pattern-detector.md) can help you estimate the complexity.


### Migration Prerequisites {#migration-prerequisites}

* **Minimum Required Java version**: Make sure you have installed Oracle&reg; JRE 17 on your Tomcat server. 
* **Tomcat server**: The version of the Tomcat server required for 6.5 LTS is **11.0.x**.

### Performing the Upgrade {#performing-the-upgrade}

All the examples in this procedure use Tomcat as the Application Server and imply that you have a working version of AEM already deployed. The procedure is meant to document upgrades performed from AEM version **6.5** to **6.5 LTS**. 

1. If AEM 6.5 is already deployed, check that the bundles are functioning correctly by accessing: *`https://<serveraddress:port>/system/console/bundles`*
1. Next, stop AEM 6.5. This can be done from the Tomcat App Manager at: *`https://<serveraddress:port>/manager/html`*
1. Make sure that you have completed the [pre-upgrade](#pre-upgrade-steps) activities like backup of AEM 6.5 server before performing any upgrade activity
1. Install Java 17 and make sure that it is correctly installed by running the command:

   ```
   java –version
   ```

1. Set up an AEM 6.5 LTS compatible Tomcat server
1. Review the start parameters for the AEM server and make sure to update the parameters accoding to the system requirements. See [Custom Standalone install](/help/sites-deploying/custom-standalone-install.md) for more information
1. Deploy the newly downloaded 6.5 LTS war on the Tomcat server using Java 17 and start AEM 6.5 LTS Tomcat server by running:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Once the AEM is up and running, make sure all the bundles are in running state by accessing: *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Now stop the AEM 6.5 LTS Tomcat server. In most situations, you can do this by running the `./catalina.sh` script, by running this command from the terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Now migrate your content from AEM 6.5 to AEM 6.5 LTS using this tutorial: [AEM 6.5 to AEM 6.5 LTS Content Migration Using Oak-upgrade](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Once the content has been migrated, apply any custom changes required in the `sling.properties` file
1. Start the AEM 6.5 LTS Tomcat server by running:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Monitor the error logs while AEM starts up to check that there are no errors and AEM is running smoothly
1. Once AEM 6.5 LTS has started, check that the bundles are functioning correctly by accessing: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Deploy Upgraded Codebase {#deploy-upgraded-codebase}

Once the upgrade process has been completed, the updated code base should be deployed. Steps for updating the code base to work in the target version of AEM can be found in [Upgrade Code and Customizations page](/help/sites-deploying/upgrading-code-and-customizations.md).

## Perform Post-Upgrade-Checks-And-Troubleshooting {#perform-post-upgrade-checks-and-troubleshooting}

See [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
