---
title: Frequently Asked Questions (FAQ)
description: Frequently asked questions about AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: d18c9dc3-fdcc-4558-b9b6-ecf1ce61048a
---
# AEM 6.5 LTS Frequently Asked Questions (FAQ) {#faq}

This page is meant to answer some frequently asked questions about AEM 6.5 LTS.

## Why has Adobe released 6.5 LTS for AEM? 

Adobe remains deeply committed to the security and stability of the applications it provides. AEM 6.5 Long-term Support lays the foundation for future updates for AEM 6.5. Notably, AEM 6.5 LTS includes support for Oracle Java 17 and Java 21, and will be the AEM branch that receives new AEM features and innovations. 

## I’m an on-premise customer, what happens if I don’t upgrade to AEM 6.5 LTS?

AEM 6.5 LTS includes important security and stability updates including support for Oracle Java 17 and Java 21. While Adobe will continue to support AEM 6.5 for at least the next 2 years, it is recommended that organizations begin to plan for an upgrade to 6.5 LTS. 

## Will my existing customizations and integrations be affected if I upgrade to AEM 6.5 LTS?

While AEM 6.5 LTS aims to maintain backward compatibility, some legacy features and artifacts have been removed. 
It is essential to review the [release notes](/help/release-notes/release-notes.md#deprecated-and-removed-features) and use the [AEM Analyzer tool](/help/sites-deploying/aem-analyzer.md) to assess the impact on your customizations and integrations.

## How can I ensure a smooth transition to AEM 6.5 LTS?

To ensure a smooth transition, it is recommended to: 

* Review the [release notes](/help/release-notes/release-notes.md) and documentation thoroughly. 
* Use the [AEM Analyzer tool](/help/sites-deploying/aem-analyzer.md) to assess the complexity of the upgrade. 
* Plan and allocate sufficient time and resources for the upgrade process. 
* Engage with Adobe support and enablement sessions for guidance and assistance.

## What are AEM 6.5 LTS Service Packs?

AEM 6.5 LTS Service Packs are a cumulative update that includes all the fixes and improvements made to AEM 6.5 LTS since its initial release. It is recommended to apply the latest service pack to ensure your AEM instance is up-to-date with the latest features and security patches.

## I am currently on AEM 6.5, can I directly upgrade to AEM 6.5 LTS Service Pack without upgrading to AEM 6.5 LTS GA release?

Yes, you can directly upgrade from AEM 6.5 to any AEM 6.5 LTS Service Pack. It is recommended to review the [release notes](/help/release-notes/release-notes.md) and [Upgrading to AEM 6.5 LTS](/help/sites-deploying/upgrade.md) section.

## I am currently on AEM 6.5 LTS GA, do I need to make any code changes to upgrade to AEM 6.5 LTS Service Packs?

No, you do not need to make any code changes to upgrade from AEM 6.5 LTS to AEM 6.5 LTS Service Packs. However, it is always recommended review the [release notes](/help/release-notes/release-notes.md) and test your customizations and integrations in a staging environment before applying the service pack to your production instance.

## I want to start fresh with a new AEM 6.5 LTS setup, can I directly start with AEM 6.5 LTS Service Pack?

Yes, you can directly set up a new AEM 6.5 LTS Service Pack without setting up AEM 6.5 LTS GA build. It is recommended to review the [release notes](/help/release-notes/release-notes.md) and [Custom Standalone Install](/help/sites-deploying/custom-standalone-install.md) section for more details.