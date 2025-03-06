---
title: Current Release Notes for Adobe Experience Manager 6.5 LTS
description: These are the current Release Notes for Adobe Experience Manager 6.5 LTS.
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
---
# Current Release Notes for Adobe Experience Manager 6.5 LTS {#release-notes}

## Release Information {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Version | 6.5 LTS |
| Type | Major release |
| General availability date | March 7, 2025 |

## What's New {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS is an upgrade release to the [!DNL Adobe Experience Manager] 6.5 code base. It provides new and enhanced functionality, key customer fixes, high priority customer enhancements, and general bug fixes oriented toward product stabilization. It also includes [!DNL Adobe Experience Manager] 6.5 Service Pack releases up to SP22.

The list below provides an overview - while the subsequent pages list the full details.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

The platform of [!DNL Adobe Experience Manager] 6.5 LTS builds on top of updated versions of the OSGi-based framework (Apache Sling and Apache Felix) and the Java&trade; Content Repository: Apache Jackrabbit Oak 1.68.0.

The Quickstart uses Eclipse Jetty 11.0.x as servlet engine.

#### Java&trade; Support  {#java-support}

* Support for Java&trade; 17.
* For optimal performance, override default GC values with other values. For more information, see the [install and update](/help/sites-deploying/custom-standalone-install.md) section.
* Java&trade; 17 maintenance updates are distributed by Adobe for customer usage in AEM-related projects, when not publicly available from Oracle.

#### Uberjar Packaging {#uber-jar-packaging}

* There is slight difference in Uberjar packaging of AEM 6.5 LTS. For more information [refer](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version-update-the-aem-uber-jar-version).

#### Upgrade {#upgrade}

* For details about the upgrade procedure, see the [upgrade documentation](/help/sites-deploying/upgrade.md).

## Install and Update {#install-update}

For setup requirements, see [installation instructions](/help/sites-deploying/custom-standalone-install.md).

For detailed instructions, see [upgrade documentation](/help/sites-deploying/upgrade.md).

## Supported Platforms {#supported-platforms}

Find the complete matrix of supported platforms including support-level on [AEM 6.5 LTS technical requirements](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java&trade; 17 is the recommended version to use with AEM 6.5 LTS.

## Deprecated and Removed Features {#deprecated-and-removed-features}

Adobe constantly evaluates product capabilities, to over time reinvent or replace older features with more modern alternatives to improve overall customer value, always under careful consideration of backward compatibility.

To communicate the impending removal or replacement of Adobe Experience Manager (AEM) capabilities, the following rules apply:

1. Announcement of deprecation comes first. While deprecated, capabilities are still available but are not further enhanced.
1. Removal of deprecated capabilities occurs in the following major release at the earliest. Actual target date for removal will be announced later.

This process gives customers at least one release cycle to adapt their implementation to a new version or successor of a deprecated capability, before actual removal.

### Deprecated features {#deprecated-features}

This section lists features and capabilities that have been marked as deprecated with AEM 6.5 LTS. Generally, features that are planned for removal in a future release are set to deprecated first, with an alternative provided.

Customers are advised to review if they use the feature/capability in their current deployment, and make plans to change their implementation to use the alternative provided.

|Area|Feature|Replacement|Version (SP)|
|---|---|---|---|
| Sites | [SPA Editor](/help/sites-developing/spa-overview.md) | The preferred editors for managing headless content in AEM are:<br>- [The Universal Editor](/help/sites-developing/universal-editor/introduction.md) for visual editing.<br>- [The Content Fragment Editor](/help/assets/content-fragments/content-fragments-managing.md) for form-based editing. | 6.5 LTS GA |

### Removed Features {#removed-features}

This section lists features and capabilities that have been removed from AEM 6.5 LTS. Prior releases had these capabilities marked as deprecated.

|Area|Feature|Replacement|Version (SP)|
|--- |--- |--- |--- |
| Commerce| AEM CIF Classic is not supported. | You should migrate to [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions| Social/Communities is not supported. | No replacement available. | 6.5 LTS GA |
| Screens| Screens is not supported. | No replacement available. | 6.5 LTS GA |
| Assets| `dam-pim` and `dam-rating` are not supported as bundles are dependent on social. | No replacement available. | 6.5 LTS GA |
| Assets| `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` has been removed. | Use the alternate api `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` that has been added. | 6.5 LTS GA |
| Portal| AEM Portal Director is not supported. | No replacement available. | 6.5 LTS GA |
| Granite| Bundle `com.adobe.granite.socketio` is removed. | No replacement available. | 6.5 LTS GA |
| Granite| `com.adobe.granite.crx-explorer` is not supported. | No replacement available. | 6.5 LTS GA |
| Granite| `crx2oak` is not supported. | Pick relevant version of [oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe| `com.adobe.cq.cq-searchpromote-integration` is not supported. | No replacement available. | 6.5 LTS GA |
| Guava| All guava dependencies are now removed in AEM and hence the `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` bundle is not part of AEM. |Customers can add guava on their own if they are dependent on guava or replace guava code with java collections or other alternates if possible. | 6.5 LTS GA |
| We.Retail| We-retail sample site is not supported. | No replacement available. | 6.5 LTS GA |
|Open Source| `oak-solr-osgi` bundle is not supported.| No replacement available. | 6.5 LTS GA |
|Open Source| `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` and `org.apache.sling.atom.taglib` are not supported.| No replacement available. | 6.5 LTS GA |
|Open Source| `org.apache.commons.io` packages are now exported from `org.apache.commons.commons-io`.| No change required. | 6.5 LTS GA |
|Open Source| `javax.mail` packages are being exported from the `com.sun.javax.mail` bundle.| No change required. | 6.5 LTS GA |
|Open Source| `org.apache.jackrabbit.api` packages now are exported from the `org.apache.jackrabbit.oak-jackrabbit-api` bundle.| No change required. | 6.5 LTS GA |
|Open Source| `com.github.jknack.handlebars` is not supported| Pick relevant [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6.5 LTS GA |

## Restricted Websites{#restricted-sites}

These websites are only available to customers. If you are a customer and need access, contact your Adobe account manager.

* [Product download at licensing.adobe.com](https://licensing.adobe.com/)
* [Contact Adobe Customer Support](https://experienceleague.adobe.com/en/docs/customer-one/using/home).
