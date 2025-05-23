---
title: Configure Dynamic Media Publish Setup for Image Server
description: Learn how to configure Dynamic Media Publish Setup for Image Server so you can publish assets. You can also test your assets before making them public.
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
solution: Experience Manager, Experience Manager Assets
exl-id: 9cad4bbc-64f6-4ea2-a9b2-b6b9aaa72f11
---
# Configure Dynamic Media Publish Setup for Image Server

Configuring Dynamic Media Publish Setup options are available only if the following are true:

* You are running Dynamic Media in Scene7 mode. See [Enable Dynamic Media in Scene7 mode](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode).
* You have an *existing* **[!UICONTROL Dynamic Media Configuration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager. See [Create a Dynamic Media Configuration in Cloud Services](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
* You are an Experience Manager system administrator with administrator privileges.

Experienced website developers and programmers are intended to use Dynamic Media Publish Setup. Adobe Dynamic Media recommends that users who change publish settings be familiar with Adobe Dynamic Media, HTTP protocol standards and conventions, and basic imaging technology.

The Dynamic Media Publish Setup page establishes default settings that determine how assets are delivered from Adobe Dynamic Media servers to web sites or applications. If no setting is specified, the Adobe Dynamic Media server delivers an asset according to a default setting that was configured on the Dynamic Media Publish Setup page.

See also [Optional - Setup and configuration of Dynamic Media - Scene7 mode settings](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) for more optional configuration tasks.

>[!NOTE]
>
>Upgrading from Dynamic Media Classic to Dynamic Media on Adobe Experience Manager? The [General Settings](/help/assets/dm-general-settings.md) page and Publish Setup page in Dynamic Media are pre-populated with the values taken from your Dynamic Media Classic account. The exceptions are all the values that are listed under the **[!UICONTROL Default upload options]** area of the General Settings page. Those values are already in Experience Manager. As such, any changes that you make under **[!UICONTROL Default upload options]**, across any of the five tabs, by way of the Experience Manager user interface, are reflected in Dynamic Media, not in Dynamic Media Classic. All other settings and values in the [General Settings](/help/assets/dm-general-settings.md) page and the Publish Setup page are maintained between Dynamic Media Classic and Dynamic Media on Experience Manager.

**To configure Dynamic Media Publish Setup Image Server:**

1. In Experience Manager Author mode, select the Experience Manager logo to access the global navigation console.
1. In the left rail, click the Tools icon, then go to **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media Publish Setup]**.
1. In the Image Server page, from the drop-down list, choose your publish context to establish default settings for delivering images from Image Servers.

| Publish context | Description |
| --- | --- |
| Image Serving | Specifies the context for publish settings. |
| Test Image Serving | Specifies the context for testing publish settings.<br>For new Dynamic Media accounts only, the default **[!UICONTROL Client address]** field is set to `127.0.0.1` automatically.<br>See [Test assets before making them public](#test-assets-before-making-public). |

1. Use the five tabs to configure the default publish context settings.

   * [Security](#security-tab) tab
   * [Catalog Management](#catalog-management-tab) tab
   * [Request Attributes](#request-attributes-tab) tab
   * [Common Thumbnail Attributes](#common-thumbnail-attributes-tab) tab
   * [Color Management Attributes](#color-management-attributes-tab) tab

   ![Dynamic Media Publish Setup page](/help/assets/assets-dm/dm-publish-setup.png)
   *Dynamic Media Publish Setup page, with the **[!UICONTROL Request Attributes]** tab selected.*<br><br>

1. When you are finished, near the upper-right corner of the page, click **[!UICONTROL Save]**.

## Security tab {#security-tab}

>[!NOTE]
>
>Security settings are not supported for the *Image Serving* publish context.

When *Test Image Serving* is set as the publish context, you can set the following security setting:

**[!UICONTROL Client address]** - Lets you specify one or more IP addresses or IP address ranges. When specified, requests to this image catalog that originates from a client at an unlisted IP address is rejected. This rule applies both to delivery of images and rendered images.

   ![Security tab](/help/assets/assets-dm/dm-ipallowlist.png)<br>*The security tab showing IP "allow" field.*

## Catalog management tab {#catalog-management-tab}

**[!UICONTROL Rule set definition file path]** - Specifies the file that contains the rule set definitions for the image catalog.

See also the [RuleSetFile](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-rulesetfile) parameter in the Dynamic Media Viewers Reference Guide.

>[!NOTE]
>
>If your Dynamic Media Classic account has a **[!UICONTROL Rule set definition file path]** selected under **[!UICONTROL Setup]** > **[!UICONTROL Application]** > **[!UICONTROL Publish setup]**, Experience Manager fetches the file. Your Dynamic Media account retrieves the file from Dynamic Media Classic. The file is then stored and made available in this field, when you open the **[!UICONTROL Dynamic Media Publish Setup]** page for the first time.

## Request attributes tab {#request-attributes-tab}

These settings pertain to the default appearance of images.

| Setting | Description |
| --- | --- |
| **[!UICONTROL Reply image size limit]** | Required.<br>For new Dynamic Media accounts only, the default size limits are automatically set to Width: `3000` and Height: `3000` for both **[!UICONTROL Image Serving]** and **[!UICONTROL Test Image Serving]**.<br>Specifies the maximum reply image width and height that is returned to the client. The server returns an error if a request causes a reply image whose width, or height, or both, is larger than this setting.<br>See also the [MaxPix](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-maxpix) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Request obfuscation mode]** | Enable if you want base64 encoding applied to valid requests.<br>See also the [RequestObfuscation](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestobfuscation) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Request locking mode]** | Enable if you want a simple hash lock included in requests.<br>See also the [RequestLock](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-requestlock) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default Request Attributes]** | |
| **[!UICONTROL Default image file suffix]** | Required.<br>Default data file extension that is appended to the catalog Path and MaskPath field values if the path does not include a file suffix.<br>See also the [DefaultExt](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultext) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default font face name]** | Specifies which font is used if no font is provided by a text layer request. If specified, it must be a valid font name value in this image catalog's font map or the default catalog's font map.<br>See also the [DefaultFont](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultfont) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default image]** | A default image is returned in response to a request where the requested image is not found.<br>See also the [DefaultImage](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-defaultimage) parameter in the Dynamic Media Viewers Reference Guide.<br>**NOTE**: If your Dynamic Media Classic account has a **[!UICONTROL Default image]** selected under **[!UICONTROL Setup]** > **[!UICONTROL Application]** > **[!UICONTROL Publish setup]**, in the **[!UICONTROL Default Request Attributes]** group, Experience Manager fetches the file. The file is then stored and made available in this field when you open the **[!UICONTROL Dynamic Media Publish Setup]** page for the first time.|
| **[!UICONTROL Default image mode]** | When the slider box is enabled (slider on the right), the **[!UICONTROL Default image]** replaces each missing layer in the source image with the default image and returns the composite as usual. When the slider box is disabled (slider on the left), the default image replaces the entire composite image, even if the missing image is just one of several layers.<br>See also the [DefaultImageMode](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultimagemode) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default view size]** | Required.<br>For new Dynamic Media accounts only, the default view sizes are automatically set to Width: `1280` and Height: `1280` for both **[!UICONTROL Image Serving]** and **[!UICONTROL Test Image Serving]**.<br>The server constrains reply images to be no larger than this width and height, if the request does not specify the view size explicitly using `wid=`, `hei=`, or `scl=`.<br>See also the [DefaultPix](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultpix) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default thumbnail size]** | Required.<br>Used instead of attribute **[!UICONTROL Default view size]** for thumbnail requests (`req=tmb`). The server constrains reply images to be no larger that this width and height, if a thumbnail request (`req=tmb`) does not specify the size explicitly using `wid=`, `hei=`, or `scl=`.<br>See also the [DefaultThumbPix](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-defaultthumbpix) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default background color]** | Specifies the RGB value used to fill in any area of a reply image that does not contain actual image data.<br>See also the [BkgColor](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-bkgcolor) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL JPEG Encoding Attributes]** |  |
| **[!UICONTROL Quality]** | <br>Specifies the default attributes for JPEG reply images.<br>For new Dynamic Media accounts only, the **[!UICONTROL Quality]** default values are automatically set to `80` for both **[!UICONTROL Image Serving]** and **[!UICONTROL Test Image Serving]**.<br>This field is defined in the range of 1 - 100.<br>See also the [JpegQuality](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-jpegquality) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Chromatically downsampling]** | Enable or disable chromatically downsampling, which JPEG encoders employ. |
| **[!UICONTROL Default resampling mode]** | Specifies the default resampling and interpolation attributes to use for scaling image data. Use when `resMode` is not specified in a request.<br>For new Dynamic Media accounts only, the default resampling modes are automatically set to `Sharp2` for both **[!UICONTROL Image Serving]** and **[!UICONTROL Test Image Serving]**.<br>See also the [ResMode](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-is-cat-resmode) parameter in the Dynamic Media Viewers Reference Guide. |

