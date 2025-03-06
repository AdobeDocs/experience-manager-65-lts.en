---
title: Understanding the folder structure
description: How to understand the folder structure of AEM Forms workspace source code to customize.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
exl-id: 08e6b25c-eef5-4f29-99fa-524f563e7f25
---
# Understanding the folder structure {#understanding-the-folder-structure}

AEM Forms workspace components are designed on MVC architecture using Backbone. Each component has a file for:

* Model, that contains business logic.
* Template, that is an HTML file containing interface controls.
* View, that acts as a Controller class to Template.

The assets for all the components are placed in the folder structure described below. To access the assets, log in to CRXDE Lite and browse to `/libs/ws/js/runtime/`.

**models** Contains backbone models.

**views** Contains backbone views.

**templates** Contains only the HTML templates for the components.

**routes** Contains universal routes. Templates folder inside routes contains the HTML code and the references to the components.

**services** Contains service interface to call Adobe Experience Manager server APIs on REST endpoint.

**util** Contains generic utilities usable by multiple components.
