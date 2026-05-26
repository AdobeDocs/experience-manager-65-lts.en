---
title: Custom Namespaces
description: Learn how to define and deploy custom namespaces to AEM 6.5 LTS.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
exl-id: a7e5d7b4-3c8f-4e2a-9b1d-5f6c8e3a4d72
---

# Custom Namespaces{#custom-namespaces}

Learn how to define and deploy custom [namespaces](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/1.0/4.5_Namespaces.html) to AEM 6.5 LTS.

Custom namespaces are the optional part of a JCR property preceding a `:`. AEM uses several namespaces such as:

+ `jcr` for JCR system properties
+ `cq` for AEM (formerly known as Adobe CQ) properties
+ `dam` for AEM properties specific to DAM assets
+ `dc` for Dublin Core properties

... and many others.

Namespaces can be used to denote the scope and intent of a property. Creating a custom namespace, often your company name, helps clearly identify nodes or properties specific to your AEM implementation and contain data specific to your business.

Custom namespaces are managed in [Sling Repository Initialization (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html) scripts, and deployed to AEM 6.5 LTS as OSGI configurations added to your AEM project's `ui.apps` content package.

## Resources

+ [Sling Repository Initialization (repoinit) documentation](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios)

## Code

The following code is used to configure a `wknd` namespace.

### RepositoryInitializer OSGi configuration

`/ui.apps/src/main/content/jcr_root/apps/wknd-examples/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~wknd-examples-namespaces.cfg.json`

```json
{
    "scripts": [
        "register namespace (wknd) https://site.wknd/1.0"
    ]
}
```

This allows custom properties using the `wknd` namespace, as denoted as the first parameter after the `register namespace` instruction, to be used in AEM. For more advanced script definitions, review the examples in the [Sling Repository Initialization (repoinit) documentation](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios).
