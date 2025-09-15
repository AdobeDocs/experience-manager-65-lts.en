---
title: Technical Frequently Asked Questions (FAQ)
description: Frequently asked technical questions about AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
---
# AEM 6.5 LTS Technical FAQ {#technical-faq}

This page is meant to answer some frequently asked technical questions about AEM 6.5 LTS.

## Technical FAQs

### The `/systemalive` endpoint is no longer available in AEM 6.5 LTS.

The Felix System Ready bundle which was configured to provide the `/systemalive` endpoint has been deprecated and superseded by Apache Felix Health Checks. This bundle is no longer included in AEM 6.5 LTS.

The new health check endpoint is available at `/system/health` and is implemented using Apache Felix Health Checks.

For detailed documentation on the Felix Health Check framework, refer to the [felix documentation](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### AEM Groovy console support

The AEM Groovy console version that was being used in AEM 6.5 might not work in AEM 6.5 LTS due to missing guava dependencies. The newly supported version of the AEM Groovy console is [19.0.8](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

### Does AEM 6.5 LTS support user-sync?

Yes, AEM 6.5 LTS supports user-sync. There is no change in the functionality of user-sync between AEM 6.5 and 6.5 LTS.

### The Uber JAR on Maven Central appears to be corrupted — what’s the issue?

Verify that you are using the Uber JAR with the `apis` classifier. Note that the packaging structure of the Uber JAR has changed in AEM 6.5 LTS. For more information, see [Update the AEM Uber Jar version](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Getting Additional Help

If you encounter issues not covered here:
* Review the [release notes](/help/release-notes/release-notes.md) for known issues.
* Contact Adobe Support for assistance.
