---
title: Optional - How to Create Single Page Applications (SPAs) with Adobe Experience Manager
description: In this optional continuation of the Adobe Experience Manager (AEM) Headless Developer Journey, you learn how AEM can combine headless delivery with traditional full-stack CMS features and how you can create editable SPAs using AEM's SPA Editor framework.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer
exl-id: 47e73efa-997d-44d9-bb41-6f550eac137a
---
# How to Create Single Page Applications (SPAs) with AEM {#create-spa}

In this optional continuation of the [AEM Headless Developer Journey,](overview.md) you learn how Adobe Experience Manager (AEM) can combine headless delivery with traditional full-stack CMS features and how you can create editable SPAs using AEM's SPA Editor framework, and integrate external SPAs, enabling editing capabilities as required.

## The Story So Far {#story-so-far}

At this point, you should have completed the entire [AEM Headless Developer Journey](overview.md) and understand the basics of headless delivery in AEM including an understanding of:

* The difference between headless and headful content delivery.
* AEM's headless features.
* How to organize and AEM Headless project.
* How to create headless content in AEM.
* How to retrieve and update headless content in AEM.
* How to go live with an AEM Headless project.

So you have now either gone live with your first AEM Headless project, or have the knowledge to do so. Congratulations!

So why are you reading this additional, optional continuation of the journey? Likely, you recall that in the [Getting Started](getting-started.md#integration-levels), there was a brief discussion about how AEM not only supports headless delivery and traditional full-stack models, but can also support hybrid models that combine the advantages of both. Although not the traditional headless model, such hybrid models can offer unprecedented flexibility to certain projects.

This article builds on your knowledge of AEM Headless by exploring in-depth how you can create your own single-page applications (SPAs) that are editable in AEM. In this way, you can create content and delivery it headlessly to a SPA, but that SPA remains editable in AEM.

## Objective {#objective}

This document helps you understand how Single Page Applications are developed using the AEM SPA Editor framework. After reading this document, you should:

* Understand the basic function of the SPA Editor.
* Know the requirements for building a fully editable SPA for AEM.
* Understand how external SPAs can be integrated into AEM.
* Understand how server-side rendering should or should not be implemented.

## Requirements and Prerequisites {#requirements-prerequisites}

There are several requirements before you begin working with SPAs in AEM.

### Knowledge {#knowledge}

* Development experience creating SPAs with React or Angular frameworks
* Basic AEM skills creating Content Fragments and using the editor
* Be sure to review the document [Headful and Headless in AEM](/help/sites-developing/headful-headless.md) to understand the various levels of SPA integration possible.

### Tools {#tools}

* Sandbox access for testing deploying your project
* Local development instance for data modeling and testing
* Existing external SPA (optional, depending on what integration model is chosen)
* AEM Project Archetype

## What is a SPA? {#what-is-a-spa}

A single-page application (SPA) differs from a conventional page in that it is rendered client-side and is primarily JavaScript-driven, relying on Ajax calls to load data and dynamically update the page. Most or all content is retrieved once in a single page load with additional resources loaded asynchronously as needed based on user interaction with the page.

This reduces the need for page refreshes and presents an experience to the user that is seamless, fast, and feels more like a native app experience.

The AEM SPA Editor allows front-end developers to create SPAs that can be integrated into an AEM site, allowing the content authors to edit the SPA content as easily as any other AEM content.

## Why a SPA? {#why-spa}

By being faster, fluid, and more like a native application, a SPA becomes an attractive experience not only for the visitor of the webpage, but also for marketers and developers due to the nature of how SPAs work.

For a full description of SPAs and why you would use them, see the [additional resources](#additional-resources) section for links to more in-dept documentation.

## How AEM Handles SPAs

Developing single page applications on AEM assumes that the front-end developer observes standard best practices when creating an SPA. As a front-end developer, if you follow these general best practices and a few AEM-specific principles, your SPA will be functional with AEM and its content-authoring capabilities.

* **Portability** - As with any components, the SPA components should be built to be as portable as possible. The SPA should be built with portably and reusable components.
* **AEM Drives Site Structure** - The front-end developer creates components and owns their internal structure, but relies on AEM to define the content structure of the site.
* **Dynamic Rendering** - All rendering should be dynamic.
* **Dynamic Routing** - The SPA is responsible for the routing and AEM listens to it and fetches based on it. Any routing should be dynamic as well.

For a full description of how AEM handles SPAs, see the [additional resources](#additional-resources) section for links to more in-dept documentation.

## The AEM SPA Editor {#aem-spa-editor}

Sites built using common SPA frameworks such as React and Angular load their content via dynamic JSON and do not provide the HTML structure that is necessary for the AEM Page Editor to be able to place edit controls.

To enable the editing of SPAs within AEM, a mapping between the JSON output of the SPA and the content model in the AEM repository is needed to save changes to the content.

SPA support in AEM introduces a thin JS layer that interacts with the SPA JS code when loaded in the Page Editor with which events can be sent and the location for the edit controls can be activated to allow in-context editing. This feature builds on the Content Services API Endpoint concept because the content from the SPA must be loaded by way of Content Services.

For a full description of the AEM SPA Editor, see the [additional resources](#additional-resources) section for links to more in-dept documentation.

## Accommodating Existing SPAs {#existing-spas}

If you have an existing SPA, AEM supports embedding it into AEM so it is visible to your content authors in the AEM Editor. This can be useful to view the content they are creating via Content Fragments in context of the end application where it will be consumed.

Also, with only small changes, you can enable certain editing ability to the external SPA within the AEM Editor.

The RemotePage component allows rendering of an external SPA in AEM.

For a full description of how to make an external SPA editable in AEM, see the [additional resources](#additional-resources) section for links to more in-dept documentation.

## What's Next {#what-is-next}

To gets started developing your own SPAs for AEM, review the following documents:

* [SPA WKND Tutorial](/help/sites-developing/spa-wknd.md)
* [Getting Started Using React](/help/sites-developing/spa-getting-started-react.md)
* [Getting Started Using Angular](/help/sites-developing/spa-getting-started-angular.md)

If you must adapt an existing SPA to use it in AEM, review the following documents:

* [The RemotePage Component](/help/sites-developing/spa-remote-page.md)
* [Editing an External SPA within AEM](/help/sites-developing/spa-edit-external.md)

See below for [additional resources](#additional-resources) that can take you deeper into SPA topics in AEM.

## Additional Resources {#additional-resources}

The following are some additional resources that do a deeper dive on some concepts mentioned in this document.

* [Headful and Headless in AEM](/help/sites-developing/headful-headless.md) - A description of the different delivery models available in AEM
* [SPA Introduction and Walkthrough.](/help/sites-developing/spa-walkthrough.md) - A good introduction to SPAs in AEM
* [Developing SPAs for AEM](/help/sites-developing/spa-architecture.md) - Guidelines on how to develop SPAs for AEM
* [SPA Editor Overview](/help/sites-developing/spa-overview.md) - Details of how the SPA Editor works
* [SPA Reference Documents](/help/sites-developing/spa-reference-materials.md) - JavaScript API references and links to the open-source AEM SPA GitHub projects
* [Content Fragments](/help/assets/content-fragments/content-fragments.md) - How to create Content Fragments
* [AEM Project Archetype](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html) - Maven template that creates a minimal, best-practices-based Adobe Experience Manager (AEM) project as a starting point for your website
