---
title: Current Release Notes for Adobe Experience Manager 6.5 LTS, SP2
description: Find current release information for Adobe Experience Manager 6.5 LTS, Service Pack 2.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
---
# Current release notes for Adobe Experience Manager 6.5 LTS, SP2 {#release-notes}

## Release information {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 2 (SP2), Hotfix for GRANITE-61551 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack release |
| Date | September 9, 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.1-hotfix-GRANITE-61551-1.4.zip) |

<!-- OLD URL TO JAR
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.1.jar) | -->


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## What is included in [!DNL Adobe Experience Manager] 6.5 LTS, SP2 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP2 includes new features, key customer-requested enhancements, and bug fixes. It also includes performance, stability, and security improvements released since the initial availability of 6.5 LTS in March 2025. [Install this Service Pack](#install-update) on 6.5 LTS.

## Key features and enhancements 



<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE THE EACH RELEASE -->

## Fixed issues in 6.5 LTS, Service Pack 2 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE --> 

### [!DNL Sites]{#sites-65-LTS-SP2}

#### Accessibility {#sites-accessibility-65-lts-sp2}

* The Text component lost keyboard focus when authors hovered items in the Component Browser during editing. This disrupted typing and triggered an accessibility failure under WCAG 3.2.1. The fix prevents hover styling from shifting focus and keeps the Text component focused during Component Browser interaction. (SITES-35370)
* Corrected focus management in the Description rich text field that blocked forward navigation with the Tab key. Users became stuck in the RTE because the component relied on a non-standard keyboard command to shift focus, which broke expected dialog box navigation. The change enforces standard keyboard interaction and preserves logical Tab sequencing throughout the dialog box. (SITES-35228)
* Addressed an issue in the Sites editor that disrupted expected behavior during page authoring and led to inconsistent component interaction. Authors experienced unreliable UI responses that interfered with standard editing tasks and reduced workflow efficiency. The update refines the underlying editor logic and restores stable, predictable interaction across affected components. (SITES-35227)
* Resolved a regression that broke the asset selector in the page editor and prevented it from loading in specific page editing scenarios. Authors can now open and use the asset selector normally when choosing or browsing assets while editing a page. This restores consistent access to asset selection workflows that were disrupted by the loading failure. (SITES-35226)
* Eliminated an issue in the Sites editor that caused inconsistent behavior during page interaction and disrupted standard authoring workflows. The defect led to unexpected UI responses that interfered with component configuration and content updates. The update stabilizes the affected functionality and restores reliable execution of editing actions across pages. (SITES-35225)
* Eliminated a defect in the Sites authoring interface that caused inconsistent behavior during page editing and disrupted normal workflows. Authors encountered unexpected UI responses that interfered with component interaction and content updates. The update stabilizes the affected functionality and restores reliable, predictable behavior across editing scenarios. (SITES-35224)


#### Admin user interface{#sites-adminui-65-lts-sp2}

* Sites console List View Settings did not reflect the columns shown in List View. The dialog box opened with cleared checkboxes and an incorrect selected-columns count. The fix syncs dialog box state with the active grid columns and updates the counter to match actual column visibility. (SITES-38576)

#### Classic user interface{#sites-classicui-65-lts-sp2} 

* Classic UI Text component editing displayed raw HTML tags instead of rich text after an upgrade. Service Pack 2 corrects Classic UI RTE (Rich Text Editor) rendering so the editor displays formatted content and preserves stored markup. The fix also stops markup expansion during repeated edits and saves. (SITES-38709)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp2}

* Headless eventing support lacked required OSGi events for Content Fragments and Models in 6.5 LTS. The update adds the eventing bundle plus required dependencies and includes a 6.5 LTS build. Content Fragment and Model events now fire correctly and support Launches API workflows. (SITES-35329)

#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp2}

* Adjusted component handling in the Sites authoring interface to stop irregular behavior during page updates. The defect led to unpredictable editor responses that interfered with routine content modifications and reduced workflow efficiency. The update aligns editor logic with expected interaction patterns and delivers dependable performance during authoring activities. (SITES-35078) CRITICAL

* A regression broke Assets console list view for Content Fragments and triggered an error during list rendering. The update corrects list-view logic after preview-info removal and restores stable list output. The console now displays Content Fragments without failures and keeps list interactions usable. (SITES-38683)


#### [!DNL Content Fragments] - Fragments Editor{#sites-fragments-editor-65-lts-sp2}

