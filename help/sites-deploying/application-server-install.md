---
title: Application Server Install
description: Learn how to install Adobe Experience Manager with an application server.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 09d54b52-485a-453c-a2d0-535adead9e6c
---
# Application Server Install{#application-server-install}

>[!NOTE]
>
>`JAR` and `WAR` are the file types Adobe Experience Manager (AEM) is released in. These formats are undergoing quality assurance to accommodate the support levels Adobe has committed to.
>

This section tells you how to install Adobe Experience Manager (AEM) with an application server. Consult the [Supported Platforms](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) section to read about the specific support levels provided for the individual application servers.

The installation steps of the following Application Servers are described:

* [WebSphere&reg; 24.0.0.7](#websphere)
* [Tomcat 10.0.x/10.1.x](#tomcat)

Consult the appropriate application server documentation for more information on installing web applications, server configurations and how to start and stop the server.

<!-- >[!NOTE]
>
>If you are using Dynamic Media in a WAR deployment, see [Dynamic Media documentation](/help/assets/config-dynamic.md#enabling-dynamic-media). -->

## General Description {#general-description}

### Default behavior when installing AEM in an Application Server {#default-behaviour-when-installing-aem-in-an-application-server}

AEM comes as a single war file to deploy.

If deployed, the following happens by default:

* The run mode is `author`
* The instance (Repository, Felix OSGI environment, bundles, and so on) is installed in is `${user.dir}/crx-quickstart`, where `${user.dir}` is the current working directory. This path to crx-quickstart is called `sling.home`

* The context root is the war file name. For example, `aem-65-lts`.

#### Configuration {#configuration}

You can change the default behavior in the following way:

* run mode : configure the `sling.run.modes` parameter in the `WEB-INF/web.xml` file of the AEM war file before deployment

* sling.home: configure the `sling.home` parameter in the `WEB-INF/web.xml` file of the AEM war file before deployment

* context root: rename the AEM war file

#### Publish installation {#publish-installation}

To get a publish instance deployed, you need to set the run mode to publish:

* Unpack the `WEB-INF/web.xml` from the AEM war file
* Change `sling.run.modes` parameter to publish
* Repack `web.xml` file into the AEM war file
* Deploy AEM war file

#### Installation check {#installation-check}

To check if everything is installed, you can:

* tail the `error.log`file to see that all content is installed
* look in `/system/console` that all bundles are installed

#### Two Instances on the same Application Server {#two-instances-on-the-same-application-server}

For demonstration purposes, it can be appropriate to install both author and publish instance in one application server. In order achieve that, you need to:

1. Change `sling.home` variable and `sling.run.modes` variables of the publish instance
1. Unpack the `WEB-INF/web.xml` file from the AEM war file
1. Change the `sling.home` parameter to a different path (absolute and relative paths are possible)
1. Change `sling.run.modes` to `publish` for the publish instance
1. Repack the `web.xml` file
1. Rename the war files, so they have different names. For example, rename one to `aemauthor.war` and the other to `aempublish.war`
1. Use higher memory settings. For example, default AEM instances use `-Xmx3072m`
1. Deploy the two web applications
1. After Deployment stop the two web applications
1. In both author and publish instances make sure that in the `sling.properties` file the property `felix.service.urlhandlers` is set to `false`. (The default is that it is set to `true`).
1. Start the two web applications again.

## Application Servers Installation Procedures {#application-servers-installation-procedures}

### WebSphere&reg; 24.0.0.7 {#websphere}

Before the deployment, please read the [General Description](#general-description) above.

**Server Preparation**

* Let Basic Auth Headers pass through:

  * One way to let AEM authenticate a user is to disable the global administrative security of the WebSphere&reg; server. In order to do that, go to **Security > Global Security** and uncheck the **Enable administrative security checkbox**, save, and restart the server.

* Set `"JAVA_OPTS= -Xmx2048m"`
* If you want to install AEM using context root = /, change the context root of the existing Default web application.

**Deploy the AEM Web Application**

* Download the AEM war file
* Make your configurations in the `web.xml` file if needed. For more info, see [General Description](#general-description) above.

  * Unpack the `WEB-INF/web.xml` file
  * Change the `sling.run.modes` parameter to `publish`
  * Uncomment initial `sling.home` parameter and set this path as you need
  * Repack the `web.xml` file.

* Deploy the AEM war file

  * Choose a context root. If you want to set the sling run modes you need to select the detailed steps of the deploy wizard, then specify it in step 6 of the wizard.

* Startthe AEM web application

#### Tomcat 10.0.x/10.1.x {#tomcat}

Before a deployment read the [General Description](#general-description) above.

* **Prepare Tomcat Server**

  * Increase VM memory settings:

    * In `bin/catalina.bat` (resp `catalina.sh` on UNIX&reg;) add the following setting:
      
      ```
      set "JAVA_OPTS= -Xmx2048m`
      ```

  * Tomcat does not enable admin or manager access at installation. Therefore, you have to manually edit `tomcat-users.xml` to allow access for these accounts:

    * Edit `tomcat-users.xml` to include access for admin and manager. The configuration should look similar to the following example:

      ```xml
      <?xml version='1.0' encoding='utf-8'?>
      <tomcat-users>
      role rolename="manager"/>
      role rolename="tomcat"/>
      <role rolename="admin"/>
      <role rolename="role1"/>
      <role rolename="manager-gui"/>
      <user username="both" password="tomcat" roles="tomcat,role1"/>
      <user username="tomcat" password="tomcat" roles="tomcat"/>
      <user username="admin" password="admin" roles="admin,manager-gui"/>
      <user username="role1" password="tomcat" roles="role1"/>
      </tomcat-users>
      ```

  * If you like to deploy AEM with context root "/", then you have to change context root of the existing ROOT webapp:

    * Stop and undeploy the ROOT webapp
    * Rename the `ROOT.war` folder in Tomcat's webapps folder
    * Start the webapp again

  * If you install the AEM web application using the manager-gui, then you need to increase the maximal size of an uploaded file, as the default only allows 50MB upload size. In order to achieven that open the `web.xml` of the manager web application:

      `webapps/manager/WEB-INF/web.xml`

      and increase the `max-file-size` and `max-request-size` to at least 500MB. See see the following `multipart-config` in an example `web.xml` file below:

      ```xml
      <multipart-config>
      <!-- 500MB max -->
      <max-file-size>524288000</max-file-size>
      <max-request-size>524288000</max-request-size>
      <file-size-threshold>0</file-size-threshold>
      </multipart-config>
      ```

* **Deploy the AEM web application**

  * Download the AEM war file.
  * Make your configurations in the `web.xml` file if needed.

    * Unpack the `WEB-INF/web.xml` file
    * Change the `sling.run.modes` parameter to `publish`
    * Uncomment  the initial `sling.home` parameter and set this path as you need
    * Repack the `web.xml` file.

  * Rename the AEM war file to `ROOT.war` if you want to deploy it as root webapp. Rename it to `aemauthor.war` if you want to have `aemauthor` as context root.
  * Copy it into Tomcat's webapps folder
  * Wait until AEM is installed.
