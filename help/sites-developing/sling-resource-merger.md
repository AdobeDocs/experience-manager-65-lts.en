---
title: Use the Sling Resource Merger in AEM
description: The Sling Resource Merger provides services to access and merge resources
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6fb6e522-fb81-4ba2-90b2-aad68f8bfa9e
---
# Use the Sling Resource Merger in AEM{#using-the-sling-resource-merger-in-aem}

## Purpose {#purpose}

The Sling Resource Merger provides services to access and merge resources. It provides diff (differencing) mechanisms for both:

* **[Overlays](/help/sites-developing/overlays.md)** of resources using the [configured search paths](/help/sites-developing/overlays.md#configuring-the-search-paths).

* **Overrides** of component dialogs for the touch-enabled UI (`cq:dialog`), using the resource type hierarchy (by means of the property `sling:resourceSuperType`).

Sling Resource Merger combines both overlay and override resources (and their properties) with the original resources and properties:

* The content of the customized definition has a higher priority than the original. That is, it *overlays* or *overrides* it.

* Where necessary, [properties](#properties) defined in the customization, indicate how content merged from the original is to be used.

>[!CAUTION]
>
>The Sling Resource Merger and related methods can only be used with [Granite](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/index.html). This situation also means that it is only appropriate for the standard, touch-enabled UI; in particular overrides defined in this manner are only applicable for the touch-enabled dialog of a component.
>
>To overlay or override other areas (including other parts of a touch-enabled component or the classic UI), copy the appropriate node and structure from the original. Place the copy where you define the customization.

### Goals for AEM {#goals-for-aem}

The goals for using the Sling Resource Merger in AEM are to:

* ensure that customization changes are not made in `/libs`.
* reduce the structure that is replicated from `/libs`.

  When using Sling Resource Merger, it is not recommended to copy the entire structure from `/libs`. The reason is because it would result in too much information being held in the customization (usually `/apps`). Duplicating information unnecessarily increases the chance of problems when the system is upgraded.

>[!NOTE]
>
>Overrides are not dependent on the search paths. They use the property `sling:resourceSuperType` to make the connection.
>
>However, overrides are often defined under `/apps`, as best practice in AEM is to define customizations under `/apps`. The reason is because you must not change anything under `/libs`.

>[!CAUTION]
>
>*Do not* change anything in the `/libs` path.
>
>The reason is because the content of `/libs` is overwritten the next time you upgrade your instance. And, it may well be overwritten when you apply either a hotfix or feature pack.
>
>The recommended method for configuration and other changes is:
>
>1. Recreate the required item (that is, as it exists in `/libs`) under `/apps`
>
>1. Make any changes within `/apps`
>

### Properties {#properties}

The resource merger provides the following properties:

* `sling:hideProperties` ( `String` or `String[]`)

  Specifies the property, or list of properties, to hide.

  The wildcard `*` hides all.

* `sling:hideResource` ( `Boolean`)

  It indicates whether the resources are completely hidden, including its children.

* `sling:hideChildren` ( `String` or `String[]`)

  It contains the child node, or list of child nodes, to hide. The properties of the node are maintained.

  The wildcard `*` hides all.

* `sling:orderBefore` ( `String`)

  It contains the name of the sibling node that the current node is positioned in front of.

These properties affect how the corresponding / original resources / properties (from `/libs`) are used by the overlay / override (often in `/apps`).

### Create the structure {#creating-the-structure}

To create an overlay or override you need to recreate the original node, with the equivalent structure, under the destination (usually `/apps`). For example:

* Overlay

    * The definition of the navigation entry for the Sites console, as shown in the rail is defined at:

      `/libs/cq/core/content/nav/sites/jcr:title`

    * To overlay, create the following node:

      `/apps/cq/core/content/nav/sites`

      Then update the property `jcr:title` as required.

* Override

    * The definition of the touch-enabled dialog box for the Texts console is defined as the following:

      `/libs/foundation/components/text/cq:dialog`

    * To override, create the following node. For example:

      `/apps/the-project/components/text/cq:dialog`

To create either, you only need to recreate the skeleton structure. To simplify the recreation of the structure, all intermediary nodes can be of type `nt:unstructured` (they do not have to reflect the original node type. For example, in `/libs`.

So, in the above overlay example, the following nodes are needed:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>When using Sling Resource Merger (that is, when dealing with the standard, touch-enabled UI) it is not recommended to copy the entire structure from `/libs`. The reason is because it would result in too much information being held in `/apps`. As a result, it can cause problems when the system is upgraded.

### Use cases {#use-cases}

With standard functionality, these use cases let you do the following:

* **Add a property**

  The property does not exist in the `/libs` definition, but is required in the `/apps` overlay / override.

    1. Create the corresponding node within `/apps`
    1. Create the new property on this node ``

* **Redefine a property (not auto-created properties)**

  The property is defined in `/libs`, but a new value is required in the `/apps` overlay / override.

    1. Create the corresponding node within `/apps`
    1. Create the matching property on this node (under `apps`)

        * The property has a priority based on the Sling Resource Resolver configuration.
        * Changing the property type is supported.

          If you use a property type different to the one used in `/libs`, then the property type you define is used.

  >[!NOTE]
  >
  >Changing the property type is supported.

* **Redefine an auto-created property**

  By default, auto-created properties (such as `jcr:primaryType`) are not subject to an overlay / override to ensure that the node type currently under `/libs` is respected. To impose an overlay / override you have to recreate the node in `/apps`, explicitly hide the property and redefine it:

    1. Create the corresponding node under `/apps` with the desired `jcr:primaryType`
    1. Create the property `sling:hideProperties` on that node, with the value set to that of the auto-created property; for example, `jcr:primaryType`

       This property, defined under `/apps`, now takes priority over the one defined under `/libs`

* **Redefine a node and its children**

  The node and its children are defined in `/libs`, but a new configuration is required in the `/apps` overlay / override.

    1. Combine the actions of:

        1. Hide children of a node (keeping the properties of the node)
        1. Redefine the property / properties

* **Hide a property**

  The property is defined in `/libs`, but not required in the `/apps` overlay / override.

    1. Create the corresponding node within `/apps`
    1. Create a property `sling:hideProperties` of type `String` or `String[]`. Use to specify the properties to be hidden / ignored. Wildcards can also be used. For example:

        * `*`
        * `["*"]`
        * `jcr:title`
        * `["jcr:title", "jcr:description"]`

* **Hide a node and its children**

  The node and its children are defined in `/libs`, but not required in the `/apps` overlay / override.

    1. Create the corresponding node under `/apps`
    1. Create a property `sling:hideResource`

        * type: `Boolean`
        * value: `true`

* **Hide children of a node (while keeping the properties of the node)**

  The node, its properties and its children are defined in `/libs`. The node and its properties are required in the `/apps` overlay / override, but some or all the child nodes are not required in the `/apps` overlay / override.

    1. Create the corresponding node under `/apps`
    1. Create the property `sling:hideChildren`:

        * type: `String[]`
        * value: a list of the child nodes (as defined in `/libs`) to hide / ignore

       The wildcard &ast; can be used to hide or ignore all child nodes.

* **Reorder nodes**

  The node and its siblings are defined in `/libs`. To change the order, recreate the node in the `/apps` overlay or override. Define its new position by referencing the appropriate sibling node in `/libs`.


    * Use the `sling:orderBefore` property:

        1. Create the corresponding node under `/apps`
        1. Create the property `sling:orderBefore`:

           Specifies the node (as in `/libs`) that the current node is positioned before:

            * type: `String`
            * value: `<before-SiblingName>`

### Invoke the Sling Resource Merger from your code {#invoking-the-sling-resource-merger-from-your-code}

The Sling Resource Merger includes two custom resource providers - one for overlays and another for overrides. Each can be invoked within your code using a mount point:

>[!NOTE]
>
>When accessing your resource, it is recommended to use the appropriate mount point.
>
>This approach invokes the Sling Resource Merger and returns the fully merged resource. It also reduces the amount of structure that you must copy from `/libs`.

* Overlay:

    * purpose: merge resources based on their search path
    * mount point: `/mnt/overlay`
    * usage: `mount point + relative path`
    * example:

        * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Override:

    * purpose: merge resources based on their super type
    * mount point: `/mnt/overide`
    * usage: `mount point + absolute path`
    * example:

        * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

### Example of usage {#example-of-usage}

Some examples are covered:

* Overlay:

    * [Customizing the Consoles](/help/sites-developing/customizing-consoles-touch.md)
    * [Customizing Page Authoring](/help/sites-developing/customizing-page-authoring-touch.md)

* Override:

    * [Configuring your Page Properties](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