* Content Fragment variation tags disappeared when the feature toggle remained disabled after refactoring. The fix restores variation tag support even when that toggle stays off. Authors can again add and view variation tags in the Content Fragment editor. (SITES-38682) CRITICAL
* Edited Content Fragments disappeared from the Assets console list after authors navigated back from the Content Fragment editor. Browser caching returned a stale list and hid the updated fragment until a manual refresh. The fix adds cache-control handling for the editor return path so the list reloads correctly and keeps the edited fragment visible. (SITES-35374) CRITICAL

* The Content Fragment RTE showed layout and visual issues after recent UI styling changes. Service Pack 2 refines RTE styling so the toolbar and editable area render correctly and remain readable. The Content Fragment editor now aligns with the Page Editor look and behavior. (SITES-38684)
* Removing IMS scopes from the Polaris Asset Selector broke Content Fragment integration with the delivery endpoint. Authors hit failures when opening the remote Asset Selector and selecting assets. The update re-adds the needed IMS scopes and restores stable delivery-tier access. (SITES-35837)


#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp2}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp2}

#### [!DNL Content Fragments] - Model Editor{#sites-model-editor-65-lts-sp2}

* Nested Content Fragment models stopped working when refactoring tied the feature to a disabled toggle. The fix restores nested model support without requiring toggle changes. Authors can again create and use nested models in the Model Editor. (SITES-38681) CRITICAL

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp2}

* AEM Headless required a dedicated release branch to avoid dependency and bundle version conflicts with mainline builds. The update adds a release/6.5lts headless branch and aligns dependency sets and bundle versions. Jenkins now builds the headless codebase cleanly without version collisions. (SITES-36585)

#### Component console{#sites-component-console-65-lts-sp2}

#### Content API{#sites-content-api-65-lts-sp2}

* A feature-toggle defect misreported Page Management API status. The update adds a dedicated enablement flag and evaluates it alongside the existing toggle. Page Management API now shows stable status. Site Management API remains experimental. (SITES-39284)

#### Core backend{#sites-core-backend-65-lts-sp2}

* Introduced a change in the Sites authoring experience to resolve inconsistent behavior that disrupted standard page editing workflows. Authors encountered unexpected results during component interaction, which interfered with content updates and reduced reliability. The change restores stable editor behavior and ensures consistent execution of authoring actions across affected scenarios. (SITES-35162) CRITICAL

* Refined Sites authoring behavior to resolve an issue that disrupted page editing and caused inconsistent results during component interaction. Authors experienced unexpected UI responses that interfered with content updates and reduced workflow reliability. The change restores stable editor state management and ensures predictable execution of authoring actions across affected scenarios. (SITES-34499)

#### Core Components{#sites-core-components-65-lts-sp2}

#### Campaign integration{#sites-campaign-integration-65-lts-sp2}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp2}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp2}

#### Launches{#sites-launches-65-lts-sp2}

* Sites Timeline showed hardcoded English text during Launch promotion: "Created version ... before promoting launch." The update replaces the hardcoded string with localized message handling. Timeline now displays localized text and aligns the entry with standard AEM localization behavior. (SITES-39157)
* Launch promotion scope drifted when authors promoted a subsection using Promote current page and sub pages. AEM also promoted unrelated pages and caused unexpected live-site modifications. The fix corrects Launch scope calculation so only the chosen subtree promotes. (SITES-38315)
* Content Fragments inside Launches did not participate in the `damAssetLucene` index and limited search results and query efficiency. This change adds Launch Content Fragment paths to the index definition. Search and custom queries now find Content Fragments under `/content/launches`. (SITES-35634)
* Launches UI showed Content Fragment Launch controls even though the product does not expose Content Fragment Launches in Touch UI. This change strips Content Fragment Launch code paths from cq-launches-content and adjusts Launch list filtering. Authors now see consistent page Launch options without Content Fragment Launch entries. (SITES-35633)
* AEM 6.5 LTS Quickstart lacked required Launches bundles and prerequisites, which blocked Launches OpenAPI enablement. The update adds Launches bundles and required dependencies such as metrics support, dam-cfm updates, and queue configuration. Launches APIs now run on 6.5 LTS Quickstart with the required runtime components present. (SITES-35297)
* CF Launches packaging pulled newer dependency versions and unnecessary GraphQL libraries, which complicated AEM 6.5 LTS integration. This change aligns dependency versions with the AEM 6.5 LTS baseline and strips unused GraphQL dependencies. Bundle resolution now stays consistent and CF Launches startup remains stable. (SITES-35295)
* AEM Launches now runs a dedicated Jenkins pipeline for the 6.5 LTS branch. The pipeline runs nightly builds and sends failure alerts by email. This setup increases test coverage and catches regressions early. (SITES-35293)
* AEM 6.5 LTS now ships an updated Launches API bundle with aligned artifact versions. The bundle tracks the primary code line while keeping the correct 6.5 LTS release version. This update stabilizes Launches API consumption across the 6.5 LTS stack. (SITES-35292)
* AEM 6.5 LTS now includes an updated launches-core bundle with aligned dependency versions. The update adds launches-core handling for Fragment UUID and Reference UUID data types. Launch processing now keeps consistent behavior across Launches and Content Fragment workflows. (SITES-35290)
* Refined the Sites editor to resolve inconsistent behavior that disrupted normal page authoring workflows. Authors encountered unexpected component interaction that interfered with content updates and reduced editing reliability. The change restores consistent UI state management and ensures predictable execution of authoring actions across affected scenarios. (SITES-35138)

