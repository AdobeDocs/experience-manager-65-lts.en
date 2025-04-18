---
title: Storage Elements in AEM 6.5 LTS
description: Learn about the node storage implementations available in AEM 6.5 LTS and how to maintain the repository.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: e51842b5-fa91-42d2-a490-5a7e867dada7
---
# Storage Elements in AEM 6.5 LTS{#storage-elements-in-aem}

This article covers the following:

* [Overview of Storage in AEM 6.5 LTS](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Maintaining the Repository](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Overview of Storage in AEM 6.5 LTS {#overview-of-storage-in-aem}

One of the most important changes in AEM 6.5 LTS are the innovations at the repository level.

Currently, there are two node storage implementations available in AEM 6.5 LTS: Tar storage, and MongoDB storage.

### Tar Storage {#tar-storage}

#### Running a freshly installed AEM instance with Tar Storage {#running-a-freshly-installed-aem-instance-with-tar-storage}

By default, AEM 6.5 LTS uses the Tar storage to store nodes and binaries, using the default configuration options. You can manually configure its storage settings by doing the following:

1. Download the AEM 6.5 LTS quickstart jar and place it in a new folder.
1. Unpack AEM by running:

   `java -jar <aem-65-lts>.jar -unpack`

1. Create a folder named `crx-quickstart\install` in the installation directory.

1. Create a file called `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` in the newly created folder.

1. Edit the file and set the configuration options. The following options are available for Segment Node Store, which is the basis of AEM's Tar storage implementation:

    * `repository.home`: Path to repository home under which various repository-related data is stored. By default segment files would be stored under the crx-quickstart/segmentstore directory.
    * `tarmk.size`: Maximum size of a segment in MB. The default is 256 MB.

1. Start AEM.

### Mongo Storage {#mongo-storage}

>[!NOTE]
>
>Minimum supported version of Mongo is Mongo 6.

#### Running a freshly installed AEM instance with Mongo Storage {#running-a-freshly-installed-aem-instance-with-mongo-storage}

AEM 6.5 LTS can be configured to run with MongoDB storage by following the below procedure:

1. Download the AEM 6.5 LTS quickstart jar and place it into a new folder.
1. Unpack AEM by running the following command:

   `java -jar <aem-65-lts>.jar -unpack`

1. Make sure that MongoDB is installed and an instance of `mongod` is running. For more info, see [Installing MongoDB](https://docs.mongodb.org/manual/installation/).
1. Create a folder named `crx-quickstart\install` in the installation directory.
1. Configure the node store by creating a configuration file with the name of the configuration that you want to use in the `crx-quickstart\install` directory.

   The Document Node Store (which is the basis for AEM's MongoDB storage implementation) uses a file called `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Edit the file and set your configuration options. The following options are available:

    * `mongouri`: The [MongoURI](https://docs.mongodb.org/manual/reference/connection-string/) required to connect to Mongo Database. The default is `mongodb://localhost:27017`
    * `db`: Name of the Mongo database. By default new AEM 6.5 LTS installations use **aem-author** as the database name.
    * `cache`: The cache size in megabytes. This cache size is distributed among various caches used in DocumentNodeStore. The default is 256.
    * `changesSize`: Size in MB of capped collection used in Mongo for caching the diff output. The default is 256.
    * `customBlobStore`: Boolean value indicating that a custom data store is used. The default is false.

1. Create a configuration file with the PID of the data store you want to use and edit the file to set the configuration options. For more info, see [Configuring Node Stores and Data Stores](/help/sites-deploying/data-store-config.md).

1. Start the AEM 6.5 LTS jar with a MongoDB storage backend by running:

   ```shell
   java -jar <aem-65-lts>.jar -r crx3,crx3mongo
   ```

   Where the backend run mode is **`-r`**, the example starts with MongoDB support.

#### Disabling Transparent Huge Pages {#disabling-transparent-huge-pages}

Red Hat&reg; Linux&reg; uses a memory management algorithm called Transparent Huge Pages (THP). While AEM performs fine-grained reads and writes, THP is optimized for large operations. Therefore, it is recommended that you disable THP both on Tar and Mongo storage. To disable the algorithm, follow these steps:

1. Open the `/etc/grub.conf` file in the text editor of your choice.
1. Add the following line to the **grub.conf** file:

   ```
   transparent_hugepage=never
   ```

1. Finally, check if the setting has taken effect by running:

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   If THP is disabled, the output of the above command should be:

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>Consult the following resources:
>
>* For more information regarding Transparent Huge Pages on Red Hat&reg; Linux&reg;, consult the following article from the Red Hat&reg; Customer Portal: [How to use, monitor, and disable transparent hugepages in Red Hat Enterprise Linux 6 ,7 and 8?](https://access.redhat.com/solutions/46111)
>* For Linux&reg; tuning tips, see [Performance Optimization](/help/sites-deploying/configuring-performance.md).
>

## Maintaining the Repository {#maintaining-the-repository}

Each update to the repository creates a content revision. As a result, with each update the size of the repository grows. To avoid uncontrolled repository growth, old revisions must be cleaned up to free disk resources. This maintenance functionality is called Revision Cleanup. The Revision Cleanup mechanism reclaims disk space by removing obsolete data from the repository. For further details about Revision Cleanup, read the [Revision Cleanup page](/help/sites-deploying/revision-cleanup.md).
