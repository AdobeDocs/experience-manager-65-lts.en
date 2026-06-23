---
title: Mitigating VULN-36128 and VULN-36120 Vulnerabilities for AEM Forms on JEE 6.5 LTS SP2
description: Mitigation steps for VULN-36128 and VULN-36120 on AEM Forms on JEE 6.5 LTS Service Pack 2 deployments running on JBoss.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
solution: Experience Manager, Experience Manager Forms
feature: Security
role: Admin
exl-id: 7c4a9e12-3b8f-4d6a-9f1e-2a5c8d7e6b04
---
# Mitigating VULN-36128 and VULN-36120 Vulnerabilities for AEM Forms on JEE 6.5 LTS SP2

## Quick Reference {#quick-reference}

| Impact Level | Affected Versions | Recommended Action |
| --- | --- | --- |
| Critical | AEM Forms on JEE 6.5 LTS Service Pack 2 (6.5 LTS SP2) | Manually install the [hotfix]() |
| Not Affected | AEM Forms on OSGi, Workbench, Cloud Service | No action required |

**Vulnerabilities Addressed:**

* **VULN-36128**: Remote code execution vulnerability allowing unauthorized remote attackers to execute arbitrary code. 
* **VULN-36120**: Improper input validation vulnerability that could allow unauthorized access to sensitive information.

## Mitigation Steps {#mitigation-steps}

### Before You Start {#before-you-start}

Before making any changes, back up the EAR file you are about to replace:

* Locate `adobe-edcserver-jboss.ear` in your deployment directory:

  ```text
  [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
  ```

* Copy the file to a secure backup location outside the deployment directory.
* Ensure the backup is complete and accessible before proceeding with any updates.

This precaution allows you to restore the original state if you encounter any issues during the update process.

### Manual Hotfix Installation for AEM Forms on JEE 6.5 LTS SP2 (JBoss) {#manual-hotfix-installation-aem-forms-jee-65-lts-sp2-jboss}

1. Download `adobe-edcserver-jboss.ear` from the [Adobe Software Distribution Portal]().

1. Locate `adobe-edcserver-jboss.ear` in your deployment directory and replace it with the downloaded file:

   ```text
   [AEM installation directory]/deploy/adobe-edcserver-jboss.ear
   ```

1. Launch the AEM Forms Configuration Manager to re-deploy the updated EAR and fully apply the patch.

1. Restart the application server and confirm successful deployment from the server logs.

## References {#references}

* [Adobe Experience Manager Forms Security Best Practices](/help/forms/using/hardening-securing-aem-forms-environment.md)
