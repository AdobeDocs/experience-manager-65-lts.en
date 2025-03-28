---
title: Naming conventions for assets testing
description: Nodes in the repository are subject to naming conventions of the Java Content Repository. However, Adobe Experience Manager imposes further conventions for the name of asset nodes.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 37de1a8b-b7db-469e-98a7-20ddb6218510
---
# Naming conventions for assets testing{#naming-conventions-for-assets-testing}

Nodes in the repository are subject to naming conventions of the [Java Content Repository](/help/sites-developing/the-basics.md#java-content-repository). However, Adobe Experience Manager imposes further conventions for the name of asset nodes.

## Classic UI {#classic-ui}

The classic UI imposes tighter restrictions:

* Validates the asset name when an explicit node name when either:

    * an asset title is provided for conversion into the node name
    * an explicit node name is provided

* Valid characters (only these characters are actually valid when an asset is created from within the classic UI):

    * 'a' to 'z'
    * 'A' to 'Z'
    * '0' to '9'
    * _ (underscore)
    * `-` (dash/minus)
