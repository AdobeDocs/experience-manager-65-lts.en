
# Major Changes & Updates 

## Java 17 Support 
* AEM Forms has been upgraded to support Java 17. 
* The foundation layer, which includes open-source components from Apache Sling, Apache Felix, and Apache Jackrabbit Oak, has also been updated for Java 17 compatibility. 

## Enhanced Servlet API Support 
* AEM 6.5.2025 JAR packaging now supports Jakarta Servlet API specifications 5. 
* WAR packaging can now be deployed to servlet containers that implement Jakarta Servlet API specifications 5 and 6. 

## Changes to AEM Uber-Jar Packaging 
* The  packaging  of  the  AEM  6.5.2025  Uber-Jar  has  been updated.  (Refer  to  the  Changes  in  Uber  Jar  Packaging  for details.)

## Removal of Legacy Features & Artifacts 
As part of modernization efforts, the following legacy features and artifacts have been removed in the 6.5.2025 update. (Refer  list of removed bundles for details).
    * Removed  Legacy  Solutions:  Social,  Commerce,  Screens, We-Retail, Integration of Search and Promote 
    * Removed  Artifacts:  crx-explorer,  crx2oak  (removed  from opt/tools), Google Guava, Abdera-Parser, JDOM (org.apache.servicemix.bundles.jdom), com.github.jknack.handlebars 

## Upgrade Compatibility

You can upgrade to AEM 6.5 Forms Update 2025 (6.5.2025 release) from any of the last six service packs.

### Upgrade Process

Perform the steps provided below in listed order to upgrade to AEM 6.5 Forms 2025 release. 
 
#### Pre-Requisites & Considerations 
 
Before starting the upgrade process, ensure the following: 
1. Take  a  Complete  Backup:  Back  up  your  AEM  repository, file  system,  and  datastore  to  prevent  data  loss  in  case  of issues.  Follow  the  official  AEM  Backup  and Restore  Guide for detailed steps. 
1. RDBMK  Support:  RDBMK  is  not  supported  for  AEM  6.5 Forms 2025 release. 
1. Test in a Non-Production  Environment: Use the beta release software in a test environment to identify 
potential issues.  
1. Review Custom Code & Integrations: Ensure your custom code,  workflows,  and  integrations  are  compatible  with 
AEM  6.5  Forms  2025  release.  Check  for  deprecated  or removed APIs and features that might affect functionality. 
1. Download Latest  version:  Download  the  latest  version  of AEM  6.5.2025  QuickStart  (.jar,  .war),  AEM  Analyzer,  S3 Connector, and (AEM Forms only) AEM Forms Add-on (Linux, Windows, macOS) from software distribution.

Privileges:  Ensure  that  you  login  with  a  user  to  install software on your operating system and also have privileges to use AEM package manager.

#### In-place upgrade process

1. Run AEM Analyzer: Before upgrading, use the AEM Analyzer (AEM Pattern Detector)  to identify potential compatibility issues. Follow these steps on the server where the AEM Forms instance is running and needs to be upgraded:

    Download and install the tool
    1. Download the latest version the tool from software distribution.
    1. Open AEM Package Manager
    1. Upload and install and the AEM Analyzer package.

    Generate the report
    1. Go to the URL: http://<aem- host>:<port>/apps/aem66- analyzer/content/modernizer/analyzer.html 
    1. Click Generate Report. Once the report is generated, run Content Transformer:
    
    Run Content Transformer
    1. Go to the URL: Go to http://<aem- host>:<port>/apps/ct/operations/content/content- transformation/content-transformer.html
    1. Use the delete operation to delete the paths, if required.

1.	Run Consistency Check: Perform a consistency check to verify system integrity. (Refer to [developer notes]() for details.)
1. Stop your AEM Instance.
1. Download and install Java 17: Download and install Java 17 on your operating system. Ensure that JAVA_HOME is correctly set after installation. After installation, check the Java version to confirm successful setup. Refer to the official Java documentation for Operating System-specific installation steps.
1. Update S3 Connector (Only for S3DS Datastore Users): This step is required only if your datastore type is S3DS. Refer to developer notes to confirm your datastore type.
1. Open the command prompt or terminal.
1. Remove the below S3 connector folders from your folder:
    * [path_of_AEM_Forms_Author_instance]/crx- quickstart/install/1
    * [path_of_AEM_Forms_Author_instance]/crx- quickstart/install/15
