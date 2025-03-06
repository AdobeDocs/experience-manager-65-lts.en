---
title: Specify security settings
description: Learn how to specify security settings to protect XML data files. The security setting feature controls the external entities in XML inputs.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
---
# Specify security settings {#specify-security-settings}

>[!NOTE]
> 
> Ensure that the user has admin privileges to access the administrator console.

Output enables you to control whether external entities in XML inputs are resolved. By default, they are resolved, but you can change this behavior to increase the security of your AEM forms system.

**Prevent the processing of XML data files that contain references to external entities**

1. In administration console, click Services &gt; output.
1. Clear the Resolve External Entities check box.
1. Click Save.
