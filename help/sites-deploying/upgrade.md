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
# Upgrading to Adobe Experience Manager (AEM) 6.5 LTS {#upgrading-to-aem}

>[!NOTE]
>The upgrade to AEM 6.5 LTS is supported from the last 6 Service packs.

This section covers upgrading an AEM installation to AEM 6.5 LTS:

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

Foundation layer now supports Java 17, incorporating latest open-source bundles from Apache Sling, Felix, and Jackrabbit Oak. Additionally, the packaging of the AEM 6.5 LTS uber-jar has changed. Additionally, a few legacy features have been removed from AEM 6.5 LTS. For more information, refer to [Release notes](/help/release-notes/release-notes.md#whats-new-what-s-new) and [List of Obsolete Bundles Uninstalled After the Upgrade](/help/sites-deploying/obsolete-bundles.md)

AEM 6.5 LTS has a strong focus on backward compatibility of features and comes with an analyzer tool. See [Assessing the Upgrade Complexity with the AEM Analyzer](/help/sites-deploying/pattern-detector.md) for assessment of complexity as you start [planning for the upgrade](/help/sites-deploying/upgrade-planning.md).
