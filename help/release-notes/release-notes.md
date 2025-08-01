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

<!-- UPDATE EACH RELEASE -->

## Fixed issues in Service Pack 1 {#fixed-issues}

<!-- UPDATE EACH RELEASE -->




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
 