## Common thumbnail attributes tab {#common-thumbnail-attributes-tab}

These settings pertain to the default appearance and alignment of thumbnail images.

| Setting | Description |
| --- | --- |
| **[!UICONTROL Default background color for thumbnail]** | Specifies the RGB value used to fill the area of an output thumbnail image that does not contain actual image data. Used only for thumbnail requests (`req=tmb`) and when **[!UICONTROL Default Thumbnail Type]** setting is set to **[!UICONTROL Fit]** or **[!UICONTROL Texture]**.<br>See also the [ThumbBkgColor](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbbkgcolor) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Horizontal alignment]** | Specifies the horizontal alignment of the thumbnail image in the reply image rectangle specified by `wid=` and `hei=` values.<br>Used only for thumbnail requests (`req=tmb`) and when **[!UICONTROL Default Thumbnail Type]** setting is set to **[!UICONTROL Fit]**.<br>There are three horizontal alignments to choose from: **[!UICONTROL Center alignment]**, **[!UICONTROL Left alignment]**, and **[!UICONTROL Right alignment]**.<br>See also the [ThumbHorizAlign](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbhorizalign) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Vertical alignment]** | Specifies the vertical alignment of the thumbnail image in the reply image rectangle specified by `wid=` and `hei=` values. Used only for thumbnail requests (`req=tmb`) and when **[!UICONTROL Default Thumbnail Type]** setting is set to **[!UICONTROL Fit]**.<br>There are three vertical alignments to choose from: **[!UICONTROL Top alignment]**, **[!UICONTROL Center alignment]**, and **[!UICONTROL Bottom alignment]**.<br>See also the [ThumbVertAlign](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbvertalign) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default cache time to live]** | A default expiration interval is given in hours in case a particular catalog record does not contain a valid catalog Expiration value. Set to `-1` to mark as never expire. <br>See also the [Expiration](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-expiration) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default thumbnail type]** | A default for the thumbnail type is given in case a particular catalog record does not contain a valid catalog ThumbType value. Used only for thumbnail requests (`req=tmb`).<br>There are three thumbnail types to choose from: **[!UICONTROL Crop]**, **[!UICONTROL Fit]**, and **[!UICONTROL Texture]**.<br>See also the [ThumbType](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbtype) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Default thumbnail resolution]** | A default for the thumbnail object resolution is given in case a particular catalog record does not contain a valid catalog ThumbRes value. Used only for thumbnail requests (`req=tmb`) and when the **[!UICONTROL Default thumbnail type]** setting is set to **[!UICONTROL Texture]**.<br>See also the [ThumbRes](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-thumbres) parameter in the Dynamic Media Viewers Reference Guide. |

