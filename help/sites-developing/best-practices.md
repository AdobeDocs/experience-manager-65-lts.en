---
title: Best Practices for AEM developers
description: Adobe Engineering and Consulting teams have developed a comprehensive set of best practices for AEM developers.
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: fc2aa62a-3fc4-491d-aff5-74896998d7d6
---
# Best Practices{#best-practices}

## Best Practices for Developers - Getting Started {#best-practices-for-developers-getting-started}

Adobe Engineering and Consulting teams have developed a comprehensive set of best practices for AEM developers. Adobe developer's adhere to these best practices as they develop core AEM product updates and customer code for customer implementations.

Before you start your AEM development project, first review these best practices:

* [Development Practices](/help/sites-developing/development-practices.md)
* [Content Architecture](/help/sites-developing/content-architecture.md)
* [Software Architecture](/help/sites-developing/software-architecture.md)
* [Coding Tips](/help/sites-developing/coding-tips.md)
* [Code Pitfalls](/help/sites-developing/code-pitfalls.md)
* [JCR Interaction](/help/sites-developing/jcr-integration.md)
* [OSGi Bundles](/help/sites-developing/osgi-bundles.md)
* [Java API Best Practices](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

### Additional Best Practices Information {#additional-best-practices-information}

The following areas have documentation available specific to developing best practices:

* [Sites](#sites)
* [Tooling/HTL](#tooling-htl)

Specific documents are described and linked to in the tables that follow.

For best practices on administering, deploying and maintaining, or authoring, see one of the following:

* [Administering best practices](/help/sites-administering/administer-best-practices.md)
* [Authoring best practices](/help/sites-authoring/best-practices.md)
* [Deploying best practices](/help/sites-deploying/best-practices.md)

## Sites {#sites}

Managing and authoring your website content has some best practices outlined as follows:

<table>
 <tbody>
  <tr>
   <td>Some of the theory behind the standard, touch-enabled UI.</td>
   <td><p><a href="/help/sites-developing/touch-ui-concepts.md">Touch-Enabled UI: Concepts</a></p> <p><a href="/help/sites-developing/touch-ui-structure.md">Touch-Enabled UI: Structure</a></p> </td>
   <td>These documents provide an overview of the concepts, and structure, of the touch-enabled UI.</td>
  </tr>
  <tr>
   <td>Touch-Enabled UI: Customizing consoles </td>
   <td><a href="/help/sites-developing/customizing-consoles-touch.md">Customizing touch-enabled UI consoles</a></td>
   <td>This document describes the best way to extend the consoles for the touch-enabled UI.</td>
  </tr>
  <tr>
   <td>Touch-enabled UI: Customizing page authoring</td>
   <td><a href="/help/sites-developing/customizing-page-authoring-touch.md">Customizing touch-enabled UI page authoring</a></td>
   <td>Describes how to extend page authoring for the touch-enabled UI.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td><a href="/help/sites-developing/workflows-best-practices.md">Developing and Extending Workflows</a></td>
   <td><p>Workflows enable you to automate Adobe Experience Manager (AEM) activities and can represent a large amount of the processing that occurs in an AEM environment, so it is highly recommended to plan your workflows implementations carefully.</p> </td>
  </tr>
 </tbody>
</table>

## Tooling/HTL {#tooling-htl}

HTML Template Language (HTL) is a new HTML templating system, introduced with AEM 6.0. It replaces JSP and ESP as the preferred templating system of AEM.

||||
|---|---|---|
| HTL overview | [HTL overview and syntax](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) |This document describes what HTL is, how to move to HTL, a sample project, syntax, expressions, and statements |
| Using API in java | [HTL Java Use-API](https://helpx.adobe.com/experience-manager/htl/using/use-api.html) |The HTL Java Use-API enables a HTL file to access helper methods in a custom Java class.  |

>[!NOTE]
>
>Following multi-part tutorial might be of interest for the best practice to setup a new AEM project, detailing the Core Components, Editable Templates, Client Libraries and component development:
>[Getting Started with AEM Sites - WKND Tutorial](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)
