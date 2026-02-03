---
title: Unable to Start JBoss Domain Controller 
description: In AEM Forms 6.5.1 LTS cluster deployments using JBoss EAP 8, the configuration file may contain duplicate tag.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
---

# Unable to Start JBoss Domain Controller 

## Issue

In **AEM Forms 6.5.1 LTS** cluster deployments using **JBoss EAP 8**, the configuration file
`<JBOSS_HOME>/domain/configuration/domain_oracle.xml` (and database-specific variants) may contain a **duplicate opening `<security>` tag**.

This causes an **invalid XML configuration**, resulting in **JBoss Domain Controller startup failure** and preventing successful cluster initialization.

## Applies To

* **Product:** AEM Forms 6.5.1 LTS
* **Deployment Type:** Cluster
* **Application Server:** JBoss EAP 8.x
* **Configuration Files:**

  * `<JBOSS_HOME>/domain/configuration/domain_oracle.xml`
  * `<JBOSS_HOME>/domain/configuration/domain_mysql.xml`
  * `<JBOSS_HOME>/domain/configuration/domain_mssql.xml`

## Troubleshooting Steps

1. During Domain Controller startup, the following errors may be observed:

   * `WFLYCTL0198: Unexpected element 'security'`
   * `IJ010061: Unexpected element: security`

2. Open the relevant configuration file:

   ```
   <JBOSS_HOME>/domain/configuration/domain_oracle.xml
   (or domain_mysql.xml / domain_mssql.xml)
   ```

3. Locate the duplicate `<security>` opening tag.

   **Incorrect configuration:**

   ```xml
   <security>
       <security>
           <user-name>adobe</user-name>
           <credential-reference store="db-creds" alias="EncryptDBPassword"/>
       </security>
   ```

4. Remove the extra opening `<security>` tag so that the configuration is corrected as shown below:

   **Correct configuration:**

   ```xml
   <security>
       <user-name>adobe</user-name>
       <credential-reference store="db-creds" alias="EncryptDBPassword"/>
   </security>
   ```

5. Save the file and start the JBoss Domain Controller.

6. Ensure the same validated configuration is applied consistently across all cluster nodes.
