---
title: AEM 6.5 to AEM 6.5 LTS Content Migration Using Oak-upgrade
description: Learn how to migrate content from AEM 6.5 to AEM 6.5 LTS using the oak-upgrade tool
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
---

# AEM 6.5 to AEM 6.5 LTS Content Migration Using Oak-upgrade {#aem-65-to-aem-65lts-content-migration-using-oak-upgrade}

This document provides a comprehensive guide for upgrading Adobe Experience Manager from version **6.5** to **6.5 LTS**, focusing on content repository migration using the oak-upgrade tool, a powerful utility for transferring content between different repositories with precision and control.

## Prerequisites {#prerequisites}

Before starting the migration, ensure the following requirements are met:

1. Java Compatibility: AEM 6.5 LTS must be installed and configured to run with Java&trade; 17. Once set up, start the AEM instance and verify that all bundles are active and running without issues
1. System Resources: Ensure adequate disk space and memory are available to handle both repositories during the migration process
1. Oak-upgrade Tool: Download the `oak-upgrade` jar from the [official Maven repository](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade). Ensure that the version matches the oak-core version used in AEM 6.5 LTS. Oak-upgrade tool runs on Oracle&reg; Java&trade; 11 or later

## Step by Step Migration Process {#step-by-step-migration-process}

### Stopping AEM 6.5 and AEM 6.5 LTS {#stopping-aem65-and-aem65lts}

Before initiating migration, stop your AEM 6.5 and AEM 6.5 LTS instances. This ensures that the repository is in a stable state and no additional writes occur during the migration.

### Backing up the AEM 6.5 Instance {#backing-up-the-aem65-instance}

Take a full backup of your AEM 6.5 instance if not already done.

### Using the Oak-upgrade Tool for Content Migration {#using-the-oak-upgrade-tool-for-content-migration}

The Oak-Upgrade tool is executed via the command line, as shown here: 

```
java -jar oak-upgrade-*.jar [options] /path/to/source/repository /path/to/destination/repository 
```

Below are the essential commands and options:

**Key Options**

* `--include-paths`: Specify subtrees to include in the migration. See this example for the command usage:

  ```
  java -jar oak-upgrade-*.jar --include-paths=/content/site /old/repository /new/repository
  ```

* `--exclude-paths`: Exclude specific paths from migration. Be cautious while using this option - if the path exists on the target system, it will be removed. See this example for the command usage:

  ```
  java -jar oak-upgrade-*.jar --exclude-paths=/content/old_site /old/repository /new/repository 
  ```

* `--copy-binaries`: By default, oak-upgrade migrates only references to binaries, leaving the actual files in the original blob/data store. As a result, the new repository still relies on the source store for binaries. To migrate binaries along with the repository content, use the `--copy-binaries` parameter to copy all binary data to the new store, as shown below:

  ```
  java -jar oak-upgrade-*.jar \
  --copy-binaries \
  --src-datastore=/old/repository/datastore \
  --datastore=/new/repository/datastore \
  /old/repository \
  /new/repository 
  ```

### Migrating Checkpoints {#migratiing-checkpoints}

When migrating an old SegmentMK repository (pre-Oak 1.6) to a new SegmentMK (Oak  version greater or equal to 1.6), the checkpoints are migrated as well. This allows reindexing to be avoided when the Oak is being run for the first time on the new repository. However, the checkpoints won't be migrated in following cases:

1. Custom include-, exclude- or merge- paths are specified or 
1. The binaries are copied by references, no source datastore is specified and two different checkpoints contain a different binary under the same path.

In the second case oak-upgrade emits following warning and breaks:

```
Checkpoints won't be copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info. 

```

The easiest way to fix this issue is specifying the source datastore in the command line options (for example `--src-datastore` or `--src-s3datastore`).

The warning may also be ignored, but in this case the repository will be fully reindexed on the first startup. It may be a long process, especially for the big instance. Repository won't be usable until the reindexing process is done. Use the `--skip-checkpoints` option to suppress the warning.

You can also offline reindex the repository before starting AEM using [offline reindexing](/help/sites-deploying/upgrade-offline-reindexing.md) avoid full reindexing on first startup.