## Color management attributes tab {#color-management-attributes-tab}

These settings determine which ICC color profiles are used for images.

**Color Conversion Rendering Intent**
A color conversion rendering intent permits overriding of the default rendering intent of the working profiles to determine how the source colors are adjusted. Used when:

1. One of the default ICC profiles is the target color space of a color conversion.
1. This profile characterizes an output device, such as a printer or monitor.
1. And, the specified rendering intent is valid for this profile.

Different rendering intents use different rules to determine how the source colors are adjusted.

See also the [IccRenderIntent](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccrenderintent) parameter in the Dynamic Media Viewers Reference Guide.

>[!NOTE]
>
>In general, use the default rendering intent for the selected color setting, which Adobe has tested to meet industry standards. For example, if you choose a color setting for North America or Europe, the default color conversion rendering intent is **[!UICONTROL Relative Colorimetric]**. If you choose a color setting for Japan, the default color conversion rendering intent is **[!UICONTROL Perceptual]**.

| Setting | Characteristics |
| --- | --- |
| **[!UICONTROL CMYK default color space]** | Specifies the name of the ICC color profile to use as a working profile for CMYK data. If **[!UICONTROL None Specified]** is chosen, color management is disabled for this image catalog when CMYK source images are involved. All CMYK working spaces are device-dependent, meaning that they are based on actual ink and paper combinations. The CMYK working spaces Adobe supplies are based on standard commercial print conditions.<br> See also [IccProfileCMYK](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilecmyk) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Gray-Scale default color space]** | Specifies the name of the ICC color profile to use as a working profile for gray-scale data. If **[!UICONTROL None Specified]** is chosen, color management is disabled for this image catalog when gray-scale source images are involved.<br>See also the [IccProfileGray](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilegray) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL RGB default color space]** | Specifies the name of the ICC color profile to use as a working profile for RGB data. If **[!UICONTROL None Specified]** is chosen, color management is disabled for this image catalog when RGB sources images are involved. In general, it is best to choose **[!UICONTROL Adobe RGB]** or **[!UICONTROL sRGB]**, rather than the profile for a specific device (such as a monitor profile). **[!UICONTROL sRGB]** is recommended when you prepare images for the web or mobile devices, because it defines the color space of the standard monitor used to view images on the web. **[!UICONTROL sRGB]** is also a good choice when you work with images from consumer-level digital cameras, because most of these cameras use sRGB as their default color space.<br>See also the [IccProfileRBG](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/attributes/r-iccprofilergb) parameter in the Dynamic Media Viewers Reference Guide. |
| **[!UICONTROL Color conversion rendering intent]** | **[!UICONTROL Perceptual]** &ndash; Aims to preserve the visual relationship between colors so it's perceived as natural to the human eye, even though the color values themselves may change. This intent is suitable for photographic images with lots of out-of-gamut colors. This setting is the standard rendering intent for the Japanese printing industry. |
|  | **[!UICONTROL Relative Colorimetric]** - Compares the extreme highlight of the source color space to that of the destination color space and shifts all colors accordingly. Out-of-gamut colors are shifted to the closest reproducible color in the destination color space. Relative Colorimetric preserves more of the original colors in an image than Perceptual. This setting is the standard rendering intent for printing in North America and Europe. |
|  | **[!UICONTROL Saturation]** &ndash; Tries to produce vivid colors in an image at the expense of color accuracy. This rendering intent is suitable for business graphics like graphs or charts, where bright saturated colors are more important than the exact relationship between colors. |
|  | **[!UICONTROL Absolute Colorimetric]** &ndash; Leaves colors that fall inside the destination gamut unchanged. Out-of-gamut colors are clipped. No scaling of colors to destination white point is performed. This intent aims to maintain color accuracy at the expense of preserving relationships between colors and is suitable for proofing to simulate the output of a particular device. This intent is useful for previewing how paper color affects printed colors.|

