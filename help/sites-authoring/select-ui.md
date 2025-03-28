---
title: Selecting your user interface in AEM
description: Configure which interface you use to work in Adobe Experience Manager 6.5.
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: 508f9dfb-1a4e-45bd-acdd-48cc910bdd0f
---
# Selecting your UI{#selecting-your-ui}

The Adobe Experience Manager (AEM) touch-enabled UI is the standard UI. However, there may be times when the user wants to switch to the [classic UI](/help/sites-classic-ui-authoring/classicui.md). There are several options for doing this.

There are various locations where you can define which UI is to be used:

* [Configuring the default UI for your instance](#configuring-the-default-ui-for-your-instance)
  This sets the default UI to show at user login. The user may be able to override this and select a different UI for their account or current session.

* [Setting Classic UI Authoring for your account](/help/sites-authoring/select-ui.md#setting-classic-ui-authoring-for-your-account)
  This sets the UI to be the default when editing pages, although the user can override this and select a different UI for their account or current session.

* [Switching to the classic UI for the current session](#switching-to-classic-ui-for-the-current-session)
  Switches to the classic UI for the current session.

* For the case of [page authoring, the system makes certain overrides in the relation to the UI](#ui-overrides-for-the-editor).

>[!CAUTION]
>
>Various options for switching to the classic UI are not immediately available out-of-the-box, they must be configured for your instance.
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

>[!NOTE]
>
>Instances upgraded from a previous version retain the classic UI for page authoring.
>
>After upgrade, page authoring is not automatically switched to the touch-enabled UI, but you can configure this using the [OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service). See [UI Overrides for the Editor](#ui-overrides-for-the-editor).

## Configuring the Default UI for Your Instance {#configuring-the-default-ui-for-your-instance}

A system administrator can configure the UI that is seen at startup and login by using [Root Mapping](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping).

This can be overridden by user defaults or session settings.

## Setting Classic UI Authoring for Your Account {#setting-classic-ui-authoring-for-your-account}

Each user can access their own [user preferences](/help/sites-authoring/user-properties.md#userpreferences) to define if they want to use the classic UI for page authoring, instead of the default UI.

This can be overridden by session settings.

## Switching to Classic UI for the Current Session {#switching-to-classic-ui-for-the-current-session}

When using the touch-enabled UI, desktop users might want to revert to the classic (desktop only) UI. There are several methods to switch to the classic UI for the current session:

* **Navigation Links**

  >[!CAUTION]
  >
  >This option for switching to the classic UI is not immediately available out-of-the-box, it must be configured for your instance.
  >
  >
  >See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

  If this is enabled, whenever you mouseover an applicable console, an icon appears (a monitor symbol). Tapping/clicking this opens the appropriate location in the classic UI.

  For example, the links from **Sites** to **siteadmin**:

  ![syui-01](assets/syui-01.png)

* **URL**

  The classic UI can be accessed using the URL for the welcome screen at `welcome.html`. For example:

  `https://localhost:4502/welcome.html`

  >[!NOTE]
  >
  >The touch-enabled UI can be accessed via `sites.html`. For example:
  >
  >
  >`https://localhost:4502/sites.html`

### Switching to Classic UI when Editing a Page {#switching-to-classic-ui-when-editing-a-page}

>[!CAUTION]
>
>This option for switching to the classic UI is not immediately available out-of-the-box, it must be configured for your instance.
>
>See [Enabling Access to Classic UI](/help/sites-administering/enable-classic-ui.md) for more information.

If enabled, **Open the Classic UI** is available from the **Page Information** dialog:

![syui-02](assets/syui-02.png)

### UI Overrides for the Editor {#ui-overrides-for-the-editor}

The settings defined by a user or system administrator can be overridden by the system if there is page authoring.

* When authoring pages:

    * Use of the classic editor is forced when accessing the page using `cf#` in the URL. For example:
      `https://localhost:4502/cf#/content/geometrixx/en/products/triangle.html`

    * Use of the touch-enabled editor is forced when using `/editor.html` in the URL or when using a touch device. For example:
      `https://localhost:4502/editor.html/content/geometrixx/en/products/triangle.html`

* Any forcing is temporary and only valid for the browser session

    * A cookie set is set dependent on whether touch-enabled ( `editor.html`) or classic ( `cf#`) is used.

* When opening pages through `siteadmin`, checks are made for the existence of the following:

    * The cookie
    * A user preference
    * If neither exist, it defaults to the definitions set in the [OSGi configuration](/help/sites-deploying/configuring-osgi.md) of the **WCM Authoring UI Mode Service** ( `AuthoringUIMode` service).

>[!NOTE]
>
>If [a user has already defined a preference for page authoring](#settingthedefaultauthoringuiforyouraccount), that is not overridden by changing the OSGi property.

>[!CAUTION]
>
>Due to the use of cookies, as already described, it is not recommended to either:
>
>* Manually edit the URL - A non-standard URL could result in an unknown situation and lack of functionality.
>* Have both editors open at the same time - For example, in separate windows.
