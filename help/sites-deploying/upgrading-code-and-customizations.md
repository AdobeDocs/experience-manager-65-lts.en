---
title: Upgrading Code and Customizations
description: Learn more about upgrading code and customizations in AEM.
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 6b94caf1-97b7-4430-92f1-4f4d0415aef3
---
# Upgrading Code and Customizations{#upgrading-code-and-customizations}

When planning an upgrade, the following areas of an implementation must be investigated and addressed.

* [Upgrade the Code Base](#upgrade-code-base)
* [Testing Procedure](#testing-procedure)

## Overview {#overview}

1. **AEM Analyzer** - Run the AEM Analyzer as described in upgrade planning, and described in detail on the [Assessing the Upgrade Complexity with AEM Analyzer](/help/sites-deploying/aem-analyzer.md) page. You get a AEM Analyzer report that contains more details on areas that must be addressed in addition to the unavailable APIs/bundles in the Target version of AEM. The AEM Analyzer report gives you an indication of any incompatibilities in your code. If none exists, then your deployment is already 6.5 LTS compatible. You can still choose to do new development for using 6.5 LTS functionality, but you do not need it just for maintaining compatibility. 
1. **Develop Code Base for 6.5 LTS**- Create a dedicated branch or repository for the code base for the Target version. Use info from Pre-Upgrade Compatibility to plan areas of code to update.
1. **Compile with 6.5 LTS Uber jar**- Update code base POMs to point to 6.5 LTS uber jar and compile code against it.
1. **Deploy to 6.5 LTS Environment** - A clean instance of AEM 6.5 LTS (Author + Publish) should be stood up in a Dev/QA environment. Updated code base and a representative sample of content (from current production) should be deployed.
1. **QA Validation and Bug fix** - QA should validate the application on both Author and Publish instances of 6.5 LTS . Any bugs found should be fixed and committed to the 6.5 LTS code base. Repeat Dev-Cycle as necessary until all bugs are fixed. 

Before proceeding with an upgrade, you should have a stable application code base that has been thoroughly tested against AEM 6.5 LTS. 

## Upgrade the Code Base {#upgrade-code-base}

### Create a Dedicated Branch for 6.5 LTS Code in Version Control {#create-a-dedicated-branch-for-6.5-lts-code-in-version-control}

All code and configurations required for your AEM implementation should be managed using some form of version control. A dedicated branch in version control should be created for managing any changes needed for the code base in the target version of AEM. Iterative testing of the code base against the target version of AEM and subsequent bug fixes is managed in this branch.

### Update the AEM Uber Jar version {#update-the-aem-uber-jar-version}

The AEM Uber jar includes all AEM APIs as a single dependency in your Maven project's `pom.xml`. It is always a best practice to include the Uber Jar as a single dependency instead of including individual AEM API dependencies. When upgrading the code base, change the version of the Uber Jar to point to the 6.5 LTS version of AEM. Update any deprecated APIs or methods so they are compatible with the target version of AEM. Recompile the code base against the new version of the Uber Jar.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>There is a slight difference in how AEM 6.5 and AEM 6.5 LTS Uber Jars are packaged. Refer to the section below: 

**Uber Jars for AEM 6.5**

1. `uber-jar-6.5.x.jar` – Contains all public APIs of AEM 6.5.
1. `uber-jar-6.5.x-apis-with-deprecations.jar` – Includes both public APIs and deprecated APIs from AEM 6.5.

**Uber Jars for AEM 6.5 LTS**

For AEM 6.5 LTS, there are again two types of Uber Jars: 

1. `uber-jar-6.6.x-apis.jar` – Contains all public APIs of AEM 6.5 LTS.
1. `uber-jar-6.6.x-deprecated-apis.jar` – Only includes deprecated APIs from AEM 6.5 LTS.

**Key Difference: AEM 6.5 vs. AEM 6.5 LTS Uber Jars**

* In AEM 6.5, if both public and deprecated APIs are needed, you can use include single jar, `uber-jar-6.5.x-apis-with-deprecations.jar` in your `pom.xml` file.
* In AEM 6.5 LTS, if you need both public and deprecated APIs, you must include two separate jars, `uber-jar-6.6.x-apis.jar` for public APIs and `uber-jar-6.6.x-deprecated-apis.jar` for deprecated APIs.

**Maven coordinates for deprecated APIs Jar**

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Developer Notes {#developer-notes}

* AEM 6.5 LTS does not include Google guava library out-of-the-box, the required version can be installed as per requirement.
* Sling XSS bundle now uses Java HTML Sanitizer library, and usage of the `XSSAPI#filterHTML()` method should be used for rendering HTML content safely and not for passing data to other APIs.

## Testing Procedure {#testing-procedure}

A comprehensive test plan should be prepared for testing upgrades. Testing the upgraded code base and application must be done in lower environments first. Any bugs found should be fixed in an iterative fashion until the code base is stable, only then should higher-level environments be upgraded.

### Testing the Upgrade Procedure {#testing-upgrade-procedure}

The upgrade procedure as outlined here should be tested on Dev and QA environments as documented in your customized run book (see [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md)). The upgrade procedure should be repeated until all steps are documented in the upgrade run book and the upgrade process is smooth.

### Implementation Test Areas  {#implementation-test-areas-}

Below are critical areas of any AEM implementation that should be covered by your test plan once the environment has been upgraded and the upgraded code base has been deployed.

<table>
 <tbody>
  <tr>
   <td><strong>Functional Test Area</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Published Sites</td>
   <td>Testing the AEM implementation and associated code on the publish tier<br /> through the Dispatcher. Should include criteria for page updates and<br /> cache invalidation.</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Testing the AEM implementation and associated code on the Author tier. Should include page, component authoring, and dialogs.</td>
  </tr>
  <tr>
   <td>Integrations with Experience Cloud Solutions</td>
   <td>Validating integrations with products like Analytics.</td>
  </tr>
  <tr>
   <td>Integrations with third-party systems</td>
   <td>Validate any third-party integrations on both Author and Publish tiers.</td>
  </tr>
  <tr>
   <td>Authentication, Security, and Permissions</td>
   <td>Any authentication mechanisms like LDAP/SAML should be validated.<br /> Permissions and groups should be tested on both Author and Publish<br /> tiers.</td>
  </tr>
  <tr>
   <td>Queries</td>
   <td>Custom indexes and queries should be tested along with query performance.</td>
  </tr>
  <tr>
   <td>UI Customizations</td>
   <td>Any extensions or customizations to the AEM UI in the author environment.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>Custom and/or out of the box workflows and functionality.</td>
  </tr>
  <tr>
   <td>Performance Testing</td>
   <td>Load testing should be performed on both Author and Publish tiers that simulate real-world scenarios.</td>
  </tr>
 </tbody>
</table>

### Document Test Plan and Results {#document-test-plan-and-results}

A test plan should be created that covers the above implementation test areas. Often it makes sense to separate the test plan by Author and Publish task lists. This test plan should be executed on Dev, QA, and Stage environments before upgrading Production environments. Test results and performance metrics should be captured on lower environments to provide comparison when upgrading Stage and Production environments.