1.	Download the latest S3 Connector (version 1.60.2) from software distribution.
1.	Extract the downloaded ZIP file.
1.	Copy the following folders to crx-quickstart/install:
    * Copy `com.adobe.granite.oak.s3connector- 1.60.2/jcr_root/libs/system/install/1 to crx- quickstart/install/1`
    * Copy `com.adobe.granite.oak.s3connector- 1.60.2/jcr_root/libs/system/install/15 to crx- quickstart/install/15`
1. Update sling.properties file: Modify your sling.properties file. The following properties are changed from 6.5 to 6.5.2025 release:

    | AEM 6.5 | AEM 6.5.2025 |
    |---------|-------------|
    | `felix.jpms.java.sql=,javax.sql;versi on\="0.0.0.9_JavaSE";uses\:\=" javax.transaction.xa",javax.transa ction.xa;version\="1.1.0"` | `felix.jpms.java.sql=,java.sql;version\=" 0.0.0.9_JavaSE",javax.sql; version\="0.0.0.9_JavaSE";uses\:\="ja vax.transaction.xa",javax. transaction.xa;version\="1.1.0"` |
    | `granite.product.version=0.0.0.0_ 0_0_6_5_` |  |
    | `org.osgi.framework.bootdelegat ion = com.yourkit.*, ,jdk.internal. reflect` | `org.osgi.framework.bootdelegation = com.yourkit.*, ,jdk.internal.reflect, jdk.internal.reflect.*,sun.*,com.sun.*,weblogic.xml.*, redirected, redirected,com.ibm.xml.*` |
    | `org.apache.sling.feature.unpack.exten sions=system-fonts;dir\:\="${sling. home}/fonts_system";key\:\=Font- Archive-Version;value\:\=1;index\:\ =Font-Archive-Contents,user- fonts;dir\:\="${sling.home}/fonts_user "; default\:\=true;key\:\=Font- Archive- Version;value\:\=1;index\:\=Font- Archive-Contents,product- fonts;dir\:\="${sling.home}/fonts";key \:\=Font- Archive- Version;value\:\=1;index\:\=Font- Archive-Contents` |  |
    | `org.osgi.framework.system.packa ges=org.osgi.framework; version\="1.9",org.osgi.framewor k.dto;version\="1.8";uses\:\="org . osgi.dto",org.osgi.framework.hoo ks.bundle;version\="1.1";uses\:\= " org.osgi.framework",org.osgi.fra mework.hooks.resolver;version\= " 1.0";uses\:\="org.osgi.framework .wiring",org.osgi.framework.hook s. service;version\="1.1";uses\:\="o rg.osgi.framework",org.osgi. framework.hooks.weaving;versio n\="1.1";uses\:\="org.osgi. framework.wiring",org.osgi.fram ework.launch;version\="1.2";use s\:` | `org.osgi.framework.system.packages= org.osgi.framework;version\=" 1.10",org.osgi.framework.connect;ver sion\="1.0.0",org.osgi.framework. dto;version\="1.8";uses\:\="org.osgi.d to",org.osgi.framework.hooks. bundle;version\="1.1";uses\:\="org.os gi.framework",org.osgi.framework. hooks.resolver;version\="1.0";uses\:\ ="org.osgi.framework.wiring",org. osgi.framework.hooks.service;version \="1.1";uses\:\="org.osgi. framework",org.osgi.framework.hook s.weaving;version\="1.1";uses\:\=" org.osgi.framework.wiring",org.osgi.fr amework.launch;version\="1.2"; uses\:\="org.osgi.framework",org.osgi .framework.namespace;version\=" 1.2";uses\:\="org.osgi.resource",org.o sgi.framework.startlevel;version\=" 1.0";uses\:\="org.osgi.framework",org \="org.osgi.framework",org.osgi.f ramework.namespace;version\=" 1.1";uses\:\="org.osgi.resource", org.osgi.framework.startlevel; version\="1.0";uses\:\="org.osgi.f ramework",org.osgi.framework. startlevel.dto;version\="1.0";uses \:\="org.osgi.dto",org.osgi. framework.wiring;version\="1.2"; uses\:\="org.osgi.framework,org. osgi.resource",org.osgi.framewor k.wiring.dto;version\="1.3";uses\:\ = "org.osgi.dto,org.osgi.resource. dto",org.osgi.resource;version\=" 1.0",org.osgi.resource.dto;versio n\="1.0";uses\:\="org.osgi.dto",o rg. osgi.service.packageadmin;versio n\="1.2";uses\:\="org.osgi. framework",org.osgi.service.start level;version\="1.1";uses\:\="org. osgi.framework",org.osgi.service. url;version\="1.0",org.osgi.servic e. resolver;version\="1.1";uses\:\=" org.osgi.resource",org.osgi.dto; version\="1.1",org.osgi.util.tracke r;version\="1.5.2";uses\:\="org. osgi.framework"{dollar}{aem.jre- {dollar}{java.specification.version }} {dollar}{aem.jre- {dollar}{felix.detect.jpms}}` |
    | `{dollar}{aem.jre- {dollar}{java.specification.version }}` | `{dollar}{aem.jre- {dollar}{felix.detect.jpms}}` |

