---
title: Certificate types used by Acrobat Reader DC Extensions
description: Learn about the certificate types used by Acrobat Reader DC Extensions.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: ca919915-c37b-4793-b5e2-21a464c5dcdf
---
# Certificate types used by Acrobat Reader DC Extensions {#certificate-types-used-by-acrobat-reader-dc-extensions}

The Certificate Viewer provides the following information about the certificate:

* Certificate "friendly" name
* Certificate profiles
* Validity period
* Acrobat Reader DC Extensions usage rights

## Certificate "friendly" name {#certificate-friendly-name}

The "friendly" name of a Acrobat Reader DC Extensions certificate is a string that describes the properties of the certificate, as in the following example:

ARE 2D Barcode Full Production V6.1 P8 0002054

The string contains the following elements:

**Certificate type:** Describes the AEM forms modules that the certificate activates, and the level of activation, such as ARE 2D Barcode Full. For a list of the certificate types available, see the Type column in the table in the Certificate profiles section.

**Deployment type:** Indicates the intended use of the certificate, such as Production. The value can be Evaluation or Production. For a list of deployment types associated with each certificate type, see the Deployment type column in the table in the Certificate profiles section.

**Usage rights version:** Describes the version of the usage rights algorithm that the certificate can be used for, such as V6.1. This version does not signify the version of Acrobat or Acrobat Reader DC Extensions.

**Profile code:** The profile code is a shorthand description of complete certificate properties, such as example, P8. For a list of the profile codes associated with each file type, see the Profile code column in the table in the Certificate Profiles section.

**Serial number:** A serial number is assigned to each certificate issued by Adobe, such as 0002054. Adobe Enterprise Support or an Adobe Enterprise account representative can use this serial number to trace the certificate to a specific product order or to an OEM relationship.

## Certificate profiles {#certificate-profiles}

The following table lists the certificate profiles that you can encounter when analyzing Acrobat Reader DC Extensions certificates.

<table>
 <thead>
  <tr>
   <th><p>Profile code</p></th>
   <th><p>Type</p></th>
   <th><p>Validity period</p></th>
   <th><p>Deployment type</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>P1</p></td>
   <td><p>SAP Production</p></td>
   <td><p>Max</p></td>
   <td><p>Production</p></td>
  </tr>
  <tr>
   <td><p>P2</p></td>
   <td><p>SAP Internal Test</p></td>
   <td><p>2 years</p></td>
   <td><p>Evaluation and test</p></td>
  </tr>
  <tr>
   <td><p>P3</p></td>
   <td><p>Acrobat Reader DC Extensions, Production</p></td>
   <td><p>Max</p></td>
   <td><p>Production</p></td>
  </tr>
  <tr>
   <td><p>P4</p></td>
   <td><p>Acrobat Reader DC Extensions, Internal Adobe Usage</p></td>
   <td><p>2 years</p></td>
   <td><p>Production</p></td>
  </tr>
  <tr>
   <td><p>P5</p></td>
   <td><p>Acrobat Reader DC Extensions, Partner Integration</p></td>
   <td><p>2 years</p></td>
   <td><p>Evaluation and test</p></td>
  </tr>
  <tr>
   <td><p>P6</p></td>
   <td><p>Acrobat Reader DC Extensions, Evaluation</p></td>
   <td><p>60 days</p></td>
   <td><p>Evaluation</p></td>
  </tr>
  <tr>
   <td><p>P8</p></td>
   <td><p>Forms, Production</p></td>
   <td><p>Max</p></td>
   <td><p>Production</p></td>
  </tr>
  <tr>
   <td><p>P9</p></td>
   <td><p>Adobe Acrobat 7.x, Production</p></td>
   <td><p>Max</p></td>
   <td><p>Production</p></td>
  </tr>
  <tr>
   <td><p>I10</p></td>
   <td><p>Forms; OEMs may use Forms</p></td>
   <td><p>Max</p></td>
   <td><p>Production and evaluation</p></td>
  </tr>
  <tr>
   <td><p>I11</p></td>
   <td><p>Forms; OEMs may use Forms.</p></td>
   <td><p>Max</p></td>
   <td><p>Production and evaluation</p></td>
  </tr>
  <tr>
   <td><p>I12</p></td>
   <td><p>Signature only; OEMs may use signature only</p></td>
   <td><p>Max</p></td>
   <td><p>Production and evaluation</p></td>
  </tr>
  <tr>
   <td><p>I13</p></td>
   <td><p>Offline Commenting only; OEMs may use offline commenting</p></td>
   <td><p>Max</p></td>
   <td><p>Production and evaluation</p></td>
  </tr>
  <tr>
   <td><p>I14</p></td>
   <td><p>Commenting only; OEMs may use commenting only</p></td>
   <td><p>Max</p></td>
   <td><p>Production and evaluation</p></td>
  </tr>
  <tr>
   <td><p>I15</p></td>
   <td><p>Full permissions; OEMs may use full permissions</p></td>
   <td><p>Max</p></td>
   <td><p>Production and evaluation</p></td>
  </tr>
 </tbody>
