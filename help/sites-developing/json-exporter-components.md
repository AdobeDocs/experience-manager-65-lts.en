---
title: Enabling JSON Export for a Component
description: Components can be adapted to generate JSON export of their content based on a modeler framework.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: aeb8e954-dd6c-4e18-bb78-6eaac86fa4b9
---
# Enable JSON Export for a component{#enabling-json-export-for-a-component}

Components can be adapted to generate JSON export of their content based on a modeler framework.

## Overview {#overview}

The JSON export is based on [Sling Models](https://sling.apache.org/documentation/bundles/models.html), and on the [Sling Model Exporter](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) framework (which itself relies on [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations)).

This approach means that the component must have a Sling Model if it must export JSON. Therefore, follow these two steps to enable JSON export on any component.

* [Define a Sling Model for the component](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Annotate the Sling Model interface](#annotate-the-sling-model-interface)

## Define a Sling Model for the component {#define-a-sling-model-for-the-component}

First, a Sling Model must be defined for the component.

>[!NOTE]
>
>For an example of using Sling Models, see [Developing Sling Model Exporters in AEM](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter).

The Sling Model implementation class must be annotated with the following:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Doing so ensures that your component could be exported on its own, using the `.model` selector and the `.json` extension.

In addition, it specifies that the Sling Model class can be adapted into the `ComponentExporter` interface.

>[!NOTE]
>
>Jackson annotations are not specified at the Sling Model class level, but rather at the Model interface level. This approach is to ensure that the JSON export is considered as part of the component API.

>[!NOTE]
>
>The `ExporterConstants` and `ComponentExporter` classes come from the `com.adobe.cq.export.json` bundle.

### Use multiple selectors {#multiple-selectors}

Although not a standard use case, it is possible to configure multiple selectors in addition to the `model` selector.

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

However, in such a case the `model` selector must be the first selector and the extension must be `.json`.

## Annotate the Sling Model interface {#annotate-the-sling-model-interface}

For the JSON Exporter framework to process it, the Model interface must implement the `ComponentExporter` interface (or `ContainerExporter` for a container component).

The corresponding Sling Model interface ( `MyComponent`) would be then annotated using [Jackson annotations](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) to define how it should be exported (serialized).

The Model interface must be properly annotated to define which methods are serialized. By default, all methods that respect the usual naming convention for getters are serialized and derive their JSON property names naturally from the getter names. This approach can be prevented or overridden using `@JsonIgnore` or `@JsonProperty` to rename the JSON property.

## Example {#example}

The Core Components have supported JSON export since release [1.1.0 of the core components](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction) and can be used as a reference.

For an example, see the Sling Model implementation of the Image Core Component and its annotated interface.

CODE ON GITHUB

You can find the code of this page on GitHub

* [Open aem-core-wcm-components project on GitHub](https://github.com/adobe/aem-core-wcm-components)
* Download the project as [a ZIP file](https://codeload.github.com/adobe/aem-core-wcm-components/zip/main)


## Related documentation {#related-documentation}

* The [Content Fragments topic in the Assets user guide](https://experienceleague.adobe.com/en/docs/experience-manager-64/assets/home#)
* [Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md)
* [Authoring with Content Fragments](/help/sites-authoring/content-fragments.md)
* [JSON Exporter for Content Services](/help/sites-developing/json-exporter.md)
* [Core Components](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction) and the [Content Fragment component](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/content-fragment-component)
