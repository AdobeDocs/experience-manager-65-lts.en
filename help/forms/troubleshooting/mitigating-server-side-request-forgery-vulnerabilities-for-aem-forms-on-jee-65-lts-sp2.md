---
title: Mitigating Server-Side Request Forgery (SSRF) Vulnerabilities for AEM Forms on JEE 6.5 LTS SP2
description: Mitigation steps for Server-Side Request Forgery (SSRF) vulnerabilities on AEM Forms on JEE 6.5 LTS Service Pack 2 deployments running on JBoss.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
product_v2:
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
---
# Mitigating Server-Side Request Forgery (SSRF) Vulnerabilities for AEM Forms on JEE 6.5 LTS SP2

## Quick Reference {#quick-reference}

| Impact Level | Affected Versions | Recommended Action |
| --- | --- | --- |
| Critical | AEM Forms on JEE 6.5 LTS Service Pack 2 (6.5 LTS SP2) | Manually install the [hotfix](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear) |
| Not Affected | AEM Forms on OSGi, Workbench, Cloud Service | No action required |

**Vulnerabilities Addressed:**

* Server-Side Request Forgery (SSRF) (CWE-918)

## Overview {#overview}

### What's Affected {#whats-affected}

| Vulnerability | Impact | Affected Components |
| --- | --- | --- |
| Server-Side Request Forgery (SSRF) (CWE-918) | Attackers may induce the server to make unintended requests to internal or external resources | AEM Forms on JEE 6.5 LTS SP2 |

### What's Not Affected {#whats-not-affected}

* Experience Manager Forms Workbench (all versions)
* Experience Manager Forms on OSGi (all versions)
* Experience Manager Forms as a Cloud Service

## Resolution Options {#resolution-options}

### Before You Start {#before-you-start}

Before making any changes, take a backup of the EAR file you are about to replace:

* Locate `adobe-edcserver-jboss.ear` in your deployment directory:

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Copy the file to a secure backup location outside the deployment directory.
* Ensure the backup is complete and accessible before proceeding with any updates.

This precaution allows you to restore the original state in case you encounter any issues during the update process.

### Manual Hotfix Installation for AEM Forms on JEE 6.5 LTS SP2 (JBoss) 

1. Download `adobe-edcserver-jboss.ear` from the [Adobe Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-edcserver-jboss.ear).

1. Locate `adobe-edcserver-jboss.ear` in your deployment directory and replace it with the downloaded file:

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Launch the AEM Forms Configuration Manager to re-deploy the updated EAR and apply the hotfix.

1. Restart the application server and confirm successful deployment from the server logs.

## Reference {#references}

* [Adobe Experience Manager Forms Security Best Practices](/help/forms/using/hardening-securing-aem-forms-environment.md) 
