---
title: Custom Namespaces
description: Learn how to define and deploy custom namespaces to AEM 6.5 LTS.
solution: Experience Manager, Experience Manager Sites
feature: Developing,JCR
role: Developer
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: c45915cf-e157-4af7-a80d-97b905bcb3a5
    internal-label: Experience Manager Sites
feature_v2:
  - id: c5d917df-d8bd-5e97-a117-6dde1e9f7103
    internal-label: Developing
  - id: f2d27a5f-0d67-4d85-8a24-86a8d8a3574b
    internal-label: Developer tools
subfeature_v2:
  - id: cd14456d-a492-4b5c-8a82-1fbd4460dbd2
    internal-label: Java Content Repository
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---

# Custom Namespaces{#custom-namespaces}

Learn how to define and deploy custom [namespaces](https://experienceleague.adobe.com/en/tools/aem-api-documentation/spec/jcr/1.0/4.5_Namespaces.html) to AEM 6.5 LTS.

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
