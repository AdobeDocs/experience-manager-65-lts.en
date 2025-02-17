---
title: Upgrading to Adobe Experience Manager 6.5
description: Learn about the basics of upgrading an older Adobe Experience Manager (AEM) installation to AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
---
# Upgrading to Adobe Experience Manager (AEM) 6.5.2025 {#upgrading-to-aem}

>[!NOTE]
>The upgrade to AEM 6.5.2025 is supported from the last 6 Service packs.

This section covers upgrading an AEM installation to AEM 6.5:

<!-- Alexandru: drafting for now 

* [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md)
* [Assessing the Upgrade Complexity with Pattern Detector](/help/sites-deploying/pattern-detector.md)
* [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
  This was drafted before: * [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

<!--
* [Upgrade Procedure](/help/sites-deploying/upgrade-procedure.md)
* [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Performing an In-Place Upgrade](/help/sites-deploying/in-place-upgrade.md)
* [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Sustainable Upgrades](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)

-->

For easier reference to the AEM instances involved in these procedures, the following terms are used throughout these articles:

* The *source* instance is the AEM instance that you are upgrading from.
* The *target* instance is the one that you are upgrading to.

## What Has Changed? {#what-has-changed}

### Updates {#updates}

The following are major changes of note over the last several releases of AEM:

1. The Foundation layer has been upgraded to support Java 17 (which comprises open-source layers of bundles from Apache Sling, Apache Felix and Apache Jackrabbit Oak) 

1. The AEM 6.5.2025 jar packaging now supports Jarkarta Servlet APIs specifications 5 and war packaging can be deployed to servlet containers implementing Jakarta Servlet API specifications 5/6

1. Packaging of AEM 6.5.2025 uber-jar has changed. Please refer [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md) for more information.

### Removed Legacy Features/Artifacts {#removed-legacy-features-artifacts}

Following legacy solutions have been removed from AEM 6.5.2025. For more information, please refer to TBD: link to release notes and [List of Obsolete Bundles Uninstalled After the Upgrade](/help/sites-deploying/obsolete-bundles.md) 

1. Social
1. Commerce
1. Screens
1. We-retail
1. Integration of search and promote 

**Removed Artifacts**

1. CRX-explorer
1. Crx2oak
1. Google guava (removed due to security vulnerabilities)
1. Abdera-parser (removed due to security vulnerabilities)
1. jdom (`org.apache.servicemix.bundles.jdom`) (removed due to security vulnerabilities)
1. `com.github.jknack.handlebars` (removed due to security vulnerabilities)

AEM 6.5.2025 has a strong focus on backward compatibility of features and comes with an analyzer tool. See [Assessing the Upgrade Complexity with the AEM Analyzer](/help/sites-deploying/pattern-detector.md) for assessment of complexity as you start planning for the upgrade. For more details about what else has changed, see the complete release notes here. TBD: Link to release notes of AEM 6.5.2025

## Upgrade Overview {#upgrade-overview}

Upgrading AEM is a multi-step, sometimes multi-month process. The following outline has been provided as an overview of what is included in an upgrade project and the content that has been included in this documentation:

![screen_shot_2018-03-30at80708am](assets/screen_shot_2018-03-30at80708am.png)

## Upgrade Flow {#upgrade-flow}

The diagram below captures the overall recommended flow highlight the upgrade approach. Note the reference to the new features that Adobe has introduced. The upgrade should start with the  AEM 6.5.2025 Analyzer tool(see [Assessing the Upgrade Complexity with the AEM Analyzer](/help/sites-deploying/pattern-detector.md)) which should let you decide the path you want to take for compatibility with AEM 6.5 based on the patterns in the generated report.

Aditionally, in your 6.5 development cycle, features introduced under Sustainable Upgrades(see [Sustainable Upgrades](/help/sites-deploying/sustainable-upgrades.md)) help you follow best practices to make future upgrades even more efficient and seamless.

![6_4_upgrade_overviewflowchart-newpage3](assets/6_4_upgrade_overviewflowchart-newpage3.png)
