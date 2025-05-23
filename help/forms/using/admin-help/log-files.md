---
title: Log files
description: Events such as run-time or startup errors are recorded to the application server log files, which can be  opened using any text editor.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: ff4dce07-725e-4750-9e95-4261b50580bd
---
# Log files {#log-files}

Events such as run-time or startup errors are recorded to the application server log files. If you have any problems deploying to the application server, you can use the log files to help you find the problem. You can open the log files using any text editor.

(JBoss) The following log files are in the `[appserver root]/server/'server'/log` directory:

* boot.log
* server.log.*[yyyy-mm-dd]*
* server.log

(WebLogic) Domain log files are in the `[appserverdomain]` directory, and server log files are in the `[appserverdomain]/servers/[appserver name]/logs` directory:

* `access.log`
* `[appserver name].log`
* `[appserver name].out.[incremental number]`

(WebSphere) The following log files are in the `[appserver root]/profiles/default/logs/[appserver name]` directory:

* SystemErr.log
* SystemOut.log
* StartServer.log
