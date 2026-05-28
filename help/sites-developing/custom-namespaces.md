---
title: Custom Namespaces
description: Learn how to define and deploy custom namespaces to AEM 6.5 LTS.
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
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

Custom namespaces are managed in [Sling Repository Initialization (repoinit)](https://sling.apache.org/documentation/bundles/repository-initialization.html) scripts, and deployed as OSGi configurations in your project's configuration package (for example, `ui.config`).

## Resources {#resources}

+ [Sling Repository Initialization (repoinit) documentation](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios)

## Code {#code}

The following code is used to configure a `wknd` namespace.

### RepositoryInitializer OSGi configuration

`/ui.config/src/main/content/jcr_root/apps/wknd-examples/osgiconfig/config/org.apache.sling.jcr.repoinit.RepositoryInitializer~wknd-examples-namespaces.cfg.json`

```json
{
    "scripts": [
        "register namespace (wknd) https://site.wknd/1.0"
    ]
}
```

This allows custom properties using the `wknd` namespace, as denoted by the first parameter after the `register namespace` instruction, to be used in AEM. For more advanced script definitions, review the examples in the [Sling Repository Initialization (repoinit) documentation](https://sling.apache.org/documentation/bundles/repository-initialization.html#repoinit-parser-test-scenarios).
