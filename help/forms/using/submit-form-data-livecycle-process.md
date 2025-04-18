---
title: Configuring AEM Forms to submit data to an AEM Forms on JEE process
description: Integrate adaptive forms with AEM Forms on JEE processes for processing form data.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: c888da5d-6a98-4139-9656-a187177efcb0
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
---
# Configuring AEM Forms to submit form data to an AEM form on JEE process{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptive forms support submitting data to AEM Forms on JEE process for further processing. It lets you trigger an AEM Forms on JEE process with the data available from the submitted form. Perform the following steps so you can enable your AEM Forms instance to submit an adaptive form to AEM Forms on JEE process:

## Configure your AEM Forms Server {#configure-your-aem-forms-server}

Perform the following steps so you can enable your AEM Forms Server to submit data to an AEM Forms on JEE server:

1. Go to AEM web configuration console at https://[*host*]:[*port*]/system/console/configMgr.

1. Locate and click the **Adobe LiveCycle Client SDK Configuration** component.
1. Click to edit the configuration server URL, username, and password for the AEM Forms on JEE server.
1. Review the settings and click **Save**.

![Adobe LiveCycle Client SDK configuration](assets/clientsdkconfiguration.jpg)

## Map data with process fields {#map-data-with-process-fields}

After configuring AEM Forms, map the data XML and attachments from the submitted form to the fields in the AEM Forms on JEE process. Do the following:

1. In the AEM web configuration console, click to edit the **Guide LiveCycle Process Locator and Invoker** configuration.
1. Specify the following parameters:

    * **Name of the data xml parameter** (mandatory): Specify the XML property file of the AEM Forms on JEE process that must process the submitted data. The default value is **dataxml**.
    
    * **Name of the file attachments parameter** (optional): Specify the list of document objects that the AEM Forms on JEE process must process. The default value is **fileAttachmentsList**.

1. Review the settings and click **Save**.

![Guide LiveCycle Process Locator and Invoker](assets/test3.jpg)

Once configured, the Submit to Forms Workflow submit action lists the AEM Forms on JEE server processes containing the specified data xml parameter.
