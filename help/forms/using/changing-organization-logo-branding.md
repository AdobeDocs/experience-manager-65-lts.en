---
title: Changing the organization logo for branding
description: To brand AEM Forms workspace provide the logo of your organization by customizing the default logo.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 3aa4aca3-3c94-4936-ba9c-484bbb196256
---
# Changing the organization logo for branding {#changing-the-organization-logo-for-branding}

The organization logo is displayed at the upper-left corner of AEM Forms workspace. To update the logo, follow the [Generic steps of AEM Forms workspace customization](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) and then the following steps.

1. Create a logo and name the file as `NewWorkspace.png`. Place the image file in /apps/ws/images folder using a WebDAV client.

   >[!NOTE]
   >
   >The recommended size of the logo image is 218 px × 20 px.

   >[!NOTE]
   >
   >For more information, see [WebDAV Access](/help/sites-administering/webdav-access.md).

1. Reference the new logo image in style sheet at /apps/ws/css/newStyle.css by adding following style.

   ```css
   #logo {

          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;

   }
   ```