## Test assets before making them public {#test-assets-before-making-public}

Secure Testing helps you define a secure test environment and build a robust business-to-business solution, based on a configurable set of IP address and ranges. This functionality lets you match your Adobe Dynamic Media deployments with the architecture of your content management and business system.

With Secure Testing, you can preview the staging version of the website with unpublished content.

If desired, create a staging environment rather than making assets publicly available for the following reasons:

* Preview websites before public launch (staging website).
* Serve assets that require restricted access, such as eCatalogs that show prices in a B2B web application.
* Use assets behind a firewall as part of a product information management system, customer service application, training site, and so on.

>[!NOTE]
>
>Secure Testing does not affect access to Adobe Dynamic Media Classic. Adobe Dynamic Media Classic security remains consistent and requires the usual credentials for access to Adobe Dynamic Media Classic and related web services.

### How Secure Testing works {#how-test-assets-works}

Most corporations run their Internet behind a firewall. Access to the Internet is possible through certain routes and typically through a limited range of public IP addresses.

From your corporate network, you can figure out your public IP address using websites like [https://www.whatismyip.com](https://www.whatismyip.com/) or request this information from your corporate IT organization.

With Secure Testing, Adobe Dynamic Media establishes a dedicated Image Server for staging environments or internal applications. Any request to this server checks the origin IP address. If the incoming request is not within the approved list of IP addresses, a failure response is returned. The Adobe Dynamic Media Company Administrator configures the approved list of IP addresses for their company's Secure Testing environment.

Because the location of the original request must be confirmed, the traffic of the Secure Testing service is not routed through a content distribution network like public Dynamic Media Image Server traffic. Requests to the Secure Testing service have a slightly higher latency compared to the public Dynamic Media Image Servers.

Unpublished assets are immediately available from the Secure Testing services, without the need to publish. In this way, you can run a preview before assets are published to their public facing Image Server.

>[!NOTE]
>
>Secure Testing services use the Catalog Server that is configured with an internal publish context. Therefore, if your company is configured to publish to Secure Testing, any uploaded assets in Adobe Dynamic Media immediately become available on Secure Testing services. This functionality is true regardless of whether the assets are marked for publish on upload.

Secure Testing services currently support the following asset types and functionalities:

* Images.
* Vignettes (Render Server requests).
* Customers must explicitly request Render Server support, which is available.
* Sets, including image sets, eCatalog, render sets, and media sets.
* Standard Adobe Dynamic Media rich media viewers.
* Adobe Dynamic Media OnDemand JSP pages.
* Static content, such as PDF files and progressively served videos.
* HTTP video streaming.
* Progressive video streaming.

The following asset types and functionalities are currently not supported:

* Adobe Dynamic Media Classic Info or eCatalog search
* RTMP video streaming
* Web-to-print
* UGC (User-Generated Content) services

  >[!IMPORTANT]
  >
  >Starting May 1, 2023, UGC assets in Dynamic Media are available for use up to 60 days from the date of upload. After 60 days, the assets are removed.

  >[!NOTE]
  >
  >Support for new or existing UGC vector image assets in Adobe Dynamic Media ended on September 30, 2021.

### Test the Secure Testing service {#test-secure-testing-service}

To ensure that the Secure Testing service works as expected, do the following:

#### Prepare your account

1. Contact Adobe Customer Care and request that they enable Secure Testing on your account.
1. In Adobe Experience Manager, select **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media Publish Setup]**.
1. On the Image Server page, in the **[!UICONTROL Publish Context]** drop-down list, select **[!UICONTROL Test Image Serving]**.
1. Select the **[!UICONTROL Security]** tab.
1. For the **[!UICONTROL Client address]** filter, select **[!UICONTROL Add]**.
1. In the **[!UICONTROL IP Address]** field, type an IP address.
1. In the **[!UICONTROL Mask]** field, type a net mask.

   >[!NOTE]
   >
   >If you add more than one IP address and net mask, it effectively permits *all* IP addresses to make asset calls, and they all show up.

