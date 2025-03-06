---
title: 'DB2&reg; database: Running a process weekly'
description: Learn how you can improve the performance of your AEM Forms DB2&reg; database.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
---
# DB2&reg; database: Running a process weekly{#db-database-running-a-process-weekly}

If your AEM Forms DB2&reg; database begins to run slowly, running the following process on a weekly basis can improve its performance:

1. Start DB2&reg; Control Center:

   (Windows) Select Start &gt; Programs &gt; IBM&reg; DB2&reg; &gt; General Administration Tools &gt; Control Center.

   (Linux&reg; and UNIX&reg;) From a command prompt, type the `db2jcc` command.

1. In the DB2&reg; Control Center object tree, click All Databases.
1. Click the database that you created for AEM Forms and click the Tables folder.
1. Select all the database tables in the contents pane, right-click them, then select Run Statistics.
1. Go to Statistics &gt; Index Statistics.
1. Select Collect Statistics For All Indexes, select Collect Statistics For Indexes With Extended Detailed Statistics, and then click OK.

A message appears when the process is completed. Close the message.
