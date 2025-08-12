---
title: Current Release Notes for Adobe Experience Manager 6.5 LTS, SP1
description: Find current release information for Adobe Experience Manager 6.5 LTS, Service Pack 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
---
# Current Release Notes for Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Release Information {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 1 (SP1) |
| Type | Service Pack release |
| Date | August 21, 2025 |

## What is included in [!DNL Adobe Experience Manager] 6.5 LTS, SP1 {#what-is-new}

[!DNL Experience Manager] 6.5 LTS, SP1 includes new features, key customer-requested enhancements, and bug fixes. It also includes performance, stability, and security improvements released since the initial availability of 6.5 LTS in March 2025.
<!-- UPDATE EACH RELEASE -->

## Key features and enhancements

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Fixed issues in Service Pack 1 {#fixed-issues}



<!-- UPDATE EACH RELEASE -->

## Fixed issues in Service Pack 23 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE --> 

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Accessibility {#sites-accessibility-65-lts-sp1}

* Canvas sections in AEM Editor pages now support full keyboard accessibility. Users can activate section titles and edit buttons using only the keyboard, without relying on mouse hover. This update ensures compliance with WCAG 2.1.1 and improves usability across components (such as Teaser, Image, Carousel, Layout, Timewarp, and Annotation modals). (SITES-25256) <!-- 6.5 LTS SP1 -->
* Fixed an accessibility issue in the AEM Page Editor where keyboard focus unexpectedly resets to the start of the Demographic toolbar after activating buttons such as Persona, Cart, or Abandoned. Focus now remains on the activated button to support consistent keyboard navigation and screen reader workflows. (SITES-25306) 
* Fixed a critical accessibility issue in AEM Page Editor where canvas elements across multiple dialog boxes and modals (for example, Asset rail or Layout preview) could not be operated using only a keyboard. All interactive canvas elements now support keyboard-only navigation, ensuring compliance with WCAG 2.1 success criterion 2.1.1 (SITE-25256) 
* Fixed an accessibility issue in the Sites Admin UI where interactive list items in the Create pop-up used incorrect ARIA roles. Elements that behaved like links were assigned `role="listitem"` instead of `role="menuitem"`, violating ARIA design patterns and confusing screen readers. Updates ensure that all list components follow proper semantic roles for improved keyboard and assistive technology support. (SITES-24493) 
* Fixed accessibility label association issue for page title and tags fields. The AEM interface now correctly associates accessibility labels with the "Title" and "Page Title" fields when using screen readers like JAWS. The fix ensures proper label reading and improves ADA compliance across page creation, properties, and move workflows. (SITES-27149) 
* Fixed an accessibility issue with table identification in the permissions dialog box. The permissions table in AEM now uses correct ARIA roles and attributes to ensure screen readers like JAWS properly identify it as a table. The fix improves accessibility compliance and ensures that users receive accurate navigation and content announcements. (SITES-27140) 
* Fixed missing visual label for comment input fields in timeline. Corrected missing visual labels for "comment" input fields under the timeline section to improve accessibility. The update ensures that screen readers can accurately announce the field labels. This experience enhances form navigation and submission for all users, particularly those individuals that rely on assistive technologies. (SITES-26903) 
* Fixed keyboard accessibility for ellipsis button in timeline comments. Enabled keyboard navigation for the ellipsis (three dots) button next to comments under the timeline section. Users can now access and interact with the button using the tab key, improving accessibility for users who rely on keyboard-only navigation. (SITES-26891) 
* Improved NVDA/Narrator announcements for search results in selection dialog boxes. Updated the Open Selection dialog box to announce whether search results are found or not when using screen readers, such as NVDA or Narrator. This improvement helps users relying on assistive technologies understand the outcome of their search actions without needing visual confirmation. (SITES-26883) 
* Corrected ARIA role for ellipsis icon beside comment input field. Updated the ellipsis (three dots) icon beside the comment input field to use the correct ARIA role, ensuring screen readers can accurately identify the element. This improvement enhances accessibility compliance and improves the experience for users relying on assistive technologies. (SITES-26881) 
* Corrected invalid ARIA attributes in Coral UI components. Updated Coral UI components to ensure all ARIA attributes use valid values, improving accessibility-compliance. In particular, cases were addressed where invalid values like `aria-modal="dialog"` were incorrectly assigned. This enhancement enables screen readers to interpret dialog box elements correctly, improving accessibility for users relying on assistive technologies. (SITES-26873) 
* Improved visibility and tooltips for icons in Reflow scenarios. Enhanced the Reflow behavior to ensure tooltips display correctly for **Download**, **Reprocess assets**, and **Checkout** icons. Focused on an accessibility issue where icons and their labels became invisible when the viewport resized or browser zoom settings changed. This fix supports users with low vision by maintaining visibility and providing proper icon descriptions during Reflow. (SITES-26871) 

#### Admin User Interface{#sites-adminui-65-lts-sp1}

Fixed Universal Editor URL Service exception with missing Externalizer endpoints. The Universal Editor URL Service now handles missing author, publish, or local Externalizer endpoints without throwing exceptions. Admin users can open the Page Editor successfully even when some Externalizer configurations are incomplete. (SITES-28877)  <!-- LTS -->

#### Classic UI{#sites-classicui-65-lts-sp1} 


#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

* AEM now prevents performance degradation caused by malformed XMP metadata in image assets. Assets that contain invalid or non-compliant XMP property names, such as those with numeric segments or unqualified structures, no longer trigger repeated warning logs during processing. The system filters out problematic metadata to ensure that asset ingestion and validation is complete without errors. (SITES-30683) <!-- AEM 6.5 LTS SP1 -->


#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1}




#### [!DNL Content Fragments] - Fragments Editor{#sites-fragments-editor-65-lts-sp1}

Other authors can still publish Content Fragments even when another author checks them out, which is contrary to the intended behavior of the checkout feature. This fix prevents other users from seeing or using the publish buttons in the authoring interface when a Content Fragment is checked out. (SITES-30578)  <!-- LTS -->

#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

Fixed GraphQL QueryValidationError with Content Fragment schemas. Refreshing the `cq-dam-cfm-graphql` bundle corrects schema validation errors when using Content Fragment references. The fix ensures that GraphQL queries function properly without requiring manual schema re-alignment or re-publishing after package deployments. (SITES-27001)  <!-- LTS -->


#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}



#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1}



#### Component Console{#sites-component-console-65-lts-sp1}



#### Core Backend{#sites-core-backend-65-lts-sp1}

* Improperly formatted XMP metadata triggered an error during processing of image assets in the `ValidationDataServlet`. The fix ensures compliant metadata handling and avoids redundant parsing of invalid properties. (SITE-30683)  <!-- LTS -->


#### Core Components{#sites-core-components-65-lts-sp1}



#### Campaign integration{#sites-campaign-integration-65-lts-sp1}



#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}



#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}




#### Launches{#sites-launches-65-lts-sp1}




#### Link Checker{#sites-link-checker-65-lts-sp1}



#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp1}




#### Page Editor{#sites-pageeditor-65-lts-sp1}




#### Replication{#sites-replication-65-lts-sp1}




#### Rich Text Editor{#sites-rte-65-lts-sp1}



#### Universal editor {#sites-universal-editor-65-lts-sp1}



### [!DNL Assets]{#assets-65-lts-sp1}



#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp1}
 

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp1}



### [!DNL Forms]{#forms-65-lts-sp1}


#### Forms Designer 


#### Forms




#### Forms JEE 

 
 
#### Forms Captcha {#forms-captcha-65-lts-sp1} 




#### XMLFM {#forms-xmlfm-65-lts-sp1}




#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp1}




#### [!DNL Forms Designer] {#forms-designer-65-lts-sp1}




### Foundation {#foundation-65-lts-sp1}


#### Apache Felix {#foundation-apachefelix-65-lts-sp1}



#### Campaign{#foundation-campaign-65-lts-sp1}


#### Cloud Services{#foundation-cloudservices-65-lts-sp1}


#### Communities {#foundation-communities-65-lts-sp1}


#### Content distribution{#foundation-content-distribution-65-lts-sp1}



#### CRX {#foundation-crx-65-lts-sp1}



#### Granite{#foundation-granite-65-lts-sp1}




#### Integrations{#foundation-integrations-65-lts-sp1}




#### Jetty{#foundation-jetty-65-lts-sp1}

Resolved an issue where SNI validation blocked API calls over HTTPS for AEM customers using Dispatcher SSL configurations with custom host headers. Introduces an option to disable SNI validation as part of Jetty configuration, enabling compatibility with specific reverse proxy setups where `mod_proxy` is not feasible. (NPR-42614) 



#### Localization{#foundation-localization-65-lts-sp1}



#### Oak {#foundation-oak-65-lts-sp1}



#### Platform{#foundation-platform-65-lts-sp1}




#### Security{#foundation-security-65-lts-sp1}


#### Sling{#foundation-sling-65-lts-sp1}



#### Translation{#foundation-translation-65-lts-sp1}



#### User interface{#foundation-ui-65-lts-sp1}



#### WCM{#foundation-wcm-65-lts-sp1}

 

#### Workflow{#foundation-workflow-65-lts-sp1}














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

## Install and update {#install-update}

For setup requirements, see [installation instructions](/help/sites-deploying/custom-standalone-install.md).

For detailed instructions, see the [upgrade documentation](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> For fresh AEM 6.5 LTS installations, index definitions must be installed separately. For more information, refer [this](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Supported platforms {#supported-platforms}

Find the complete matrix of supported platforms including support-level on [AEM 6.5 LTS technical requirements](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java&trade; 17/Java&trade; 21 are the recommended versions to use with AEM 6.5 LTS.

## Deprecated and removed features {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe continually reviews product capabilities to improve customer value by modernizing or replacing older features. These changes are made with careful attention to backward compatibility.

To communicate the impending removal or replacement of Adobe Experience Manager (AEM) capabilities, the following rules apply:

1. Announcement of deprecation comes first. While deprecated, capabilities are still available but are not further enhanced.
1. Removal of deprecated capabilities occurs in the following major release at the earliest. The actual target date for removal is planned for announcement later.

This process gives customers at least one release cycle to adapt their implementation to a new version or successor of a deprecated capability, before actual removal.


### Deprecated features {#deprecated-features}

This section lists features and capabilities that Adobe has deprecated in AEM 6.5 LTS. Typically, Adobe deprecates features before removing them in a future release and provides an alternative.


Customers are advised to review if they use the feature/capability in their current deployment, and make plans to change their implementation to use the alternative provided.

|Area|Feature|Replacement|Version (SP)|
|---|---|---|---|


### Removed features {#removed-features}

This section lists features and capabilities that have been removed from AEM 6.5 LTS. Prior releases had these capabilities marked as deprecated.

|Area|Feature|Replacement|Version (SP)|
|--- |--- |--- |--- |



## Known issues {#known-issues} 

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

### Issue with JSP scripting bundle in AEM 6.5.21-6.5.23 and AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23, and AEM 6.5 LTS GA ship with the `org.apache.sling.scripting.jsp:2.6.0` bundle, which contains a known issue. The issue typically occurs under high load when the AEM instance handles many concurrent requests.

When this issue occurs, one of the following exceptions may appear in the error logs alongside references to `org.apache.sling.scripting.jsp:2.6.0`:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

A hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) is available to resolve this problem.

### Dispatcher connection failure with SSL-only feature {#ssl-only-feature}

When enabling the SSL-only feature in AEM deployments, there is a known issue that affects connectivity between the Dispatcher and AEM instances. After enabling this feature, health checks may fail and communication between Dispatcher and AEM instances can be disrupted. This issue specifically occurs when customers attempt to connect via `https + IP` from the Dispatcher to AEM instances and is related to SNI (Server Name Indication) validation problems.

**Impact:**

* Health check failures with HTTP 400 response codes
* Broken traffic between Dispatcher and AEM instances
* Content cannot be properly served through the Dispatcher
* Connection failures when using HTTPS with IP addresses in Dispatcher configuration
* HTTP 400 "Invalid SNI" errors when connecting via HTTPS + IP

**Affected environments:**

* AEM deployments with Dispatcher configurations
* Systems where the SSL-only feature has been enabled
* Dispatcher configurations using `https + IP` connection method to AEM instances

**Solution:**
If you experience this issue, please contact Adobe Customer Support. A hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) is available to resolve this problem. Do not attempt to enable SSL-only features until applying the necessary hotfix.

## Restricted websites{#restricted-sites}

These websites are only available to customers. If you are a customer and need access, contact your Adobe account manager.

* [Product download at licensing.adobe.com](https://licensing.adobe.com/)
* [Contact Adobe Customer Support](https://experienceleague.adobe.com/en/docs/customer-one/using/home).
 
