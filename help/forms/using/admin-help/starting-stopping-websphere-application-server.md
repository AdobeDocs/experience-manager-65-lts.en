---
title: Starting and stopping WebSphere Application Server
description: Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. This document describes how to start and stop the WebSphere Application Server.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: 20cd6efb-edcf-4c87-b0f5-bdec5a0f6280
---
# Starting and stopping WebSphere Application Server {#starting-and-stopping-websphere-application-server}

Several procedures require you to stop or start the instance of WebSphere where you want to deploy AEM forms products. If you are unsure whether the application server has started, you can first view the status of WebSphere Application Server.

## View the status of WebSphere Application Server {#view-the-status-of-websphere-application-server}

1. From a command prompt, go to the `[appserver root]/bin` directory.
1. Enter the following command, replacing *server_name* with the name of your WebSphere Application Server:

    * (Windows) `serverStatus.bat`*server_name*
    * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## Start WebSphere Application Server {#start-websphere-application-server}

1. From a command prompt, go to the `[appserver root]/bin` directory.
1. Enter the following command, replacing *server_name* with the name of your WebSphere Application Server:

    * (Windows) `startServer.bat`*server_name*
    * (Linux, UNIX) ./ `startServer.sh`*server_name*

## Stop WebSphere Application Server {#stop-websphere-application-server}

1. From a command prompt, go to the `[appserver root]/bin` directory.
1. Enter the following command, replacing *server_name* with the name of your WebSphere Application Server:

    * (Windows) `stopServer.bat`*server_name*
    * (Linux, UNIX) ./ `stopServer.sh`*server_name*
