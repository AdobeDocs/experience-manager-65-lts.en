---
title: Deploying and Maintaining
description: Learn how to get started with the AEM installation.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 4a2ada26-b859-4a32-9ab0-2d4c2b695245
---
# Deploying and Maintaining{#deploying-and-maintaining}

In this page you find:

- [Deploying and Maintaining{#deploying-and-maintaining}](#deploying-and-maintainingdeploying-and-maintaining)
  - [Basic Concepts {#basic-concepts}](#basic-concepts-basic-concepts)
    - [What is AEM? {#what-is-aem}](#what-is-aem-what-is-aem)
    - [Typical Deployment Scenarios {#typical-deployment-scenarios}](#typical-deployment-scenarios-typical-deployment-scenarios)
    - [On-premise {#on-premise}](#on-premise-on-premise)
    - [Managed Services using Cloud Manager {#managed-services-using-cloud-manager}](#managed-services-using-cloud-manager-managed-services-using-cloud-manager)
  - [Getting Started {#getting-started}](#getting-started-getting-started)
    - [Prerequisites {#prerequisites}](#prerequisites-prerequisites)
    - [Getting the Software {#getting-the-software}](#getting-the-software-getting-the-software)
    - [Default Local Install {#default-local-install}](#default-local-install-default-local-install)
    - [Author and Publish Installs {#author-and-publish-installs}](#author-and-publish-installs-author-and-publish-installs)
    - [Unpacked Install Directory {#unpacked-install-directory}](#unpacked-install-directory-unpacked-install-directory)
    - [Starting and Stopping {#starting-and-stopping}](#starting-and-stopping-starting-and-stopping)

<!-- Once you have familiarized yourself with these basics, you can find in more advanced and detailed information in the following subpages:

* [Technical Requirements](/help/sites-deploying/technical-requirements.md)
* [Recommended Deployments](/help/sites-deploying/recommended-deploys.md)
* [Custom Standalone Install](/help/sites-deploying/custom-standalone-install.md)
* [Application Server Install](/help/sites-deploying/application-server-install.md)
* [Command Line Start and Stop](/help/sites-deploying/command-line-start-and-stop.md)
* [Configuring](/help/sites-deploying/configuring.md)
* [Upgrading to AEM 6.5](/help/sites-deploying/upgrade.md)
* [Configuration How-To Articles](/help/sites-deploying/ht-deploy.md)
* [Web Console](/help/sites-deploying/web-console.md)
* [Troubleshooting Replication](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Introduction to the AEM Platform](/help/sites-deploying/platform.md)
* [Performance Guidelines](/help/sites-deploying/performance-guidelines.md) -->

## Basic Concepts {#basic-concepts}

### What is AEM? {#what-is-aem}

Adobe Experience Manager is a web-based client-server system for building, managing, and deploying commercial websites and related services. It combines several infrastructure-level and application-level functions into a single integrated package.

At the infrastructure level AEM provides the following:

* **Web Application Server**: AEM can be deployed in standalone mode (it includes an integrated Jetty web server) or as a web application within a third-party application server.
* **Web Application Framework**: AEM incorporates the Sling Web Application Framework that simplifies the writing of RESTful, content-oriented web applications.
* **Content Repository**: AEM includes a Java&trade; Content Repository (JCR), a type of hierarchical database designed specifically for unstructured and semi-structured data. The repository stores not only the user-facing content but also all code, templates, and internal data used by the application.

Building on this base, AEM also offers several application-level features for the management of:

* **Websites**
* **Digital Publications**
* **Forms & Documents**
* **Digital Assets**

Finally, customers can use these infrastructure and application-level building blocks to create customized solutions by building applications of their own.

The AEM server is **Java-based** and runs on most operating systems that support that platform. All client interaction with AEM is done through a **web browser**.

>[!NOTE]
>
>The Adaptive Forms feature, available in AEM 6.5 LTS QuickStart, is designed for exploration and evaluation purposes only. For production use, it is essential to obtain a valid license for AEM Forms, as Adaptive Forms functionality requires proper licensing.

### Typical Deployment Scenarios {#typical-deployment-scenarios}

In AEM terminology, an "instance" is a copy of AEM running on a server. AEM installations usually involve at least two instances, typically running on separate computers:

* **Author**: An AEM instance used to create, upload, and edit content and to administer the website. Once content is ready to go live, it is replicated to the publish instance.
* **Publish**: An AEM instance that serves the published content to the public.

These instances are identical in terms of installed software. They are differentiated by configuration only. In addition, most installations use a Dispatcher:

* **Dispatcher**: A static web server (Apache httpd, Microsoft&reg; IIS, and so on) augmented with the AEM Dispatcher module. It caches web pages produced by the publish instance to improve performance.

There are many advanced options and elaborations of this setup, but the basic pattern of author, publish and Dispatcher is at the core of most deployments. Let's begin by focusing on a simple setup. Discussions of advanced deployment options follow.

The following sections describe both the scenarios:

* **On-premise**: AEM deployed and managed in your corporate environment.

* **Managed Services - Cloud Manager for Adobe Experience Manager**: AEM deployed and managed by Adobe Managed Services.

### On-premise {#on-premise}

You can install AEM on servers in your Corporate environment. Typical installation instances include: Development, Testing, and Publishing environments. See [Getting Started](#getting-started) for basic details on how to get the AEM software to install it locally.

<!-- To learn more about the typical on-premises deployments, see [Recommended Deployments](/help/sites-deploying/recommended-deploys.md). -->

### Managed Services using Cloud Manager {#managed-services-using-cloud-manager}
<i>To be announced soon.</i>

## Getting Started {#getting-started}

### Prerequisites {#prerequisites}

While production instances are run on dedicated machines running an officially supported OS (see [Technical Requirements](/help/sites-deploying/technical-requirements.md)), the Experience Manager server will actually run on any system that supports [**Java&trade; Standard Edition 17**](https://www.oracle.com/java/technologies/downloads/#java17a).

For purposes of familiarization and for developing on AEM, it is common to use an instance installed on your local machine running Apple OS X or desktop versions of Microsoft&reg; Windows or Linux&reg;.

On the client-side, AEM works with all modern browsers (**Microsoft&reg; Edge**,  **Chrome** 51+, **Firefox** 47+, **Safari** 8+) on both desktop and tablet operating systems. See [Supported Client Platforms](/help/sites-deploying/technical-requirements.md#supported-client-platforms) for details.

### Getting the Software {#getting-the-software}

Customers with a valid maintenance and support contract should have received a mail notification with a code and be able to download AEM from the [**Adobe Licensing Website**](https://licensing.adobe.com/). Business partners can request download access from [**spphelp@adobe.com**](mailto:spphelp@adobe.com).

The AEM software package is available in two forms:

* **CQ AEM 6.5 LTS jar:** A standalone executable *jar* file that includes everything that you need to get running.

* **CQ AEM 6.5 LTS war:** A *war* file for deployment in a third-party application server.

In the following section we describe the **standalone installation**. For details on installing AEM in an application server see [Application Server Install](/help/sites-deploying/application-server-install.md).

### Default Local Install {#default-local-install}

1. Create an install directory on your local machine. For example:

   UNIX&reg; install location: **/opt/aem**

   Windows install location: **`C:\Program Files\aem`**

   Equally, it is common to install sample instances in a folder right on the desktop. In any case, Adobe refers to this location generically as:

   `<aem-install>`

   *The path of the file directory must consist of only US ASCII characters.*

1. Place the **jar** and **license** files in this directory:

   ```shell
   <aem-install>/
       <aem-65-lts>.jar
       license.properties
   ```

   If you do not provide a `license.properties` file, AEM redirects your browser to a **Welcome** screen on startup, where you can enter a license key. You need to request a valid license key from Adobe if you do not yet have one.

1. To start up the instance in a GUI environment, double-click the **`<aem-65-lts>.jar`** file.

   Alternative, you can launch AEM from the command line:

   ```shell
       java -Xmx1024M -jar <aem-65-lts>.jar
   ```

AEM takes a few minutes to unpack the jar file, install itself, and start up. The above procedure results in:

* an **AEM author** instance
* running on **localhost**
* on port **4502**

To access the instance, point your browser to:

**`https://localhost:4502`**

The result in author instance will be automatically configured to connect to a **publish instance** on **`localhost:4503`**.

### Author and Publish Installs {#author-and-publish-installs}

The default install (an **author** instance on **`localhost:4502`**) can be changed simply by renaming the `jar` file before launching it for the first time. The naming pattern is:

**`cq-<instance-type>-p<port-number>.jar`**

For example, renaming the file to

**`cq-author-p4502.jar`**

And launching it, results in an author instance running on **`localhost:4502`**.

Similarly, renaming and launching the file

**`cq-publish-p4503.jar`**

Results in a publish instance running on **`localhost:4503`**.

You would install these two instances in, for example

`<aem-install>/author`and

**`<aem-install>/publish`**

For more details on customizing your installation see the following:

* [Custom Standalone Install](/help/sites-deploying/custom-standalone-install.md)
<!-- * [Run Modes](/help/sites-deploying/configure-runmodes.md) -->

### Unpacked Install Directory {#unpacked-install-directory}

When the quickstart jar is launched for the first time, it unpacks itself into the same directory under a new subdirectory called `crx-quickstart`. You should have the following:

```xml
<aem-install>/
    license.properties
    <aem-65-lts>.jar
    crx-quickstart/
        app/
        bin/
        conf/
        launchpad/
        logs/
        metrics/
        monitoring/
        opt/
        repository/
        threaddumps/
        eula-de_DE.html
        eula-en_US.html
        eula-fr_FR.html
        eula-ja_JP.html
        readme.txt
```

If the instance was installed from the UI, a browser window opens automatically, and a desktop application window also opens displaying the host and port of the instance and an on/off switch:

![start up screen](assets/screen_shot_.png)

>[!NOTE]
>
>If you are using symlinks, have a look at [issues with symlink](https://helpx.adobe.com/experience-manager/kb/changing-symlink.html).

### Starting and Stopping {#starting-and-stopping}

Once AEM has unpacked itself and started up for the first time, double-clicking the jar file in the install directory simply starts the instance, it does not reinstall it.

To stop the instance from the GUI, click the **on/off** switch on the desktop application window.

You can also stop and start AEM from the command line. Assuming you have already installed the instance for the first time, the **command-line scripts** are here:

**`<aem-install>/crx-quickstart/bin/`**

This folder contains the following UNIX&reg; bash shell scripts:

* **`start`**: Starts the instance
* `stop`: Stops the instance
* **`status`**: Reports the Status of the instance
* **`quickstart`**: Used to configure start information, if necessary.

There are also equivalent **`bat`** files for Windows. For more detailed information, see:

* [Command Line Start and Stop](/help/sites-deploying/command-line-start-and-stop.md)

AEM starts and automatically redirects your web browser to the appropriate page, usually the login page; for example:

`https://localhost:4502/`

![sign in screen](assets/screen_shot_2019-04-08at83533am.png)
<!-- 
After you are logged in, you have access to AEM. For more information, depending on your role, see the following:

* [Authoring](/help/sites-authoring/first-steps.md)
* [Administering](/help/sites-administering/home.md)
* [Developing](/help/sites-developing/getting-started.md)
* [Managing](/help/managing/best-practices.md) -->

<!-- ## Advanced Deployment {#advanced-deployment}

The above section should give you a good understanding of the basics of AEM installation. However, installing a full production system of AEM can involve considerably more complexity. For full coverage of advanced installation see the following subpages:

* [Technical Requirements](/help/sites-deploying/technical-requirements.md)
* [Recommended Deployments](/help/sites-deploying/recommended-deploys.md)
* [Custom Standalone Install](/help/sites-deploying/custom-standalone-install.md)
* [Application Server Install](/help/sites-deploying/application-server-install.md)
* [Command Line Start and Stop](/help/sites-deploying/command-line-start-and-stop.md)
* [Configuring](/help/sites-deploying/configuring.md)
* [Upgrading to AEM 6.5](/help/sites-deploying/upgrade.md)
* [Configuration How-To Articles](/help/sites-deploying/ht-deploy.md)
* [Web Console](/help/sites-deploying/web-console.md)
* [Troubleshooting Replication](/help/sites-deploying/troubleshoot-rep.md)
* [Best Practices](/help/sites-deploying/best-practices.md)
* [Introduction to the AEM Platform](/help/sites-deploying/platform.md)
* [Performance Guidelines](/help/sites-deploying/performance-guidelines.md) -->
