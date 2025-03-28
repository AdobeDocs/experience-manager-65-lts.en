---
title: Configuring Task Manager endpoints
description: Learn how to configure Task Manager endpoints to invoke the service. Different settings are required for configuring Task Manager endpoints.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: 57fd8b5d-6347-4b83-9489-e8ee59ee39a5
---
# Configuring Task Manager endpoints {#configuring-task-manager-endpoints}

Task Manager endpoints enable Workspace users to invoke the service.

**Task Manager endpoint settings**

Use the following settings to configure a Task Manager endpoint.

**Name:** (Mandatory) Identifies the endpoint. The name is displayed in the card view in Workspace. Do not include a < character because it will truncate the name displayed in Workspace. If you’re entering a URL as the name of the endpoint, ensure that it conforms with the syntax rules specified in RFC1738.

**Description:** A description of the endpoint. Do not include a < character because it will truncate the description displayed in Workspace.

**Task Instructions:** Instructions for the user who starts this workflow.

**Process Owner:** The name of the person who is responsible for the process.

**User Can Forward Task:** Allows the user to forward the initial task.

**Show Attachment Window:** Allows the user to see the attachment window.

**Allow Attachment Adding:** Allows the user to add attachments and notes.

**Task Initially Locked:** Locks the initial task.

**Add ACLs for Shared Queues:** The initial task is created with ACLs for shared queue users.

**Categorization:** (Mandatory) The category in which the user will see the form in Workspace. Select a category from the list, or select New Category to add a category.

**Operation Name:** (Mandatory) A list of operations that can be assigned to the endpoint.
