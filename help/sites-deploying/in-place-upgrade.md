---
title: Performing an In-Place Upgrade
description: Learn how to perform an in-place upgrade for AEM 6.5 LTS.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: c7351625-b29e-45a7-b966-e7c0f56d4f22
---
# Performing an In-Place Upgrade {#performing-an-in-place-upgrade}

>[!NOTE]
>
>This page outlines the in-place upgrade procedure for AEM 6.5 LTS. If you have an installation that is deployed to an application server, see [Upgrade Steps for Application Server Installations](/help/sites-deploying/app-server-upgrade.md).

## Pre-Upgrade Steps {#pre-upgrade-steps}

Before executing your upgrade, there are several steps that must be completed. See [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md) and [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) for more information. Additionally, make sure that your system meets the [requirements for AEM 6.5 LTS](/help/sites-deploying/technical-requirements.md) and see [upgrade planning considerations](/help/sites-deploying/upgrade-planning.md) and how [Analyzer](/help/sites-deploying/pattern-detector.md) can help you estimate the complexity.

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migration Prerequisites {#migration-prerequisites}

* **Minimum Required Java version:** Make sure you have Oracle's Java&trade; 17/21 installed on your system.

## Preparation of the AEM Quickstart jar file {#prep-quickstart-file}

1. Download the new AEM 6.5 LTS jar file

1. [Determine the correct upgrade start command](#determining-the-correct-upgrade-start-command)

1. Stop the instance if it is running

1. Use new AEM 6.5 LTS jar to replace the old one outside the `crx-quickstart` folder

1. Take a backup of the `sling.properties` file (usually present in the `crx-quickstart/conf/`), then delete it

1. Unpack the new quickstart jar by running:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

1. If custom sling.properties need to be applied, create a fresh local AEM instance and retrieve the sling.properties file from its crx-quickstart/conf directory. Apply the required custom changes to this file, then copy it to the crx-quickstart/conf directory of the AEM instance being upgraded. If there are no custom properties, this step can be skipped.

<!-- Alexandru: drafting temporarily

## Content Repository Migration {#content-repository-migration}

This migration is not required if you are upgrading from AEM 6.3. For versions older than 6.3, Adobe provides a tool that can be used to migrate the repository to the new version of the Oak Segment Tar present in AEM 6.3. It is provided as part of the quickstart package and is mandatory for any upgrades that will be using TarMK. Upgrades for environments that are using MongoMK do not require repository migration. For more information on what the benefits of the new Segment Tar format are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

The actual migration is performed using the standard AEM quickstart jar file, executed with a new `-x crx2oak` option which executes the crx2oak tool to simplify the upgrade and make it more robust.

>[!NOTE]
>
>If you are performing TarMK repository content migration using the CRX2Oak Quickstart extension, you might remove the **samplecontent** runmode by adding the following to the migration command line:
>
>* `--promote-runmode nosamplecontent`
>

To determine the command that you should run, use the following command:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Where `<<YOUR_PROFILE>>` and `<<ADDITIONAL_FLAGS>>` are replaced with the profile and flags listed in the following table:

<table>
 <tbody>
  <tr>
   <td><strong>Source Repository</strong></td>
   <td><strong>Target Repository</strong></td>
   <td><strong>Profile</strong></td>
   <td><strong>Additional Flags</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 or TarMK with <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK or crx2 with <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-custom-ds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>TarMK with no datastore</td>
   <td>TarMK</td>
   <td>segment-no-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>No migration is needed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Where:**

* `mongo-host` is the MongoDB server IP (for example, 127.0.0.1)

* `mongo-port` is the MongoDB server port (for example: 27017)

* `mongo-database-name` represents the name of the database (for example: aem-author)

**You may also require additional switches for the following scenarios:**

* If you are performing the upgrade on a Windows system where Java memory mapping is not handled correctly, add the `--disable-mmap` parameter to the command.

For additional instructions on using the crx2oak tool, see Using the [CRX2Oak Migration Tool](/help/sites-deploying/using-crx2oak.md). The crx2oak helper JAR can be manually upgraded if needed, by manually replacing it with newer versions after unpacking the quickstart. Its location in the AEM installation folder is: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. The newest version of the CRX2Oak migration tool is available for download from the Adobe Repository at: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

If the migration has completed successfully, the tool will exit with an exit code of zero. Additionally, check for WARN and ERROR messages in the `upgrade.log` file, located under `crx-quickstart/logs` in the AEM installation directory, as these could indicate non-fatal errors that occurred during the migration.

Check the configuration files beneath `crx-quickstart/install` folder. If a migration was necessary these will be updated to reflect the target repository.

**A note on datastores:**

While `FileDataStore` is the new default for AEM 6.3 installations, using an external datastore is not required. While using an external datastore is recommended as a best practice for production deployments, it is not a prerequisite to upgrade. Due to the complexity already present in upgrading AEM, Adobe recommends performing the upgrade without doing a datastore migration. If desired, a datastore migration can be executed afterwards as a separate effort.

## Troubleshooting Migration Issues {#troubleshooting-migration-issues}

Skip this section if you are upgrading from 6.3. While the provided crx2oak profiles should meet the needs of most customers, there are times when additional parameters will be necessary. If you run into an error during your migration, it is possible that there are aspects of your environment that require additional configuration options to be provided. If so, you will likely encounter the following error:

**Checkpoints are not copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info.**

For some reason, the migration process needs access to binaries in the datastore and is unable to find it. To specify your datastore configuration, include the following flags in the `<<ADDITIONAL_FLAGS>>` portion of your migration command:

**For S3 datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Where `/path/to/SharedS3DataStore.config` represents the path to your S3 datastore config file and `/path/to/datastore` represents the path to your S3 datastore.

**For File datastores:**

```shell
--src-datastore=/path/to/datastore
```

Where `/path/to/datastore` represents the path to your File Datastore.

-->

## Performing The Upgrade {#performing-the-upgrade}

**If using S3:**

1. Remove any jars beneath `crx-quickstart/install` associated with an earlier version of the S3 connector.

1. Download the latest release of the 1.60.2 S3 connector from [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) <!-- Alexandru: this is a stub link for now -->

1. Extract the S3 connector (version 1.60.2) and copy the content of the following folders under `crx-quickstart/install`, as follows:

   1. Copy `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/1` under `crx-quickstart/install/1`
   1. Copy `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/15` under `crx-quickstart/install/15` 

Now, start the AEM instance using the new command determined using the information under the [Determining the correct upgrade start command](#determining-the-correct-upgrade-start-command) section.

### Determining the correct upgrade start command {#determining-the-correct-upgrade-start-command}

>[!NOTE]
>
>Support for some of Java 8/11 arguments have been removed in Java 17/21, see [Oracle Java&trade; 17 documents](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html), [Oracle Java&trade; 21 documents](https://docs.oracle.com/en/java/javase/21/docs/specs/man/java.html) and [Java&trade arguments considerations for AEM 6.5 LTS](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations).

To execute the upgrade, it is important to start AEM using the jar file to bring up the instance.

Note that starting AEM from the start script will not start the upgrade. Most customers start AEM using the start script and have customized this start script to include switches for environment configurations such as memory settings, security certificates, and so on. For this reason, Adobe recommends following this procedure to determine the proper upgrade command:

1. On a running AEM instance, execute the following from the command line:

   ```shell
   ps -ef | grep java
   ```

1. Look for the AEM process. It will look something like:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Modify the command by replacing the path to the existing jar ( `crx-quickstart/app/aem-quickstart*.jar` in this case) with the new AEM 6.5 LTS jar that is a sibling of the `crx-quickstart` folder. Using our previous command as an example, our command would be:

   ```shell
   /usr/bin/java -server -Xmx4096m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar <AEM-6.5-LTS.jar> -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   This will ensure that all proper memory settings, custom runmodes, and other environmental parameters are applied for the upgrade. After the upgrade has completed, the instance may be started from the start script on future startups.

## Deploy Upgraded Codebase {#deploy-upgraded-codebase}

Once the in-place upgrade process has been completed, the updated code base should be deployed. Steps for updating the code base to work in the target version of AEM can be found in [Upgrade Code and Customizations page](/help/sites-deploying/upgrading-code-and-customizations.md).

## Perform Post-Upgrade Checks and Troubleshooting {#perform-post-upgrade-check-troubleshooting}

See [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