1. Upgrade to latest AEM version: Replace AEM 6.5’s QuickStart file (.jar file) with AEM 6.5 2025 release’s file (.jar file). Make sure that replaced jar has the correct user/group ownership.
1. Unpack AEM 6.5 2025 release file:
`java -jar [name_of_downloaded_jar_file] -unpack`
1. Start the AEM instance. For detailed information on start command, see determining the correct upgrade start  commands.

> [!NOTE] 
> You can use the parameter XX:MaxMetaspaceSize=1024m instead of -XX:MaxPermSize=256m. The -XX:MaxPermSize=256m option is no longer available in Java 17. For a full list of supported JVM arguments in Java 17, refer to the Oracle documentation.

    1. (For AEM Forms only) Open Package Manager and click Upload Package to upload the package.
    1. (For AEM Forms only) Select the AEM Forms add-on package downloaded from Software Distribution and click Install.

After the package is installed, you are prompted to restart the AEM instance. Do not immediately restart the server. Before stopping the AEM Forms server, wait until the ServiceEvent REGISTERED and ServiceEvent UNREGISTERED messages stop appearing in the [AEM-Installation-Directory]/crx- quickstart/logs/error.log file and the log is stable.

## Developer notes{#developer-notes}

### Check the Datastore Type

You can find the configured DATASTORE path in the instance’s configuration settings by:

1. Opening the AEM Configuration Manager. The default URL is [host:port]/system/console/configMgr.
1. Look for the `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore` and `org.apache.jackrabbit.oak.plugins.blob.datastore.SharedS3Data` Store configurations.
    * If the following configuration is present, the Datastore is FDS (File Data Store): `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore`
    * If the following configuration is present, the Datastore is S3DS (Shared S3 Data Store): `org.apache.jackrabbit.oak.plugins.blob.datastore.SharedS3DataStore`.

### Run Consistency Check

**Run consistency check for FDS instance**

You can find the configured DATASTORE path in the instance’s configuration settings by:

1. Open the terminal window. 
1. Stop AEM before starting the consistency check.
1. Navigate to parent folder of your ‘crx-quickstart ‘ directory.
1. Set the following variables for your instance: 
    * DATASTORE="crx-quickstart/repository/repository/datastore"
    * SEGMENTSTORE="crx-quickstart/repository/segmentstore"
    * PATH_TO_FDS_DATASTORE="crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config"
    * OAK_VERSION="1.22.14" ( Use the Oak version from your AEM instance)
    * REPOSITORY="crx-quickstart/repository"
1. Run these commands to download oak-run and tika-app:
    * wget -nc https://repo1.maven.org/maven2/org/apache/jack rabbit/oak-run/${OAK_VERSION}/oak-run-${OAK_VERSION}.jar
    * wget -nc https://repo1.maven.org/maven2/org/apache/tika/tika-app/1.28.5/tika-app-1.28.5.jar
1. Run the following commands to perform consistency checks
    * Index Consistency Check: java -jar oak-run-${OAK_VERSION}.jar index --fds- path=${DATASTORE} ${SEGMENTSTORE} --index-consistency-check
    * Segment Store Consistency Check: java -jar oak- run-${OAK_VERSION}.jar check ${SEGMENTSTORE}
    * Data Store Consistency Check: java -jar oak-run-${OAK_VERSION}.jar datastorecheck --consistency --ref --id --fds ${PATH_TO_FDS_DATASTORE} -- repoHome ${REPOSITORY} --store ${SEGMENTSTORE}

Run Consistency Check for S3 Data Store
1. Open the terminal window.
1. Stop AEM before starting the consistency check.
1. Navigate to parent folder of your ‘crx-quickstart ‘ directory.
1. Set the following variables for your instance:
    * PATH_TO_S3_DATASTORE="crx-quickstart/install/org.apache.jackrabbit.oak.plugins.blob.datastore.SharedS3DataStore.config"
    * SEGMENTSTORE="crx-quickstart/repository/segmentstore"
