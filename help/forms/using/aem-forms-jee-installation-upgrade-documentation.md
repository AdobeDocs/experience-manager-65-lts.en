---
title: Installation and upgrade workflow for AEM Forms on JEE
description: Installation and upgrade workflow for AEM Forms 6.5 LTS on JEE (JBoss), with a consolidated list of relevant PDFs and their purpose.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms on JEE,Installation,Upgrade
exl-id: 6d8c0e24-7f08-4e66-bb12-2cf1cfe1d5d3
---

# Installation and upgrade workflow for AEM Forms on JEE {#aem-forms-jee-installation-upgrade-documentation}

## Applies to {#applies-to}

This documentation applies to **AEM 6.5 LTS Forms**.

Use the following workflow and tables to pick the correct guide(s) for your scenario. Some documents are published as PDFs; additional documents may be added over time as they become available.

## Installation and upgrade workflow {#installation-upgrade-workflow}

1. Review [Supported platforms for AEM Forms on JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) and ensure your system meets the required software/hardware combinations.
2. Decide whether you are performing a **fresh installation** or an **upgrade**.
3. For your chosen path, follow the sequence described below (some scenarios require more than one guide).

## Pre-installation and pre-upgrade steps {#start-here}

| Guide | Description |
| --- | --- |
| [Supported platforms for AEM Forms on JEE](/help/forms/using/aem-forms-jee-supported-platforms.md) | Lists supported software and hardware combinations for AEM Forms on JEE. Use this to validate prerequisites before you begin an installation or upgrade. |
| [Architecture and deployment topologies for AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md) | Explains recommended architectures and deployment topologies so you can choose an approach that matches your environment (for example, single server vs. cluster). |
| [Choosing a persistence type for an AEM Forms installation](/help/forms/using/choosing-persistence-type-for-aem-forms.md) | Helps you select an appropriate persistence type for your installation topology before you begin. |

## How do I install Adobe Experience Manager Forms (AEM Forms) on JEE on JBoss? {#installing-aem-forms-jee-jboss}

### Turnkey {#install-jee-jboss-turnkey}

| Guide | Description |
| --- | --- |
| [Installing and Deploying AEM Forms 6.5 LTS on JEE Using JBoss Turnkey (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-turnkey.pdf) | Use for a **fresh turnkey installation** on JBoss. This document provides instructions for installing and deploying AEM Forms on JEE using the JBoss turnkey distribution. |

### Single server (non-turnkey) {#install-jee-jboss-single-server}

| Guide | Description |
| --- | --- |
| [Preparing to Install AEM Forms (Single Server) (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-install-single-server.pdf) | Use **before** a **fresh single-server (non-turnkey) installation**. This document lists prerequisites and environment preparation steps for installing AEM Forms on JEE in a single-server topology. |
| [Installing and Deploying AEM Forms on JEE for JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-jboss.pdf) | Use for the **step-by-step installation and deployment** of AEM Forms on JEE on JBoss (**non-turnkey**). For single-server installations, follow this guide **after** completing *Preparing to Install AEM Forms (Single Server)*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **fresh cluster installation**. Describes prerequisites and environment preparation steps for installing AEM Forms on JEE in a server cluster topology. *(Link will be added once the PDF is available.)* |
| [Configuring AEM Forms on JEE on JBoss Cluster (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/cluster-jboss.pdf) | Use when setting up and configuring a **JBoss cluster topology** for AEM Forms on JEE. |
-->
## How do I upgrade Adobe Experience Manager Forms (AEM Forms) on JEE on JBoss? {#upgrading-aem-forms-jee-jboss}

### Turnkey {#upgrade-jee-jboss-turnkey}

| Guide | Description |
| --- | --- |
| [Upgrading to AEM Forms 6.5 LTS on JEE for JBoss Turnkey (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-turnkey.pdf) | Use for a **turnkey upgrade**. This document provides instructions for upgrading an existing AEM Forms on JEE JBoss turnkey installation. |

### Single server {#upgrade-jee-jboss-single-server}

| Guide | Description |
| --- | --- |
| [Preparing to upgrade AEM Forms (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-upgrade.pdf) | Use **before** a **single-server upgrade**. Describes how to prepare the environment before upgrading to AEM 6.5 LTS Forms. It applies to environments running AEM Forms on JEE in a single-server installation mode. |
| [Upgrading to AEM Forms on JEE for JBoss (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-jboss.pdf) | Use for the **step-by-step upgrade procedure** on JBoss in a **single-server** installation mode. Follow this guide **after** completing *Preparing to upgrade AEM Forms*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **cluster upgrade**. Describes how to prepare the environment for a server cluster before upgrading to AEM 6.5 LTS Forms. It applies to environments running AEM Forms on JEE in a server cluster installation mode. *(Link will be added once the PDF is available.)* |
| Upgrading to AEM Forms on JEE for JBoss (Cluster) (PDF) (**TBD**) | Use for the **step-by-step upgrade procedure** on JBoss in a **clustered** installation mode. Follow this guide **after** completing *Preparing to Install AEM Forms (Server Cluster)*. *(Link will be added once the PDF is available.)* | -->