#### Link Checker{#sites-link-checker-65-lts-sp2}

#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp2}

* Administrators had limited visibility into MSM push-on-modify processing during content changes. The fix adds detailed logging around MSM event reception and rollout execution. Debug output now shows which events fired, which content paths changed, and who triggered the change. (SITES-38029)

#### Page editor{#sites-pageeditor-65-lts-sp2}

#### Replication{#sites-replication-65-lts-sp2}

#### Rich Text Editor{#sites-rte-65-lts-sp2}

#### Template Editor{#sites-template-editor-65-lts-sp2}

* Template status text displayed vertically in **Tools** > **General** > **Templates** for some locales. The "outdated" label broke layout and read as a column of characters. The fix corrects template status styling so the label renders on a single horizontal line. (SITES-36797)

#### Universal editor {#sites-universal-editor-65-lts-sp2}

* An OSGi default configuration set `preview=true` and forced Universal Editor to start in Preview mode. This update corrects the default value and restores the standard Production entry behavior. Universal Editor now opens in Production mode unless an admin explicitly enables Preview mode. (SITES-37193)




### [!DNL Assets]{#assets-65-lts-sp2}

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp2}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp2}




### [!DNL Forms]{#forms-65-lts-sp2}

#### Forms Designer

#### Forms

#### Forms JEE 

#### Forms Captcha {#forms-captcha-65-lts-sp2}

#### XMLFM {#forms-xmlfm-65-lts-sp2}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp2}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp2}

#### Forms Designer

#### AdaptIve Forms

#### Forms Captcha

#### Forms Management UI





### Foundation {#foundation-65-lts-sp2}

#### Apache Felix {#foundation-apachefelix-65-lts-sp2}

#### Campaign{#foundation-campaign-65-lts-sp2}

#### Cloud Services{#foundation-cloudservices-65-lts-sp2}

#### Communities {#foundation-communities-65-lts-sp2}

#### Content distribution{#foundation-content-distribution-65-lts-sp2}

#### CRX {#foundation-crx-65-lts-sp2}

#### Granite{#foundation-granite-65-lts-sp2}

#### HTL{#foundatoin-htl-5-lts-sp2}

#### Integrations{#foundation-integrations-65-lts-sp2}

#### Jetty{#foundation-jetty-65-lts-sp2}

#### Localization{#foundation-localization-65-lts-sp2}

#### Oak {#foundation-oak-65-lts-sp2}

#### Omnisearch{#foundation-omnisearch-65-lts-sp2}

#### Platform{#foundation-platform-65-lts-sp2}

#### Projects{#foundation-projects-65-lts-sp2}

#### Quickstart{#foundation-quickstart-65-lts-sp2} 

#### Security{#foundation-security-65-lts-sp2}

#### Sling{#foundation-sling-65-lts-sp2}

#### Translation{#foundation-translation-65-lts-sp2}

#### User interface{#foundation-ui-65-lts-sp2}

#### WCM{#foundation-wcm-65-lts-sp2}

#### Workflow{#foundation-workflow-65-lts-sp2}





## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

The platform of [!DNL Adobe Experience Manager] 6.5 LTS builds on top of updated versions of the OSGi-based framework (Apache Sling and Apache Felix) and the Java&trade; Content Repository: Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x is used as a servlet engine for the Quickstart.

### Java&trade; support  {#java-support}

