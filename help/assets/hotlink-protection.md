---
title: Activating hot link protection in Dynamic Media
description: Information on how to activate hot link protection in Dynamic Media.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
role: User, Admin
feature: Configuration
solution: Experience Manager, Experience Manager Assets
exl-id: 56eb956e-c6a8-464b-980a-28e0dab0da7c
---
# Activate hot link protection in Dynamic Media {#activating-hotlink-protection-in-dynamic-media}

Hot linking is when a third-party website uses HTML code to display an image from your website. They use your bandwidth every time the picture is requested because the visitor's browser is accessing it directly from your server. Hotlink *protection* is a method to prevent other websites from directly linking to pictures, CSS, or JavaScript on your webpages. This kind of shield helps reduce unnecessary bandwidth usage under your Dynamic Media account.

[Experience Manager Customer Support](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) can configure a referrer filter at the CDN (Content Delivery Network) level so that Dynamic Media content is only served to websites on your list of permitted websites for the domain.

>[!NOTE]
>
>This feature requires that you use the out-of-the-box CDN that is bundled with Adobe Experience Manager Dynamic Media. Any other custom CDN is not supported with this feature. To activate hot link protection, an Administrator must create an Adobe Customer Support support ticket to request the configuration change to your Dynamic Media account. There is no additional cost for activating hot link protection.
