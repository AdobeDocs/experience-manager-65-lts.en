---
title: AEM Forms Server starts processing the documents even before all the services are up and running.
description: AEM Forms Server starts processing the documents even before all the services are up and running on JEE Server and OSGi Server.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: 22dd8daa-b8c6-4e7d-bca3-3958a79fb4b5
---
# AEM Forms Server starts processing the documents even before all the services are up and running{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Issue {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Before the AEM Forms Server is fully up and all the applications are up and running, AEM Forms Server starts processing the documents.


## Applies to {#applies-to}

The solution applies to AEM Forms on JEE Server and AEM Forms on OSGi Server.

## Solution {#solution}

To resolve the issue, add an argument `Dcom.adobe.livecycle.dsc.deferServiceStart=true` to the [batch file](/help/sites-deploying/command-line-start-and-stop.md#windows-platform-start-bat-script-example) during server startup.