* Support for Java&trade; 17 and Java&trade; 21.
* For optimal performance, override the default GC values with other values. For more information, see the [install and update](/help/sites-deploying/custom-standalone-install.md) section.
* Adobe distributes Java&trade; 17  and Java&trade; 21 maintenance updates for customer usage in AEM-related projects, when not publicly available from Oracle.

### Uberjar packaging {#uber-jar-packaging}

* There is a slight difference in Uberjar packaging of AEM 6.5 LTS. For more information, see [Update the AEM Uber Jar version](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Upgrade {#upgrade}

* For details about the upgrade procedure, see the [upgrade documentation](/help/sites-deploying/upgrade.md).
* For detailed upgrade instructions, see the [Upgrade Guide for AEM Forms 6.5 LTS SP1 on JEE](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

#### Best practices for AEM 6.5 LTS Service Pack upgrades

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

**Environment**
Applies to: AEM 6.5 LTS (On-Premise) customers installing Service Pack 1 (SP1). SP1 is delivered as a Quickstart JAR.

**Why this matters**
SP1 for AEM 6.5 LTS ships as a Quickstart JAR rather than a ZIP to install through Package Manager. On-prem customers upgrade by replacing the Quickstart JAR, unpacking it, and restarting. This method is consistent with Adobe's in-place upgrade procedure.

**Recommended upgrade flow (Author or Publish)**

1. Verify that your AEM 6.5 LTS instance is healthy and accessible.
1. Download the SP1 Quickstart JAR (for example, `cq-quickstart-6.6.x.jar`) from Software Distribution. 
1. Stop the running instance. 
1. In the AEM install directory (outside `crx-quickstart/`), replace the previous Quickstart JAR with the SP1 JAR.
1. Unpack the JAR:

    ```java
    java -jar cq-quickstart-6.6.x.jar -unpack
    ```

    (Adjust heap flags as needed.)

1. Rename the unpacked JAR to match the role and port, for example `cq-author-4502.jar` or `cq-publish-4503.jar`.
1. Start AEM and confirm the upgrade in the UI (Help > About) and logs.

**Good hygiene**

* Run the upgrade in lower/test environments before production.
* Take a full, restorable backup (repository plus any external datastores) before you begin.
* Review Adobe's in-place upgrade guidance and technical requirements (Java 17/21 recommended for LTS).

>[!NOTE]
>
>File names shown above (for example, `cq-quickstart-6.6.x.jar`) reflect the SP1 Quickstart artifact naming observed for this LTS release; always use the exact file name you download from Software Distribution. 

## Install and update{#install-update}

For setup requirements, see [installation instructions](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> If you are directly upgrading to LTS SP1 from old 6.5 SPs, please follow the instructions given for 6.5 to 6.5 LTS GA [upgrade](/help/sites-deploying/upgrade.md).


For detailed instructions, see the [upgrade documentation](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> For fresh AEM 6.5 LTS installations, index definitions must be installed separately. For more information, see [this article](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Install and update AEM Forms add-on {#install-update-aem-forms-add-on}

For detailed instructions, see [Performing an In-Place Upgrade](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).



## Supported platforms {#supported-platforms}

Find the complete matrix of supported platforms including support-level on [AEM 6.5 LTS technical requirements](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java&trade; 17/Java&trade; 21 are the recommended versions to use with AEM 6.5 LTS.


## Deprecated and removed features {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe continually reviews and evolves product capabilities to deliver greater customer value by modernizing or replacing legacy features. These changes are implemented with careful consideration for backward compatibility.

To ensure transparency and allow adequate planning, Adobe follows this deprecation process for Adobe Experience Manager (AEM):

* Deprecation is announced first. Deprecated capabilities remain available but are no longer enhanced.

* Removal occurs no earlier than the next major release. The planned removal timeline is communicated separately.

* A minimum of one release cycle is provided for customers to transition to supported alternatives before a capability is removed.

### Deprecated features {#deprecated-features}

This section lists features and capabilities that Adobe has deprecated in AEM 6.5 LTS. Typically, Adobe deprecates features before removing them in a future release and provides an alternative.

Customers are advised to review if they use the feature/capability in their current deployment, and make plans to change their implementation to use the alternative provided.

| Area | Feature | Replacement | Version (SP) |
| --- | --- | --- | --- |
| Sites | [SPA Editor](/help/sites-developing/spa-overview.md) | The preferred editors for managing headless content in AEM are:<br>- [The Universal Editor](/help/sites-developing/universal-editor/introduction.md) for visual editing.<br>- [The Content Fragment Editor](/help/assets/content-fragments/content-fragments-managing.md) for form-based editing. | 6.5 LTS GA |
| [!DNL Foundation]       | Support for com.adobe.granite.oauth.server | Adobe IMS Integration ||

### Removed features {#removed-features}

This section lists features and capabilities that have been removed from AEM 6.5 LTS. Prior releases had these capabilities marked as deprecated.

* Support for RDBMK for CRX repository persistence has been removed.

* In clustered environments, MongoMK is now the only supported option for repository persistence.

| Area | Feature | Replacement | Version (SP) |
| --- | --- | --- | --- |
| Commerce| AEM CIF Classic is not supported. | Migrate to [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions| Social/Communities is not supported. | No replacement available. | 6.5 LTS GA |
| Screens| Screens are not supported. | No replacement available. | 6.5 LTS GA |
| Assets| `dam-pim` and `dam-rating` are not supported as bundles are dependent on social. | No replacement available. | 6.5 LTS GA |
| Assets| `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` has been removed. | Use the alternate api `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` that has been added. | 6.5 LTS GA |
| Portal| AEM Portal Director is not supported. | No replacement available. | 6.5 LTS GA |
| Granite| Bundle `com.adobe.granite.socketio` is removed. | No replacement available. | 6.5 LTS GA |
| Granite| `com.adobe.granite.crx-explorer` is not supported. | No replacement available. | 6.5 LTS GA |
| Granite| `crx2oak` is not supported. | Pick the relevant version of [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe| `com.adobe.cq.cq-searchpromote-integration` is not supported. | No replacement available. | 6.5 LTS GA |
| Guava| All guava dependencies are now removed in AEM and hence the `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` bundle is not part of AEM. |Customers can add guava on their own if they are dependent on guava or replace guava code with java collections or other alternates if possible. | 6.5 LTS GA |
| `We.Retail`| `We-retail` sample site is not supported. | No replacement available. | 6.5 LTS GA |
|Open Source| `oak-solr-osgi` bundle is not supported.| No replacement available. | 6.5 LTS GA |
|Open Source| `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` and `org.apache.sling.atom.taglib` are not supported.| No replacement available. | 6.5 LTS GA |
|Open Source| `org.apache.commons.io` packages are now exported from `org.apache.commons.commons-io`.| No change required. | 6.5 LTS GA |
|Open Source| `javax.mail` packages are being exported from the `com.sun.javax.mail` bundle.| No change required. | 6.5 LTS GA |
|Open Source| `org.apache.jackrabbit.api` packages now are exported from the `org.apache.jackrabbit.oak-jackrabbit-api` bundle.| No change required. | 6.5 LTS GA |
|Open Source| `com.github.jknack.handlebars` is not supported| Pick the relevant [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6.5 LTS GA |


## Known issues {#known-issues} 

### Dispatcher connection failure with SSL-only feature (Fixed in AEM 6.5 LTS SP1 and later){#ssl-only-feature}

>[!NOTE]
>
> This issue is only present in the AEM 6.5 LTS GA release.

When enabling the SSL-only feature in AEM deployments, there is a known issue that affects connectivity between the Dispatcher and AEM instances. After enabling this feature, health checks may fail and communication between Dispatcher and AEM instances can be disrupted. This issue specifically occurs when customers attempt to connect through `https + IP` from the Dispatcher to AEM instances. It is related to SNI (Server Name Indication) validation problems.

**Impact**

* Health check failures with HTTP 400 response codes
* Broken traffic between Dispatcher and AEM instances
* Content cannot be properly served through the Dispatcher
* Connection failures when using HTTPS with IP addresses in Dispatcher configuration
* HTTP 400 "Invalid SNI" errors when connecting via HTTPS + IP

**Affected environments**

* AEM deployments with Dispatcher configurations
* Systems where the SSL-only feature has been enabled
* Dispatcher configurations using `https + IP` connection method to AEM instances

**Solution**

If you experience this issue, please contact Adobe Customer Support. A hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) is available to resolve this problem. Do not attempt to enable SSL-only features until applying the necessary hotfix.

## OSGi bundles and content packages included{#osgi-bundles-and-content-packages-included}

The following text documents list the OSGi bundles and Content Packages included in this [!DNL Experience Manager] 6.5 LTS, Service Pack 1 release:

* [List of OSGi bundles included in Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [List of Content Packages included in Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Restricted websites{#restricted-sites}

These websites are only available to customers. If you are a customer and need access, contact your Adobe account manager.

* [Product download at licensing.adobe.com](https://licensing.adobe.com/)
* [Contact Adobe Customer Support](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).
 
