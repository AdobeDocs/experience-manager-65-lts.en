---
title: Recognizing valid and expired certificates in PDF documents
description: Learn how to recognize valid and expired certificates in PDF documents.
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
exl-id: f7402f0d-7c19-4a56-8630-208faa197f94
---
# Recognizing valid and expired certificates in PDF documents {#recognizing-valid-and-expired-certificates-in-pdf-documents}

When a PDF document that has usage rights applied by Reader Extensions is opened in Adobe Reader, a status bar appears that describes the specific usage rights enabled in the PDF document.

When the digital certificate that specifies the usage rights for a PDF document expires and the PDF document is opened in Adobe Reader, a dialog box advises the user that the PDF document has usage rights, but these rights are disabled. Although the message indicates that the PDF document was altered or tampered with, this is not necessarily the case. Adobe Reader displays this message when a certificate expires or a document is modified. In Adobe Reader 7.0.x or later, you cannot determine which case is currently the issue.

After you close the dialog box, Adobe Reader opens the PDF document. The usage rights that were applied using Acrobat Reader DC extensions are not available, as expected. If the PDF document is an interactive form, the form fields are locked and the user cannot change the form data.
