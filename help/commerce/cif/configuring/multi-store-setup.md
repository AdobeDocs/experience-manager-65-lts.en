---
title: Commerce Multi-Store Setup
description: Learn how to map multiple store views from Adobe Commerce to AEM. This allows projects to support multi-tenant and multi-lingual use cases.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
solution: Experience Manager,Commerce
role: Admin, Developer
exl-id: 3a5d10d2-4ef8-4f85-942e-47ece6538acb
---
# Commerce Multi-Store Setup {#multi-store}

The AEM CIF Core Components can be used on multiple AEM site structures and the underlying GraphQL client implementation can connect to different Adobe Commerce stores / store views. This allows projects to implement complex multi-store / multi-site setups.

A video walkthrough detailing options for integrating multiple Adobe Commerce Store Views with Adobe Experience Manager Sites. 

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

AEM Multi-Site Management features of Live Copy and Language Copy are used with the Commerce Integration Framework to globally manage sites across regions and locales.

The recommended setup is to use a 1:1 relationship between the AEM site and the Adobe Commerce store view.

To connect an AEM site and AEM CIF Core Components so too to a dedicated store view, follow the steps below:

## Configuration {#configuration}

1. Configure multiple stores & store views according to the pattern described in [Adobe Commerce Websites, Stores & Views](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)

2. Make sure the connection between AEM & Adobe Commerce is working.

3. Create a child configuration of the CIF Cloud Service config following these steps:

   * In AEM go to Tools > General > [Configuration Browser](/help/sites-administering/configurations.md#using-configuration-browser)
   * Select the base configuration that you created
   * Create a configuration using the steps described at point 2 above

   This new configuration is created as a child configuration of the base one. You can now go to Tools > General > Configuration Browser and create the configuration settings.

   >[!TIP]
   >
   >Commerce catalogs can be addressed by using IDs or UIDs. UIDs got introduced in Adobe Commerce 2.4.2. Only enable this if your commerce backend supports a GraphQL schema of version 2.4.2 or later.

4. Assign the child configuration to an AEM site

   * Go to the AEM Sites console
   * Navigate to the region or language root of your site structure, for example,  /content/venia/us _or_ /content/venia/us/en for the Venia sample page
   * Select the page and open the page properties
   * Select the Advanced tab
   * In the `Configuration` section, select the configuration that you created at step

## Additional Resources

* [Adobe Commerce Websites, Stores & Views](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)
* [AEM CIF Core Components - Multi store / site configuration](https://github.com/adobe/aem-core-cif-components#multi-store--site-configuration)
* [Using Multi-Site Manager](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Reusing Content: Multi Site Manager and Live Copy](/help/sites-administering/msm.md)
