---
title: How to restart AEM SDK?
description: Best practices to restart AEM SDK
role: Admin, Developer, User
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
solution: Experience Manager, Experience Manager Forms
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: 68935045-89b1-4219-b111-88a4600200df
---
# Restarting the AEM SDK 

If you restart the AEM SDK by stopping the Java™ processes, may lead to inconsistencies in the AEM development environment an error occurs as:

`javax.jcr.RepositoryException: Applying repoinit operation failed despite retry; set loglevel to DEBUG to see all exceptions. Last exception message was: Failed to set ACL (javax.jcr.ValueFormatException: Invalid type: 0) AclLine ALLOW {principals=[forms-xfa-writers], privileges=[jcr:modifyProperties]} restrictions=[rep:glob=[*/jcr:content/*], rep:itemNames=[xfaForm], fd:condition=[xfaForm, 1]]`

![Restart-aem-sdk-error](/help/forms/using/assets/restart-sdk-error.png)

## Solution

To restart the AEM SDK, go to active command window and press `Ctrl + C` command to restart the SDK. 

It is recommended to use the 'Ctrl + C' command to restart the SDK. Restarting the AEM SDK using alternative methods, for example, stopping Java™ processes, may lead to inconsistencies in the AEM development environment.