o	OAK_VERSION="1.22.14" (Use the Oak version present in your AEM instance)
o	REPOSITORY="crx-quickstart/repository"
5.	Run the following commands to download oak-run and tika- app:
o	wget -nc https://repo1.maven.org/maven2/org/apache/jack rabbit/oak-run/${OAK_VERSION}/oak-run-
${OAK_VERSION}.jar
o	wget -nc https://repo1.maven.org/maven2/org/apache/tika
/tika-app/1.28.5/tika-app-1.28.5.jar
6.	Run the following commands to perform consistency checks
 
o	Index Consistency Check for S3 Data Store:java -cp oak-run-${OAK_VERSION}.jar:tika-app-1.28.5.jar org.apache.jackrabbit.oak.run.Main index -- s3ds=${PATH_TO_S3_DATASTORE}
${SEGMENTSTORE} --index-consistency-check
o	Segment Store Consistency Check: java -jar oak- run-${OAK_VERSION}.jar check ${SEGMENTSTORE}
o	Data Store Consistency Check: java -jar oak-run-
${OAK_VERSION}.jar datastorecheck --consistency -- ref --id --s3ds ${PATH_TO_S3_DATASTORE} -- repoHome ${REPOSITORY} --store
${SEGMENTSTORE}
 
Changes in Uber Jar Packaging

The AEM Uber Jar is a single package that includes all Adobe Experience Manager (AEM) APIs, making it easy to integrate AEM into a Maven project. It is added to the project’s pom.xml file and provides access to all required AEM APIs for development.

There is a slight difference in how AEM 6.5 and AEM 6.5.2025 Uber Jars are packaged.

Uber Jars for AEM 6.5.x

For AEM 6.5.x, there are two types of Uber Jars:
1.	uber-jar-6.5.x.jar – Contains all public APIs of AEM 6.5.x.
2.	uber-jar-6.5.x-apis-with-deprecations.jar – Includes both public APIs and deprecated APIs from AEM 6.5.x.

Uber Jars for AEM 6.5.2025.x

For AEM 6.5.2025.x, there are again two types of Uber Jars, but they are handled differently:
1.	uber-jar-6.5.2025.x.jar – Contains all public APIs of AEM 6.5.2025.x.
2.	uber-jar-6.5.2025.x-deprecated.jar – Only includes deprecated APIs from AEM 6.5.2025.x.




Key Difference: AEM 6.5.x vs. AEM 6.5.2025.x Uber Jars
 
•	In AEM 6.5.x, if both public and deprecated APIs are needed, you can use include single jar, uber-jar-6.5.x-apis- with-deprecations.jar in your pom.xml file.
•	In AEM 6.5.2025.x, if you need both public and deprecated APIs, you must include two separate jars, uber-jar- 6.5.2025.x.jar for public APIs and uber-jar-6.5.2025.x- deprecated.jar for deprecated APIs.
 
Removed Bundles

com.adobe.cq.social.cq-social-activitystreams com.adobe.cq.social.cq-social-as-provider com.adobe.cq.social.cq-social-badging-api com.adobe.cq.social.cq-social-badging-basic-impl com.adobe.cq.social.cq-social-badging-impl com.adobe.cq.social.cq-social-calendar-api com.adobe.cq.social.cq-social-calendar-impl com.adobe.cq.social.cq-social-commons-oauth com.adobe.cq.social.cq-social-commons com.adobe.cq.social.cq-social-console com.adobe.cq.social.cq-social-content-fragments-impl com.adobe.cq.social.cq-social-enablement-api com.adobe.cq.social.cq-social-enablement-impl com.adobe.cq.social.cq-social-filelibrary com.adobe.cq.social.cq-social-forum com.adobe.cq.social.cq-social-gamification-api com.adobe.cq.social.cq-social-gamification-impl com.adobe.cq.social.cq-social-graph-api com.adobe.cq.social.cq-social-graph-impl com.adobe.cq.social.cq-social-group com.adobe.cq.social.cq-social-handlebars com.adobe.cq.social.cq-social-ideation-api com.adobe.cq.social.cq-social-ideation-impl com.adobe.cq.social.cq-social-jcr-provider-common com.adobe.cq.social.cq-social-jcr-provider com.adobe.cq.social.cq-social-journal com.adobe.cq.social.cq-social-livefyre com.adobe.cq.social.cq-social-members-api com.adobe.cq.social.cq-social-members-impl com.adobe.cq.social.cq-social-messaging-api com.adobe.cq.social.cq-social-messaging-impl
com.adobe.cq.social.cq-social-moderation-spamdetector-core com.adobe.cq.social.cq-social-moderation com.adobe.cq.social.cq-social-ms-provider
 
