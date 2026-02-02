---
title: Installing and configuring Designer
description: Designer is available as a stand-alone installer and is also bundled with Workbench. Learn how to install a stand-alone Designer.
role: Admin, User, Developer
feature: Forms Designer,Designer
solution: Experience Manager, Experience Manager Forms
exl-id: 526bbc59-62c3-4e6d-a938-e368d07fe6b0
---
# Installing and configuring Designer{#installing-and-configuring-designer}

## Pre-requisites {#pre-requisites}

+++ For 64-bit AEM Forms Designer (Recommended)

* Install a 64-bit version of  [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Ensure that the previously mentioned redistributable runtime packages are installed before starting the installation.
* A user with administrator rights to install or uninstall AEM Forms Designer.

+++

+++ For 32-bit AEM Forms Designer

* Install a 32-bit version of  [Visual C++ 2019 Redistributable (x64)](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Ensure that the previously mentioned redistributable runtime packages are installed before starting the installation.
* A user with administrator rights to install or uninstall AEM Forms Designer.

+++

>[!NOTE]
>
>* The 64-bit version of the Designer was introduced with AEM 6.5 Forms Service Pack 19 (6.5.19.0).
>* The 32-bit version of the Designer is deprecated since the release of [AEM Forms Service Pack 21 (6.5.21.0)](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
> * The supported platforms for Forms Designer align with the AEM Forms supported platforms. To learn about the supported platforms for Forms Designer, [click here](/help/sites-deploying/technical-requirements.md)

For more information regarding installation of Forms Designer, Visit [Frequently asked questions](#fandq).

## Install AEM Forms Designer {#install-designer}

Designer is available as a stand-alone installer and is also bundled with WorkBench. If you are using a stand-alone installer for AEM Forms Designer, perform the following steps:

1. Uninstall the previous version of AEM Forms Designer, if it is already installed.
1. Download 64-bit AEM Forms Designer (recommended) or 32-bit AEM Forms Designer based on your requirements.

   >[!NOTE]
   > 
   >* 32-bit Forms Designer is scheduled to deprecate with AEM 6.5 Forms Service Packs 20 (6.5.20.0) release. Adobe recommends that you upgrade to 64-bit Forms Designer.
   >* 64-bit Forms Designer is available only for AEM 6.5 Forms Service Packs 19 (6.5.19.0) or later releases.
   >* Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) onwards Forms Designer version also includes the Service Pack version. For example, for Service Pack 15 the version number is 6.5.15.20221112.1.0. In this example, 6.5.15 is the Service Pack version.

1. Launch the AEM Forms Designer installer by double-clicking setup.exe.
1. Proceed and provide your details and the serial number on the Personalization screen.

   >[!NOTE]
   >
   >* Obtain your Forms Designer license key from the [Adobe Licensing Website](https://licensing.adobe.com/).

1. If you accept the license agreement, click Next to proceed.
1. (Optional) change the default installation path, if you want to install Designer at a location of your choice. Click Next.
1. Click Back to change any preferences. To install Designer, click Install.
1. Click Finish when the installation completes.

Alternatively, you can install the AEM Forms Designer through the command line using passive or silent mode.

* Passive command-line install: The installer displays a progress bar that indicates that the installation is in progress but no prompts or error messages are displayed. Once launched, you cannot cancel the installation.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Silent command-line install: The installer runs the installation without displaying a user interface. No prompts, messages, or dialog boxes are displayed. Once launched, you cannot cancel the installation.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```

## Update AEM Forms Designer {#update-forms-designer}

There are two cases while updating the latest version of AEM Forms Designer 6.5.16.0:

* **Case 1**: When the user has AEM Forms Designer version earlier than 6.5.15.0.
* **Case 2**: When the user has 6.5.15.0 AEM Forms Designer version.

+++**When the user has AEM Forms Designer version earlier than 6.5.15.0.**

   If you are using a stand-alone installer for AEM Forms Designer, perform the following steps:

   1. Before installing **AEM Forms Designer 6.5.16.0**, users must uninstall any previous versions.
   1. Download and install [AEM Forms Designer 6.5.15.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) from the AEM Form Releases Page.
   1. After successful installation of **AEM Forms Designer 6.5.15.0**, download and install [AEM Forms Designer 6.5.16.0](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) by double-clicking on the downloaded installer file .

   +++

+++**When the user has 6.5.15.0 AEM Forms Designer version**

   If you are using a stand-alone installer for AEM Forms Designer, perform the following steps:

   1. Download the latest version of AEM Forms Designer from the [Software Distribution Portal](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#).
   1. Install the latest version of AEM Forms Designer by double-clicking on the downloaded installer file.

+++

## Frequently asked questions {#fandq}

* **Can a user directly upgrade or install 64-bit Designer?**
   * Yes, users can directly upgrade or install 64-bit Designer. To upgrade, install the [SP19](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) Designer full installer and apply the subsequent Designer patch release over it.

      >[!NOTE]
      > Before you upgrade to 64-bit Designer, first uninstall 32-bit Designer if it exists.

* **Can users keep both 32-bit and 64-bit installed on their system?**
   * No. A 32-bit and 64-bit installation does not work on the same computer. User can either have a 32-bit Designer or a 64-bit Designer.

* **How do you check if a user is on 64-bit Designer or 32-bit Designer?**
   * There are two ways to check the Forms Designer version:

      1. Open Designer. 
      1. Click **Help** > **About Designer** to view the Designer version and bitness information.
      For example, the version string ends with **64-bit**, as seen in the following example:
      `6.5.21.20240522.1.161 | 64 bit`
      1. Open Designer, On the upper left you see a branding icon that contains 64-bit information with the product name.
