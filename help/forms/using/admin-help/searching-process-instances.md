---
title: Searching for process instances
description: Use the Process Search page to enter search criteria for finding a process instance.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: yes
hidefromtoc: yes
removedfrom6.5.2025: yes
exl-id: e358ee51-c23f-4737-9dcf-3193ed541bbb
---
# Searching for process instances{#searching-for-process-instances}

>[!NOTE]
> 
> Ensure that the user has admin privileges to access the administrator console.

Use the Process Search page to enter search criteria for finding a process instance. You can access the Process Search page from the Forms Workflow page. Or, you can click **Search** on the Process Instance page.

You can enter basic criteria to perform a general search, specific attributes to perform a detailed search, or a combination of basic criteria and specific attributes to perform a combined search.

## Perform a general search {#perform-a-general-search}

A general search for a process is most appropriate if you know the process ID of the process instance. Or, if you are looking for a group of related process instances, or if only a few process instances are running.

Enter the basic criteria to perform a general search. If you enter multiple criteria, the search is performed with an implied AND condition.

1. In the administration console, click Services &gt; Forms Workflow &gt; Process Search.
1. On the Process Search page, under General Search, provide the following criteria:

    * **Process ID:** The positive integer that identifies each unique process instance.
    * **Process Status:** Select a status from the list.
    * **Application:** Select an application from the list. Only deployed applications are shown.
    * **Process Name - Version:** Select a process name from the menu. Only deployed processes are shown.

1. Click **Search**. The Process Instance page appears, listing the instances found.

## Perform a detailed search for a process {#perform-a-detailed-search-for-a-process}

You can enter specific attributes to perform a detailed search. A detailed search is most appropriate if you have many process instances running and you need to narrow the possible finds by certain criteria.

1. In the administration console, click Services &gt; Forms Workflow &gt; Process Search.
1. On the Process Search page, under Detailed Search, specify your first criteria set:

    * In the Attribute list, select an attribute.
    * In the Filter list, select an operator.
    * In the Value box, type a value appropriate to the attribute you selected.

1. To add another row, select More Filters. Another set of Attribute, Filter, and Value lists appears, and a Condition list.
1. Under Condition, select AND or OR. Repeat steps 1 - 3 as required to narrow your search further.
1. To add or remove rows, click More Filters or Fewer Filters. You can have from one to four rows.
1. Click **Search**. The Process Instance page appears, listing the instances found.

See also [About process instance statuses](/help/forms/using/admin-help/processes.md#about-process-instance-statuses).

## Perform a combined search for a process {#perform-a-combined-search-for-a-process}

To create a search that uses both general and detailed criteria, enter values in both areas on the Process Search page. The system applies an implied `AND` between the two areas.

If the search is too narrow, no instances are found.
