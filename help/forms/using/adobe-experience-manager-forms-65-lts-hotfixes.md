---
title: Adobe Experience Manager Forms 6.5 LTS Hotfixes
description: Provides information on how to download and install a hotfix for AEM Forms 6.5 LTS. For AEM 6.5 (non-LTS), see the AEM 6.5 Forms hotfixes article.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: e485100f-3e16-4fd4-a8ce-af771d765dd1
---
# Adobe Experience Manager Forms 6.5 LTS Hotfixes{#aem-form-hotfix}

This article lists the critical fixes implemented to address known issues, improve system stability, and enhance overall performance of AEM Forms 6.5 LTS.   


This article applies to AEM Forms 6.5 LTS. For AEM 6.5 (non-LTS) deployments, see [Adobe Experience Manager Forms Hotfixes](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/aem-forms-hotfix).

>[!NOTE]
>
> The hotfixes are designed to be cumulative, encompassing all preceding fixes. When you apply the latest hotfix to a release, it not only addresses the most recent issue but also incorporates all prior bug fixes and enhancements.

## Hotfixes for AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Date</strong></td>
    <td><strong>Hotfix download link (AEM Software Distribution link)</strong></td>
    <td><strong>Fixed issues</strong></td>
  </tr>
  <tr>
    <td>
      <strong>Sep 21, 2026</strong><br>
      <em>Applies to:</em> AEM Forms 6.5 LTS Service Pack 2 JEE deployments (JBoss, WebLogic, WebSphere)<br>
    </td>
    <td>
    <p><strong>To install this hotfix, complete these steps in order:</strong></p>
    <p><strong>Step 1: Install the patch</strong></p>
    <ul>
    <strong>JBoss:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-jboss.zip">Hotfix for AEM Forms 6.5 LTS SP2 on Windows for JBoss JEE server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/jboss/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-jboss.tar.gz">Hotfix for AEM Forms 6.5 LTS SP2 on Linux for JBoss JEE server</a></li>
    <strong>WebLogic:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-weblogic.zip">Hotfix for AEM Forms 6.5 LTS SP2 on Windows for Weblogic JEE server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/weblogic/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-weblogic.tar.gz">Hotfix for AEM Forms 6.5 LTS SP2 on Linux for Weblogic JEE server</a></li>
    <strong>WebSphere:</strong>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-win-websphere.zip">Hotfix for AEM Forms 6.5 LTS SP2 on Windows for Websphere JEE server</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/websphere/adobe-aem-forms-jee-hotfix-6.5.LTS.2-linux-websphere.tar.gz">Hotfix for AEM Forms 6.5 LTS SP2 on Linux for Websphere JEE server</a></li>
    </ul>
    <p>Install the patch using the standard AEM Forms on JEE patch installation procedure. <!-- TODO: link to the 6.5 LTS JEE patch installation instructions once available --></p>
    <p><strong>Step 2: Install the vulnerability fix bundle</strong></p>
    <ul>
    <li><a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-lts-sp2-hotfix/SP2LTSBundles_VULN-36670.zip">Vulnerability fix bundle for AEM Forms 6.5 LTS SP2</a></li>
    </ul>
    <ol>
    <li>Open the OSGi console at <code>http://&lt;host&gt;:&lt;port&gt;/lc/system/console/bundles</code>.</li>
    <li>Click <strong>Install/Update</strong>.</li>
    <li>Select the <strong>Start Bundle</strong> and <strong>Refresh Packages</strong> checkboxes.</li>
    <li>Click <strong>Choose File</strong>, and then upload the downloaded bundle.</li>
    <li>Wait until the log settles and the bundle shows as <strong>Active</strong>.</li>
    </ol>
    <p><strong>Step 3: Update the AEM Forms Workbench installer</strong></p>
    <p>You must update to the latest AEM Forms Workbench installer. Download it from <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/fd/workbench/6-5-0-20260902-1-45/Workbench_DVD.zip">AEM Forms Workbench installer</a>.</p>
    <p><strong>Step 4: Update client library files (developers)</strong></p>
    <p>This patch includes a major update to the SDK client library <code>adobe-livecycle-client.jar</code> (see <a href="/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files">Including AEM Forms Java library files</a>). If your project uses this JAR file, update <code>adobe-livecycle-client.jar</code> in your project's classpath after you install the hotfix. The latest version is available at <code>&lt;AEM_Forms_Installation_dir&gt;\sdk\client-libs\common\adobe-livecycle-client.jar</code>.</p>
    <p>The hotfix is cumulative, so you can apply it on AEM Forms 6.5 LTS Service Pack 2 or an earlier Service Pack without installing Service Pack 2 first.</p>
    </td>
    <td>
    <ul>
    <li><b>FORMS-26818</b> After Apache Shiro is updated to version 2.1.0, AEM Forms on JEE fails to bootstrap with a <code>NoClassDefFoundError</code> for the Shiro security manager. This hotfix restores successful bootstrapping.</li>
    <li><b>FORMS-26819</b> AEM Forms on JEE fails with a "no class found" error for <code>org.owasp.esapi.reference.JavaLogFactory</code>. This hotfix resolves the missing class.</li>
    <li><b>FORMS-26584, FORMS-26589</b> After upgrading to AEM Forms 6.5 LTS, TaskManager endpoints are removed. This hotfix restores the TaskManager endpoints.</li>
    <li><b>FORMS-26569</b> On JEE, the Configuration Manager MergeEars step fails with a DOCTYPE declaration error (<code>ALC-LCM-010-200</code>) because of the secure XML builder. This hotfix lets the MergeEars step complete.</li>
    <li><b>FORMS-25063</b> Application-level logs are missing on IBM WebSphere Liberty deployments. This hotfix restores application-level logging.</li>
    <li><b>FORMS-24892</b> On JBoss, email fails with "IMAPProvider not a subtype." This hotfix restores email functionality on JBoss.</li>
    <li><b>FORMS-24692</b> On WebSphere Liberty Profile (WLP), email fails with "Could not convert socket to TLS." This hotfix restores email over TLS on WLP.</li>
    <li><b>FORMS-26688</b> Updates the Gibson library to version 6.0.29665850.</li>
    <li><b>FORMS-25222</b> Backports SAML assertion validation improvements.</li>
    <li><b>FORMS-26733, FORMS-26734</b> Updated Apache Log4j to version 2.25.5.</li>
    <li>This hotfix also includes security fixes.</li>
    </ul>
    <p><strong>Build:</strong> AEMForms-6.6.0-0008</p>
    </td>
  </tr>
  <tr>
    <td>
      <strong>Sept 09, 2025</strong><br>
    <td>
    <ul>
    <li>Windows- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip">Hotfix2 for AEM Service Pack 6.5 LTS on Windows</a></li>
    <li>Linux- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip">Hotfix2 for AEM Service Pack 6.5 LTS on Linux</a></li>
     <li>MacOS- <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[…]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip">Hotfix2 for AEM Service Pack 6.5 LTS on MacOS</a></li>
    <td>
    <ul>
    <li>Enhanced form submission reliability by addressing an issue where submissions may fail when Server-Side Validation (SSV) was enabled If you encounter any issues, contact [Adobe Experience Manager Forms Support](https://business.adobe.com/in/support/main.html)
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>

## Download and install an OSGi Hotfix {#download-install-hotfix}

Perform the following steps to download and install the Hotfix:

  1. Download [Hotfix](#hotfix-for-adaptive-forms) from the Software Distribution link.
  1. Extract the Hotfix archive file so you can obtain an Experience Manager package (.zip) and bundle (.jar) files.
  1. Upload and install the package (.zip) via the [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
  1. Open the configuration manager bundles `https://server:host/system/console/bundles`, upload, and install the bundle (.jar). The hotfix is installed.
