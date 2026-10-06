---
title: AEM Forms Server starts processing the documents even before all the services are up and running.
description: AEM Forms Server starts processing the documents even before all the services are up and running on JEE Server and OSGi Server.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
removedfrom6.5.2025: 'yes'
exl-id: 22dd8daa-b8c6-4e7d-bca3-3958a79fb4b5
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
feature_v2:
  - id: e72c079d-d036-46d5-b43d-29b276a174c2
    internal-label: Authoring and publishing content
subfeature_v2:
  - id: a26f372d-6d7c-452b-81df-594dd4365ae1
    internal-label: Adaptive Forms
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# AEM Forms Server starts processing the documents even before all the services are up and running{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Issue {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Before the AEM Forms Server is fully up and all the applications are up and running, AEM Forms Server starts processing the documents.


## Applies to {#applies-to}

The solution applies to AEM Forms on JEE Server and AEM Forms on OSGi Server.

## Solution {#solution}

To resolve the issue, add an argument `Dcom.adobe.livecycle.dsc.deferServiceStart=true` to the [batch file](/help/sites-deploying/command-line-start-and-stop.md#windows-platform-start-bat-script-example) during server startup.
