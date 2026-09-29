---
title: Technical Frequently Asked Questions (FAQ)
description: Frequently asked technical questions about AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: ed762d86-a04b-452b-a08f-86359bb8ff27
    internal-label: Configuration and operations
subfeature_v2:
  - id: c21ccc2b-e0c8-4853-bf41-f12259ed93f8
    internal-label: Release information
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# AEM 6.5 LTS Technical FAQ {#technical-faq}

This page is meant to answer some frequently asked technical questions about AEM 6.5 LTS.

## Technical FAQs

### The `/systemalive` endpoint is no longer available in AEM 6.5 LTS.

The Felix System Ready bundle which was configured to provide the `/systemalive` endpoint has been deprecated and superseded by Apache Felix Health Checks. This bundle is no longer included in AEM 6.5 LTS.

The new health check endpoint is available at `/system/health` and is implemented using Apache Felix Health Checks.

For detailed documentation on the Felix Health Check framework, refer to the [felix documentation](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### AEM Groovy Console support

The AEM Groovy Console version that was being used in AEM 6.5 might not work in AEM 6.5 LTS due to missing guava dependencies. The newly supported version of the AEM Groovy Console is [19.0.8](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

#### Additional configuration required for AEM Groovy Console

If you are using the AEM Groovy Console, you must explicitly add the following OSGi configuration for `com.adobe.granite.apicontroller.FilterResolverHookFactory`. Add `aem-groovy-console-bundle` to the allowed bundle list for the `org.apache.sling.distribution.api` key, extending the platform defaults:

```
"org.apache.sling.distribution.api": "com.adobe.*,com.day.*,org.apache.sling.*,aem-groovy-console-bundle"
```

### Does AEM 6.5 LTS support user-sync?

Yes, AEM 6.5 LTS supports user-sync. There is no change in the functionality of user-sync between AEM 6.5 and 6.5 LTS.

### The Uber JAR on Maven Central appears to be corrupted — what’s the issue?

Verify that you are using the Uber JAR with the `apis` classifier. Note that the packaging structure of the Uber JAR has changed in AEM 6.5 LTS. For more information, see [Update the AEM Uber Jar version](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Does AEM 6.5 LTS support the `jakarta.*` package namespaces (for example, `jakarta.annotation`)?

No. AEM 6.5 LTS does not support Sling artifacts migrated to the `jakarta.*` package namespaces. Use the `javax.*` equivalents in your code and dependencies — for example, `javax.annotation.PostConstruct` rather than `jakarta.annotation.PostConstruct` in Sling Models. The Sling Models implementation in AEM 6.5 LTS recognizes only the `javax.*` annotations, so `jakarta.*` annotations are silently ignored during initialization.

For more information, see the knowledge base article [Sling Models with `jakarta.annotation.PostConstruct` fail on AEM 6.5 LTS](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-30339).

## Getting Additional Help

If you encounter issues not covered here:
* Review the [release notes](/help/release-notes/release-notes.md) for known issues.
* Contact Adobe Support for assistance.