com.adobe.cq.social.cq-social-notifications-api com.adobe.cq.social.cq-social-notifications-channels-web com.adobe.cq.social.cq-social-notifications-impl com.adobe.cq.social.cq-social-qna com.adobe.cq.social.cq-social-rdb-provider com.adobe.cq.social.cq-social-reporting-management com.adobe.cq.social.cq-social-review com.adobe.cq.social.cq-social-scf-api com.adobe.cq.social.cq-social-scf-impl com.adobe.cq.social.cq-social-scoring-api com.adobe.cq.social.cq-social-scoring-basic-impl com.adobe.cq.social.cq-social-scoring-impl com.adobe.cq.social.cq-social-serviceusers-api com.adobe.cq.social.cq-social-serviceusers-impl com.adobe.cq.social.cq-social-srp-api com.adobe.cq.social.cq-social-srp-impl com.adobe.cq.social.cq-social-tally com.adobe.cq.social.cq-social-translation com.adobe.cq.social.cq-social-ugc-search-collections com.adobe.cq.social.cq-social-ugcbase-api com.adobe.cq.social.cq-social-ugcbase-impl com.adobe.cq.social.cq-social-user-ugc-management com.adobe.cq.sample.we.retail.core com.adobe.cq.screens.dcc com.adobe.cq.screens.mq.activemq com.adobe.cq.screens.mq.core
com.adobe.cq.screens com.adobe.cq.screens.sessions com.adobe.granite.socketio org.apache.jackrabbit.jackrabbit-api com.adobe.cq.commerce.cq-commerce-core com.adobe.cq.commerce.cq-commerce-pim org.apache.servicemix.bundles.abdera-parser org.apache.servicemix.bundles.jdom com.day.cq.dam.cq-dam-pim com.day.cq.dam.cq-dam-rating
org.apache.commons.io (Replaced with newer version
 
org.apache.commons.commons-io) com.adobe.granite.crx-explorer com.adobe.cq.cq-searchpromote-integration org.apache.sling.atom.taglib






























The upgrade process to Adobe Experience Manager (AEM) 6.5 Forms 2025 release involves several steps and considerations:
# Pre-Requisites & Considerations 
1.	Backup: Take a complete backup of your AEM repository, file system, and datastore. 
1.	RDBMK Support: RDBMK is not supported for AEM 6.5 Forms 2025 release. 
1.	Testing: Use the beta release software in a non-production environment to identify potential issues. 
1.	Custom Code Review: Ensure your custom code, workflows, and integrations are compatible with the new release. 
1.	Download Latest Version: Download the latest version of AEM 6.5.2025 QuickStart, AEM Analyzer, and AEM Forms Add-on from software distribution. 
1.	Privileges: Ensure you have the necessary privileges to install software and use AEM package manager. 

## In-Place Upgrade Process 
1.	Run AEM Analyzer: Use the AEM Analyzer to identify potential compatibility issues.  
1. Download and install the tool. 
1. Generate a report and run the Content Transformer if needed. 
1.	Run Consistency Check: Perform a consistency check to verify system integrity. 
1.	Stop AEM Instance: Stop your AEM instance before proceeding. 
1.	Install Java 17: Download and install Java 17, ensuring JAVA_HOME is correctly set. 
1.	Update S3 Connector: For S3DS datastore users, update the S3 connector. 
1.	Update sling.properties: Modify the sling.properties file with the new properties for the 6.5.2025 release. 
1.	Upgrade AEM Version: Replace the AEM 6.5 QuickStart file with the AEM 6.5 2025 release file and unpack it. 
1.	Start AEM Instance: Start the AEM instance using the correct commands. 
1.	Install AEM Forms Add-on: Upload and install the AEM Forms add-on package, and wait for the log to stabilize before restarting the server. 
Developer Notes
•	Check Datastore Type: Verify the configured datastore type (FDS or S3DS) in the instance’s configuration settings. 
•	Run Consistency Check: Perform consistency checks for FDS or S3DS instances using specific commands and tools like oak-run and tika-app. 
By following these steps, you can ensure a smooth upgrade to AEM 6.5 Forms 2025 release. 

