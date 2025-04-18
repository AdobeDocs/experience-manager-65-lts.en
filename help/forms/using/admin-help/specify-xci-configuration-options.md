---
title: Specify XCI configuration options
description: Learn how to specify the XCI configuration options. You can specify a custom XCI file values for Adaptive Form, so that it can be used while form rendering.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: 5fb6e6cc-6af7-4cf5-804b-bb3030079383
---
# Specify XCI configuration options {#specify-xci-configuration-options}

>[!NOTE]
> 
> Ensure that the user has admin privileges to access the administrator console.

Output lets you specify a custom XCI file that it uses for rendering. See [Specify file locations for Output](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output). 

By default, Output overrides some of the options specified in the XCI file, including the following:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

You can select options that cancel the override for the options listed above, in which case Output uses the values specified in the custom XCI file.

1. In administration console, click **Services** > output.
1. Select or deselect the Use System Default XCI Options check box. When this option is selected, Output uses its default values for the packets, creator, producer, and compressObjectStream settings. When this option is deselected, Output uses the values specified in the custom XCI file.
1. Click **Save**.
