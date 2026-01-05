---
title: Adobe Experience Manager Forms 6.5 LTS SP1 Hotfixes 
description: Provides information on how to download and install a hotfix for AEM Forms 6.5 LTS. 
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
---

# Adobe Experience Manager Forms 6.5 LTS Hotfixes{#aem-form-hotfix}

This article lists the critical fixes implemented to address known issues, improve system stability, and enhance overall performance of AEM Forms 6.5 LTS. 

>[!NOTE]
>
> The hotfixes are designed to be cumulative, encompassing all preceding fixes. When you apply the latest hotfix to a release, it not only addresses the most recent issue but also incorporates all prior bug fixes and enhancements.

## Hotfixes for AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Date</strong></td>
    <td><strong>Hotfix download link (AEM Software Distribution link)</strong></td>
    <td><strong>Fixed issues</strong></td>
  </tr>
  <tr>
    <td>
      <strong>Sept 09, 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Hotfix2 for AEM Service Pack 6.5 LTS on Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 for AEM Service Pack 6.5 LTS on Linux</a></li>
     <li>MacOS- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">Hotfix2 for AEM Service Pack 6.5 LTS on MacOS</a></li>
    <td>
    <ul>
    <li>Enhanced form submission reliability by addressing an issue where submissions may fail when Server-Side Validation (SSV) was enabled If you encounter any issues, contact [Adobe Experience Manager Forms Support](https://business.adobe.com/in/support/main.html)
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Download and install an OSGi Hotfix {#download-install-hotfix}

Perform the following steps to download and install the Hotfix:

  1. Download [Hotfix](#hotfix-for-adaptive-forms) from the Software Distribution link.
  1. Extract the Hotfix archive file so you can obtain an Experience Manager package (.zip) and bundle (.jar) files.
  1. Upload and install the package (.zip) via the [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
  1. Open the configuration manager bundles `https://server:host/system/console/bundles`, upload, and install the bundle (.jar). The hotfix is installed. 
