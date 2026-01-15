---
title: Release Notes for [!DNL Adobe Experience Manager] 6.5 LTS SP1
description: Find release information, what's new, install how-tos, and a detailed change list for [!DNL Adobe Experience Manager] 6.5 LTS SP1
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
---

# Adobe Experience Manager (AEM) Forms 6.5 LTS SP1 on JEE Release Notes


## Release Information

| **Product**          | Adobe Experience Manager Forms       |
| -------------------- | ------------------------------------ |
| **Version**          | 6.5 LTS SP1                          |
| **Type**             | Long-Term Support Service Pack (JEE) |
| **Release Category** | Upgrade Release                      |
| **Download URL**     | Software Distribution                |

## What is included in [!DNL Experience Manager] 6.5 LTS SP1 {#what-is-included-in-aem-65ltssp1}

Adobe Experience Manager (AEM) Forms **6.5 LTS SP1 on JEE**  delivers  new features, key customer-requested platform updates, and general bug fixes, with a strong focus on product stability and long-term support.

## What Is Included in AEM Forms 6.5 LTS SP1

### 1. Java Support Updates

Support for newer Java versions has been introduced:

* **Java&trade; 17**
* **Java&trade; 21**

### 2. Application Server Support Updates

#### JBoss EAP 8 Support

* Support for **JBoss EAP 8** has been added.
* The legacy **PicketBox** security framework has been removed.
* **Elytron-based credential stores** are now supported for secure credential management.

##### Configuration: Credential Store (Elytron-based)

AEM Forms on JBoss EAP 8 uses Elytron for managing secure credentials. Customers must configure an Elytron-based Credential Store to ensure successful server startup and secure database authentication.

For configuration details, refer to the installation and configuration guide.

### 3. Platform and Compatibility Changes

#### Servlet Specification Support

* Support for **Servlet Specification 5+**
* Based on **Jakarta EE 9** compliance

#### Namespace Migration Requirement

* Jakarta EE 9 introduces a namespace change from `javax.*` to `jakarta.*`
* All **custom DSCs** must be migrated to the `jakarta.*` namespace
* AEM Forms 6.5 LTS SP1 supports **only Jakarta EE 9+–based application servers**

For more information, see **Migration from javax to jakarta Namespace**.

## Upgrade

For detailed upgrade instructions, see the **Upgrade Guide for AEM Forms 6.5 LTS SP1 on JEE**.

## Installation

For installation steps and prerequisites, refer to the **Installation Guide for AEM Forms 6.5 LTS SP1 (JEE)**.

## Supported Platforms

For the complete list of supported platforms, operating systems, databases, and application servers, see the:

**Supported Platforms Matrix – AEM Forms 6.5 LTS SP1 (JEE)**

## Deprecated and Removed Features

* Support for **RDBMK** for CRX repository persistence has been removed.
* For clustered environments, **only MongoMK** is supported for repository persistence.

## Migration from javax to jakarta Namespace

Starting with **AEM Forms 6.5 LTS SP1**, only application servers implementing the **Jakarta Servlet API** are supported. Customers must migrate all custom code, including DSCs and integrations, from the `javax.*` namespace to `jakarta.*`.
