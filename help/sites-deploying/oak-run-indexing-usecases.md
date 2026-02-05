---
title: Oak-run.jar Indexing Use Cases
description: Learn about the various user cases for performing indexing with the Oak-run tool.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: a7a8a20a-e513-43df-80b7-1e6daf957f20
---
# Oak-run.jar Indexing Use Cases{#oak-run-jar-indexing-use-cases}

Oak-run supports indexing use cases on the command line without having to orchestrate the execution of these use cases by way of AEM's JMX console.

The overarching benefits of using the `oak-run.jar` index command approach for managing Oak indexes are the following:

* Oak-run index command provides a new indexing toolset since the release of AEM 6.4.
* Oak-run decreases time-to-reindex which reduces reindex times on larger repositories.
* Oak-run reduces resource consumption during reindexing in AEM, resulting in overall better system performance.
* Oak-run provides out-of-band reindexing, supporting situations where production must be available, and cannot tolerate maintenance or downtime otherwise required to reindex.

The sections below provide sample commands. Oak-run index command supports all NodeStore and BlobStore setups. The examples provided below are for setups having FileDataStore and SegmentNodeStore.

## Use case 1 - Index consistency check {#usercase1indexconsistencycheck}

This use case is related to index corruption. Sometimes, it was not possible to determine which of the indexes are corrupt. Therefore, Adobe has provided tooling that:

* Performs index consistency checks on all indexes and provides a report on which indexes are valid and which are not valid.
* The tooling is usable even if AEM is not accessible;
* It is easy to use.

Use `--index-consistency-check` to check for corrupt indexes:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

