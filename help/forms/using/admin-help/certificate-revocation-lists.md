---
title: Managing certificate revocation lists
description: Learn how to manage certificate revocation lists. You can import, edit, and delete certificate revocation lists (CRLs) using Trust Store Management.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: a5e49cc8-cd46-47e6-8ff3-655dcf23296a
---
# Managing certificate revocation lists{#managing-certificate-revocationlists}

>[!NOTE]
> 
> Ensure that the user has admin privileges to access the administrator console.

Using Trust Store Management, you can import, edit, and delete certificate revocation lists (CRLs). Base64 and DER-encoded certificate revocation lists are supported.

## Import a CRL {#import-a-crl}

1. In the administration console, click Settings &gt;Trust Store Management &gt; Certificate Revocation Lists, and then click Import.
1. In the Alias box, type an identifier for the CRL.
1. Click Browse to locate the CRL and then click OK.

## Export a CRL {#export-a-crl}

1. In the administration console, click Settings &gt;Trust Store Management &gt; Certificate Revocation Lists.
1. Click the alias name of the CRL so you can export, and then click Export.
1. Follow the directions so you can export the CRL. CRLs are exported in Base64 encoding.
1. Click OK.

## Delete a CRL {#delete-a-crl}

1. In the administration console, click Settings &gt;Trust Store Management &gt; Certificate Revocation Lists.
1. Select the check boxes for the CRLs to delete, click Delete, and then click OK.
