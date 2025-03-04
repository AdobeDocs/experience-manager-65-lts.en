---
title: Pre-Upgrade Maintenance Tasks

description: Learn about the pre-upgrade tasks recommended for AEM.


contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading

docset: aem65

feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
---
# Pre-Upgrade Maintenance Tasks{#pre-upgrade-maintenance-tasks}

Before beginning your upgrade, it is important to follow these maintenance tasks to ensure that the system is ready and can be rolled back should issues occur:

* [Index Definitions](#index-definitions)
* [Ensure Sufficient Disk Space](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Fully Back Up AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Generate The quickstart.properties File](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Configure Workflow and Audit Log Purging](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [Install, Configure, and Run The Pre-Upgrade Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Remove Updates From The /install Directory](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Stop Any Cold Standby Instances](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Disable Custom Scheduled Jobs](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Execute Offline Revision Cleanup](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Execute Datastore Garbage Collection](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Upgrade the Database Schema If Needed](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Rotate Log Files](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Index Definitions {#index-definitions}

Make sure that you have installed the required index definitions released with AEM 6.5 Sevice Packs provided with AEM Service Pack 22 at a minimum (Refer to [AEM 6.5 servicepack release notes](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes) for more information). 

## Ensure Sufficient Disk Space {#ensure-sufficient-disk-space}

When executing the upgrade, ensure that there is enough disk space.

## Fully Back Up AEM {#fully-back-up-aem}

AEM should be fully backed up before beginning the upgrade. Make sure to back up your repository, application installation, datastore, and Mongo instances if applicable. For more information on backing up and restoring an AEM instance, see [Backup and Restore](/help/sites-administering/backup-and-restore.md).

## Generate The quickstart.properties File {#generate-quickstart-properties}

When starting AEM from the jar file, a `quickstart.properties` file is generated under `crx-quickstart/conf`. If AEM has only been started with the start script in the past, this file is not present and the upgrade fails. Make sure to check for the existence of this file and restart AEM from the jar file if it is not present.

## Configure Workflow and Audit Log Purging {#configure-wf-audit-purging}

The `WorkflowPurgeTask` and `com.day.cq.audit.impl.AuditLogMaintenanceTask` tasks require separate OSGi configurations and cannot work without them. If they fail during pre-upgrade task execution, missing configurations is the most likely reason. Therefore, make sure to add OSGi configurations for these tasks or remove them altogether from the pre-upgrade optimization tasks list if you do not wish to run them. Documentation for configuring workflow purging tasks can be found at [Administering Workflow Instances](/help/sites-administering/workflows-administering.md) and audit log maintenance task configuration can be found at [Audit Log Maintenance in AEM 6](/help/sites-administering/operations-audit-log.md).


## Install, Configure, and Run The Pre-Upgrade Tasks {#install-configure-run-pre-upgrade-tasks}

Pre-upgrade maintenance tasks that before had to be performed manually are being optimized and automated. The pre-upgrade maintenance optimization enables a unified way to trigger these tasks and be able to inspect their result on demand.

### How to Use It {#how-to-use-it}

The `PreUpgradeTasksMBean` OSGI component comes preconfigured with a list of pre-upgrade maintenance tasks that can be run all at once. You can configure the tasks by following the below procedure:

1. Go to the Web Console by browsing to *https://serveraddress:serverport/system/console/configMgr*

1. Search for "**preupgradetasks**", then click the first matching component. The full name of the component is `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Modify the list of maintenance tasks that must be run as shown below:

   ![1487758925984](assets/1487758925984.png)

Below is a description of the run mode that each maintenance task is designed for.

| Task  |  Notes |
|---|---|
|  WorkflowPurgeTask | Must configure the Adobe Granite Workflow Purge Configuration OSGi before running. |
|  GenerateBundlesListFileTask |   |
|  RevisionCleanupTask |   |
| com.day.cq.audit.impl.AuditLogMaintenanceTask  | Must configure the Audit Log Purge Scheduler OSGi configuration before running.  |

### Default Configuration of the Pre-Upgrade Health Checks {#default-configuration-of-the-pre-upgrade-health-checks}

The `PreUpgradeTasksMBeanImpl` OSGI component comes pre-configured with a list of pre-upgrade health check tags to execute when the `runAllPreUpgradeHealthChecks` method is called:

* **system** - the tag used by the granite maintenance health checks

* **pre-upgrade** - a custom tag that could be added to all the health checks that you can set to run before an upgrade

**MBean Methods**

The managed bean functionality can be accessed using the [JMX Console](/help/sites-administering/jmx-console.md).

You can access the MBeans by:

1. Going to the JMX Console at *https://serveraddress:serverport/system/console/jmx*
1. Search for **PreUpgradeTasks** and click the result

1. Select any method from the **Operations** section and select **Invoke** in the following window.

Below is a list of all the available methods that the `PreUpgradeTasksMBeanImpl` exposes:

|  Method Name |  Type  |  Descriptio |
|---|---|---|
| runAllPreUpgradeTasks()  | ACTION   |  Runs all the pre-upgrade maintenance tasks in the list.  |
| runPreUpgradeTask(preUpgradeTaskName)  | ACTION  | Runs the pre-upgrade maintenance task with the name given as the parameter.  |
|  getPreUpgradeTaskLastRunTime(preUpgradeTaskName) | ACTION   | Displays the exact running time of the pre-upgrade maintenance task with the name given as the parameter.  |
| getPreUpgradeTaskLastRunState(preUpgradeTaskName)  |  ACTION | Displays the last running state of the pre-upgrade maintenance task with the name given as the parameter.   |
|  runAllPreUpgradeHealthChecks(shutDownOnSuccess) |  ACTION  | Runs all the pre-upgrade health checks and saves their status in a file named preUpgradeHCStatus.properties in the sling home path. If shutDownOnSuccess is set to true, the AEM instance is shut down, but only if all the pre-upgrade health checks have an OK status. The properties file is used as a precondition for any future upgrade, and the upgrade process is stopped if the pre-upgrade health check execution failed. If you want to ignore the result of the pre-upgrade health checks and launch the upgrade anyway, you can delete the file.  |
|  detectUsageOfUnavailableAPI(aemVersion) | ACTION  | Lists all the imported packages that are no longer satisfied when upgrading to the specified AEM version. The target AEM version must be given as a parameter.  |

>[!NOTE]
>
>The MBean methods can be invoked via:
>
>* The JMX Console
>* Any external application that connects to JMX
>* cURL
>

## Remove Updates From The /install Directory {#remove-updates-install-directory}

>[!NOTE]
>
>Only remove packages from the crx-quickstart/install directory AFTER shutting down the AEM instance. This step is one of the last before starting the in-place upgrade procedure.

Remove any service packs, feature packs, or hotfixes that were deployed through the `crx-quickstart/install` directory on the local file system. Doing so prevents the inadvertent installation of old hotfixes and service packs on top of the new AEM version after the update has completed.

## Stop Any Cold Standby Instances {#stop-tarmk-coldstandby-instance}

If using TarMK cold standby, stop any cold standby instances. Doing so guarantees an efficient way to come back online if there are issues in the upgrade. After the upgrade has completed successfully, the cold standby instances must be rebuilt from the upgraded primary instances.

## Disable Custom Scheduled Jobs {#disable-custom-scheduled-jobs}

Disable any OSGi scheduled jobs that are included in your application code.

## Execute Offline Revision Cleanup {#execute-offline-revision-cleanup}

>[!NOTE]
>
>This step is only necessary for TarMK installations

If using TarMK, you should run Offline Revision Cleanup before upgrading. Doing so makes the repository migration step and subsequent upgrade tasks execute much faster and helps to ensure that Online Revision Cleanup can execute successfully after the upgrade has completed. For information on running Offline Revision Cleanup, see [Performing Offline Revision Cleanup](/help/sites-deploying/revision-cleanup.md#revision-cleanuprevision-cleanup).

## Execute Datastore Garbage Collection {#execute-datastore-garbage-collection}

After running revision cleanup on CRX3 instances, you should run Datastore Garbage Collection to remove any unreferenced blobs in the data store. For instructions, see the documentation on [Data Store Garbage Collection](/help/sites-administering/data-store-garbage-collection.md).

## Rotate Log Files {#rotate-log-files}

Adobe recommends archiving your current log files before beginning your upgrade. Doing so makes it easier to monitor and scan your log files during and after the upgrade to identify and resolve any issues that may occur.
