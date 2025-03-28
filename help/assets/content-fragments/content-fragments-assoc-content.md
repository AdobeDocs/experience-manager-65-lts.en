---
title: Associated Content
description: Understand how AEM's associated content feature provides the connection so that assets can be optionally used with the fragment when it is added to a content page, adding additional flexibility to headless content delivery.
feature: Content Fragments
role: User
solution: Experience Manager, Experience Manager Assets
exl-id: 5e0a8316-4207-417a-9855-dfac53ca0eb0
---
# Associated Content{#associated-content}

AEM's Associated content feature provides the connection so that assets can (optionally) be used with the fragment when it is added to a content page. This provides flexibility for your headless content delivery by [providing a range of assets to access when using the content fragment on a page,](/help/sites-authoring/content-fragments.md#using-associated-content) while also helping to reduce the time required to search for the appropriate asset. Any associated content can be configured using the Content Fragment editor.

## Adding Associated Content {#adding-associated-content}

>[!NOTE]
>
>There are various methods of adding [visual assets (for example, images)](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) to the fragment and/or page.

To make the association you first need to [add your media assets to a collection](/help/assets/manage-collections.md). After that is done you can:

1. Open your fragment and select **Associated Content** from the side panel.

   ![Associated Content](assets/cfm-assoc-content-01.png)

1. Depending on whether any collections have already been associated, or not - select either:

   * **Associate Content** - this will be the first associated collection
   * **Associate Collection** - associated collections that are already configured

1. Select the required collection.

   You can optionally add the fragment itself to the selected collection; this aids tracking.

   ![Select collection](assets/cfm-assoc-content-02.png)

1. Confirm (with **Select**). The collection will be listed as associated.

   ![cfm-6420-05](assets/cfm-assoc-content-03.png)

## Editing Associated Content {#editing-associated-content}

Once you have associated a collection you can:

* **Remove** the association.
* **Add Assets** to the collection.
* Select an asset for further action.
* Edit the asset.