</table>

## Validity period {#validity-period}

Evaluation certificates are issued to customers and developers so that they can evaluate and develop sample applications for products. The validity period of these certificates is between 60 and 90 days. They expire at the end of the second month following the issue data.

Partner Integration certificates are issued to Adobe business partners to support software development, integration, prototyping, and demonstration. These certificates are valid for two years from the date of issue.

Adobe Internal Use Certificates are used within Adobe to support software development, integration, prototyping and demonstration. These certificates are valid for two years from the date of issue.

Production certificates are issued to customers who purchased Acrobat Reader DC Extensions. These certificates are valid for the maximum period permitted by the certificate authority (CA), shown as *Max* in the Certificate Profiles table.

## Acrobat Reader DC Extensions usage rights {#acrobat-reader-dc-extensions-usage-rights}

When you examine the Acrobat Reader DC Extensions certificate in the Certificate Viewer, you can select the usage rights item from the Details tab (if configured). You can see an itemized list of the Adobe Reader usage rights that the certificate can enable. The usage rights enabled on a particular document may be a subset of those rights enabled by the certificate.

If online commenting is required in a non-collaborative environment, contact Adobe Support for more information. The Mode property matches the deployment type and is either *production* or *evaluation*.

The permitted Acrobat Reader DC Extensions usage rights consist of one or more specific elements. These elements are used in different combinations to achieve varieties of licensed product functionality.

<table>
 <thead>
  <tr>
   <th><p>Usage rights element</p></th>
   <th><p>Capability enabled in Adobe Reader when viewing a rights-enabled PDF document</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>FormFillInAndSave</p></td>
   <td><p>Fill in the form fields and save the files locally.</p></td>
  </tr>
  <tr>
   <td><p>FormImportExport</p></td>
   <td><p>Import and export form data as FDF, XFDF, XML, and XDP files.</p></td>
  </tr>
  <tr>
   <td><p>FormAddDelete</p></td>
   <td><p>Add, change, or delete fields and field properties on the PDF form.</p></td>
  </tr>
  <tr>
   <td><p>SubmitStandalone</p></td>
   <td><p>Submit data, by email or offline, to a server when it is not running in a browser session.</p></td>
  </tr>
  <tr>
   <td><p>SpawnTemplate</p></td>
   <td><p>Create pages from template pages within the same PDF form.</p></td>
  </tr>
  <tr>
   <td><p>Signing</p></td>
   <td><p>Digitally sign and save PDF documents, and clear digital signatures.</p></td>
  </tr>
  <tr>
   <td><p>AnnotModify</p></td>
   <td><p>Create and modify document annotations such as comments.</p></td>
  </tr>
  <tr>
   <td><p>AnnotImportExport</p></td>
   <td><p>Save annotations such as comments in a separate data file and load comments from a file.</p></td>
  </tr>
  <tr>
   <td><p>BarcodePlaintext</p></td>
   <td><p>Print a document with form data barcoded in an unencrypted form that does not require licensed server software to decode.</p></td>
  </tr>
  <tr>
   <td><p>AnnotOnline</p></td>
   <td><p>Upload and download annotations such as comments to and from an online document review and comment server.</p></td>
  </tr>
  <tr>
   <td><p>FormOnline</p></td>
   <td><p>Connect to web services or databases that are defined within a PDF form.</p></td>
  </tr>
  <tr>
   <td><p>EFModif</p></td>
   <td><p>Modify embedded file objects associated with the PDF document.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Acrobat Reader DC Extensions usage rights can be licensed from Adobe only in certain combinations that work together. It is not possible to license these capabilities independently. For information about the available combinations of usage rights, contact an AEM forms account representative.
