---
title: Compatibility Package
description: Installing the Compatibility package on AEM Forms 6.5 LTS lets you use the Correspondence Management assets from AEM Forms 6.5 and earlier versions and deprecated adaptive forms templates and pages
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 3a529a82-e2fd-423c-96c1-a5accc87775e
---
# Compatibility Package{#compatibility-package}

## Overview {#overview}

Interactive communication is the default and recommended approach to create customer communications in AEM Forms 6.5 LTS. To continue using letters in AEM Forms 6.5 LTS, you need to install the latest [AEMFD Compatibility package](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

The AEMFD Compatibility package also lets you [use the following assets from AEM Forms 6.5.22.0, 6.4, 6.3 and 6.2 on AEM Forms 6.5 LTS](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Document Fragments
* Letters
* Data Dictionaries
* Adaptive forms deprecated templates and pages

For more information, see [Assets made compatible with AEM Forms 6.5 by installing the Compatibility package](../../forms/using/compatibility-package.md#assetsmadecompatible).

## Add support for AEM Forms 6.5, 6.4, 6.3 and 6.2 assets in AEM Forms 6.5 LTS {#add-support-for-aem-forms-and-assets-in-aem-forms-6.5.lts}

After performing an upgrade, do the following to install the AEMFD compatibility package and make your assets compatible with 6.5:

Ensure that you have [AEM Compatibility package](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) pre-installed.

1. Install the latest AEM 6.5 LTS [Compatibility package](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

   For more information on uploading and installing the package, see [How to work with packages](/help/sites-administering/package-manager.md).

1. After the logs are stabilized, restart the server.
1. Use the migration utility for making your assets compatible with 6.5 LTS.

    >[!NOTE]
    >
    > It is recommended to use the `Ctrl + C` command to restart the SDK. Restarting the AEM SDK using alternative methods, for example, stopping Java processes, may lead to inconsistencies in the AEM development environment.

   For more information, see [migration utility](../../forms/using/migration-utility.md).

## Assets made compatible with AEM Forms 6.5 LTS by installing the Compatibility package {#assetsmadecompatible}

By installing the Compatibility package, you can make the following assets and templates compatible with AEM Forms 6.5 LTS:

* Correspondence Management Assets from AEM 6.4 and earlier:

    * [Letters](../../forms/using/create-letter.md)
    * [Data Dictionaries](/help/forms/using/data-dictionary.md)
    * Document Fragments

* Adaptive form deprecated templates:

    * /libs/fd/af/templates/blankTemplate2
    * /libs/fd/af/templates/simpleEnrollmentTemplate
    * /libs/fd/af/templates/simpleEnrollmentTemplate2
    * /libs/fd/af/templates/surveyTemplate
    * /libs/fd/af/templates/surveyTemplate2
    * /libs/fd/af/templates/tabbedEnrollmentTemplate
    * /libs/fd/af/templates/tabbedEnrollmentTemplate2
    * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
    * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Adaptive forms deprecated pages:

    * /libs/fd/af/components/page/survey
    * /libs/fd/af/components/page/tabbedenrollment
    * /libs/fd/afaddon/components/page/advancedenrollment