1. Do one of the following:

   * To add more IP addresses, repeat the previous three steps.
   * Continue to the next step.

1. In the upper right corner of the Image Server page, select **[!UICONTROL Save]**.
1. Upload the desired images to your Adobe Dynamic Media account.

<!--    See [Upload files](uploading-files.md#uploading_files). -->

1. Make sure some of the images are marked for publish and others are unmarked, and then submit the publish job.

<!--    See [Publish files](publishing-files.md#publishing_files). -->

1. Determine the name of your Secure Testing service by going to **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media General Setting]**.
1. On the **[!UICONTROL Server]** page, find the server name to the right of **[!UICONTROL Published Server Name]**.

Contact Adobe Care if the server name is missing or the URL to the server does not work.

#### Prepare website variations

You need two variations of a website that links the published and unpublished assets:

* Public version - Link assets using your traditional Adobe Dynamic Media URL syntax.
* Staging version - Link assets using the same syntax but with the Secure Testing site name.

#### Run the tests

Perform the following tests:

1. Check whether assets are visible from within your corporate network.

   From within the corporate network identified by the previously defined IP address range, the staging version of the website displays all images, whether marked for publish or not. As such, you can test without accidentally making images available before preview approval or product launch.

   Confirm that the public version of your site shows published assets as previously experienced with Adobe Dynamic Media.

1. From outside your corporate network, verify that nonpublished assets (that is, unmarked for publish) are protected from third-party access.

   Access your network from outside (such as from your home computer, or over a 4G/5G connection), then verify that the public version of the site shows all published assets but none of the unpublished content.

   Confirm that the staging version does not show any asset because you are accessing the Secure Testing service from an unapproved IP address.
