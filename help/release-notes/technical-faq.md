---
title: Technical Frequently Asked Questions (FAQ)
description: Frequently asked technical questions about AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
---
# AEM 6.5 LTS Technical FAQ {#technical-faq}

This page is meant to answer some frequently asked technical questions about AEM 6.5 LTS.

## Technical FAQs

### The `/systemalive` endpoint is no longer available in AEM 6.5 LTS.

The Felix System Ready bundle which was configured to provide the `/systemalive` endpoint has been deprecated and superseded by Apache Felix Health Checks. This bundle is no longer included in AEM 6.5 LTS.

The new health check endpoint is available at `/system/health` and is implemented using Apache Felix Health Checks.

For detailed documentation on the Felix Health Check framework, refer to the [felix documentation](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md)

### AEM Groovy console support

The AEM Groovy console version that was being used in AEM 6.5 might not work in AEM 6.5 LTS due to missing guava dependencies. The newly supported version of AEM Groovy console is [19.0.8](https://mvnrepository.com/artifact/be.orbinson.aem/aem-groovy-console/19.0.8)

## Getting Additional Help

If you encounter issues not covered here:
* Review the [release notes](/help/release-notes/release-notes.md) for known issues
* Contact Adobe Support for assistance
