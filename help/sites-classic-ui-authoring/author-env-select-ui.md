---
title: Selecting your UI
description: For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 781b580a-e4d1-419e-afb1-884c8fb634b9
---
# Selecting your UI{#selecting-your-ui}

Since the touch-enabled UI supersedes the classic UI, the user or administrator of the AEM instance must make an active decision to continue using the classic UI. Because the classic UI is no longer maintained, there is no way for the authoring user to simply switch from the classic UI to the equivalent in the touch-enabled UI.

For convenience to authoring users, the touch-enabled UI does allow for switching to the classic UI when necessary. See the [Selecting your UI](/help/sites-authoring/select-ui.md) in the standard Authoring documentation for details.

>[!NOTE]
>
>Instances upgraded from a previous version will retain the classic UI for page authoring.
>
>After upgrade, page authoring will not be automatically switched to the touch-enabled UI, but you can configure this usingthe[OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). See [UI Overrides for the Editor](#uioverridesfortheeditor).

## Configuring the Default UI for Your Instance {#configuring-the-default-ui-for-your-instance}

A system administrator can configure the UI that is seen at startup and login by using [Root Mapping](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

This can be overridden by user defaults or session settings.