This operation generates a report in `indexing-result/index-consistency-check-report.txt`. See below for a sample report:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Benefits {#uc1benefits}

Support and System Administrators can use the tooling to identify corrupt indexes quickly and reindex them.

## Use case 2 - Index statistics {#usecase2indexstatistics}

For diagnosing some of the cases around query performance, Adobe often required existing index definition, index-related statistics from the customer setup. To make troubleshooting easier, Adobe has created tooling that does the following:

1. Dump all index definition present on the system in a single JSON file;

1. Dump important statistics from existing indexes;

1. Dump index contents for offline analysis;

1. It is usable even if AEM is not accessible

You can perform the above operations using the following index commands:

* `--index-info` - Collects and dumps various statistics related to the indexes

* `--index-definitions` - Collects and dumps index definitions

* `--index-dump` - Dumps index content

See below an example of how the commands work in practice:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

The reports would be generated in `indexing-result/index-info.txt` and `indexing-result/index-definitions.json`

In addition, the same details are provided by way of the Web Console and would be part of the configuration dump zip. They can be accessed at the following location:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Benefits {#uc2benefits}

This tooling enables the gathering of all required details related to indexing or query issues quickly and reduce the time spent in extracting this information.

## Use case 3 - Reindexing {#usecase3reindexing}

Depending on the [scenarios](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing), sometimes, reindexing must be performed. Currently, you reindex by setting the `reindex` flag to `true` in the index definition node using CRXDE or the Index Manager user interface. After you set the flag, reindexing runs asynchronously. After the flag is set, reindexing is done asynchronously.

Some points to note around reindexing:

* Reindexing is lot slower on `DocumentNodeStore` setups compared to `SegmentNodeStore` setups where all content is local;

* With the current design, while reindexing happens, the async indexer is blocked and all other async indexes become stale and do not get updated during indexing. As a result, if the system is in use, users may not see up-to-date results;
* Reindexing involves traversal of the whole repository which can put a high load on the AEM setup and thus impact the end user experience;
* For a `DocumentNodeStore` installation where reindexing may take a considerable amount of time, a Mongo database connection failure during the operation can interrupt indexing. In that case, you must restart indexing from scratch.


* Sometimes, reindexing can take a long time because of text extraction. Such an issue can occur when it is specific for setups that have lots of PDF files, where the time spent on text extraction can impact indexing time.

To meet these objectives, the Oak-run index tooling supports different modes for reindexing which can be used as required. The Oak-run index command provides the following benefits:

* **out-of-band reindexing** - Oak-run reindexing can be done separately from a running AEM setup and thus, it minimizes the impact on the AEM instance that is in use;

* **out-of-lane reindexing** - The reindexing takes place without impacting indexing operations. The async indexer can continue to index other indexes;

* **Simplified reindex for DocumentNodeStore installations** - For `DocumentNodeStore` installations, reindexing can be done with a single command which ensures that reindexing is done in the most optimal way;

* **Supports updating index definitions and introducing new index definitions**

### Reindex - DocumentNodeStore {#reindexdocumentnodestore}

For `DocumentNodeStore` installations, you can perform reindexing using a single Oak-run command:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

This operation provides the following benefits:

* Minimal impact on running AEM instances. Most of the reads can be done from secondary servers and running AEM caches are not adversely impacted due to all the traversal required for reindexing;
* Users can also provide a JSON of a new or updated index by way of the `--index-definitions-file` option.

### Reindex - SegmentNodeStore {#reindexsegmentnodestore}

For `SegmentNodeStore` installations reindexing can be done in one of the following ways:

#### Online reindex - SegmentNodeStore {#onlinereindexsegmentnodestore}

Follow the established way where reindexing is done by way of setting `reindex` flag.

#### Online reindex - SegmentNodeStore - The AEM Instance is Running {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

For `SegmentNodeStore` installations, only one process can access segment files in read-write mode. As such, some operations in Oak-run indexing require additional manual steps being taken involving the following:

1. Step text.
1. Connect the `oak-run` to the same repository used by AEM in read-only mode.
1. Perform indexing using the following as an example:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Finally, import the created index files by way of the `IndexerMBean#importIndex` operation from the path where Oak-run saved the indexing files after running the above command.

In this scenario, you do not have to stop the AEM server or provision any new instance. However, as indexing involves traversal of the whole repository it would increase the I/O load on the installation, negatively impacting runtime performance.

#### Online reindex - SegmentNodeStore - The AEM instance is shut down {#onlinereindexsegmentnodestoreaeminstanceisdown}

For `SegmentNodeStore` installations, you can perform reindexing using a single Oak-run command. However, the AEM instance must be shut down.

You can trigger reindexing with the following command:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

The difference between this approach and the one explained above is that checkpoint creation and index import are done automatically. The downside is that AEM must be down during the process.

#### Out of band reindex - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In this use case, you can perform reindexing on a cloned setup to minimize impact on the running AEM instance:

1. Create a checkpoint by way of a JMX operation. Go to the [JMX Console](/help/sites-administering/jmx-console.md) and search for `CheckpointManager`. Then, click the **createCheckpoint(long p1)** operation using a high value for expiration in seconds (for example, **2592000**).
1. Copy the `crx-quickstart` folder to a new machine.
1. Perform reindex by way of Oak-run index command.

1. Copy the generated index files to an AEM server.

1. Import the index files by way of JMX.

Under this use case, the Data Store must be accessible from another instance, which may not be possible when `FileDataStore` resides on a cloud-based storage solution like EBS. This situation excludes the scenario where `FileDataStore` is also cloned. If the index definition does not perform fulltext indexing, then access to `DataStore` is not required.

## Use case 4 - Updating index definitions {#usecase4updatingindexdefinitions}

Currently, you can ship index definition changes by way of the [ACS Ensure Index](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html) package. You can ship the index definitions in a content package, then perform reindexing by setting the `reindex` flag to `true`.


This works well for smaller installations where reindexing does not take a long time. However, for large repositories, reindexing is done in a considerably larger amount of time. For such cases, you can now use the Oak-run index tooling.

Oak-run now supports providing index definitions in JSON format and creation of index in out-of-band mode where no changes are performed on a live instance.

The process to consider for this use case is the following:

1. A developer would update the index definitions on a local instance and then generate an index definition JSON file by way of the `--index-definitions` option.
1. The updated JSON is then given to the System Administrator.
1. System Administrator follows the out-of-band approach and prepares the index on a different installation.
1. When completed, the generated index files are imported on a running AEM installation.
