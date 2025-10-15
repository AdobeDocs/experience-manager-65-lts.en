---
title: Current Release Notes for Adobe Experience Manager 6.5 LTS, SP1
description: Find current release information for Adobe Experience Manager 6.5 LTS, Service Pack 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
---
# Current release notes for Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Release information {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 1 (SP1), Hotfix for GRANITE-61551 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack release |
| Date | September 9, 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq660%2Fhotfixes%2Fcq-6.5.lts.1-hotfix-GRANITE-61551-1.2.zip) |

<!-- OLD URL TO JAR
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.1.jar) | -->


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## What is included in [!DNL Adobe Experience Manager] 6.5 LTS, SP1 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP1 includes new features, key customer-requested enhancements, and bug fixes. It also includes performance, stability, and security improvements released since the initial availability of 6.5 LTS in March 2025. [Install this Service Pack](#install-update) on 6.5 LTS.

<!-- ## Key features and enhancements -->

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Fixed issues in 6.5 LTS, Service Pack 1 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE --> 

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Accessibility {#sites-accessibility-65-lts-sp1}

* Fixed an issue where the text editor element in Content Fragments was truncated by default. The text editor now displays the full content without truncation. (SITES-33005)
* Fixed an issue where clicking URL paths opened Indigo's home page instead of the correct destination URL. (SITES-33004)
* Fixed an accessibility issue in a custom AEM component that caused ADA compliance failures during automated testing. (SITES-30660)
* Fixed ADA compliance issues in Alert dialog box and Workflow Messages by ensuring text displays in black on light backgrounds and meets WCAG 2.0 contrast requirements. (SITES-30138) 
* Fixed an accessibility issue where the "Category" button in the AEM Sites editor lacked a specific label, causing JAWS to announce it as "Images button menu" instead of providing a descriptive label. (SITES-27497)
* Fixed an accessibility issue where checkmark icons in the Effective Permissions screen lacked alternative text, preventing JAWS from reading and conveying their meaning. (SITES-27272)
* Fixed an accessibility issue where the Permissions page did not provide a clear JAWS announcement for removing user or group permissions, causing confusion for screen reader users. (SITES-27238)
* Fixed an accessibility issue where error messages displayed only as icons without descriptive text, preventing JAWS from announcing the errors when they occurred. (SITES-27155)
* Fixed an accessibility issue where JAWS read incorrect and unclear button descriptions in the AEM On-Premise environment, including missing heading level 2 text for the modules section. (SITES-27152)
* Fixed an accessibility issue where JAWS did not announce the number of results after filtering values in the AEM Assets tab. (SITES-27150) 
* Fixed an accessibility issue where creating a folder did not display a confirmation and JAWS did not announce it in the Assets UI. (SITES-27141)
* Fixed an accessibility issue in AEM Sites. JAWS did not announce form errors, focus moved to non-interactive error elements, and required-field errors failed to show on tab-out. (SITES-27138)
* Fixed an accessibility issue where the Timelines button menu lacked a specific label, causing JAWS to read only "Activities button menu" without providing a clear description. (SITES-27134)
* Fixed an accessibility issue where JAWS did not announce the action or role for container items, reading only "Breadcrumb v1" and "button v2" instead of descriptive labels. (SITES-27131) 
* Fixed an accessibility issue where the quick publish pop-up did not provide a proper success message, preventing screen readers from announcing completion feedback. (SITES-26912)
* Fixed an accessibility issue in the coral-column view where elements with ARIA roles requiring child roles did not contain them, causing non-compliance with accessibility standards. (SITES-26898)
* Fixed an accessibility issue where "template" and "properties" texts in the top navigation of the create page were not visible in Reflow mode, preventing access for keyboard and screen reader users. (SITES-26895)
* Fixed an accessibility issue where tooltips for the "search," "solution," "help," "inbox," and "user" icons in the top navigation were not accessible using keyboard navigation. (SITES-26889)
* Fixed an accessibility issue where Basic tab form fields did not provide error suggestions, preventing users from receiving guidance when required input fields were left empty. (SITES-26885)
* Fixed an accessibility issue where NVDA and Narrator screen readers did not announce template file details in the Create page, preventing users from receiving complete information programmatically. (SITES-26884)
* Fixed an accessibility issue that used an incorrect name for the "Page title text box" in the Basic tab, preventing screen readers from providing accurate information to users. (SITES-26879)
* Updated button foreground and background colors to meet WCAG 2.2 AA minimum contrast ratio requirements, improving readability and accessibility for all users. (SITES-26877)
* Resolved an issue that caused the "template" and "properties" texts in the top navigation of the create page to disappear after resizing, ensuring visibility and accessibility for low-vision users. (SITES-26872)
* Fixed an issue that caused multiple horizontal scroll bars to appear on the main page after applying a Reflow, ensuring a single scroll bar displays for proper accessibility and content visibility. (SITES-26800)
* Fixed an accessibility issue in the AEM Page Editor where keyboard focus unexpectedly resets to the start of the Demographic Toolbar after activating buttons such as Persona, Cart, or Abandoned. Focus now remains on the activated button to support consistent keyboard navigation and screen reader workflows. (SITES-25306) 
* Fixed accessibility label association issue for page title and tags fields. The AEM interface now correctly associates accessibility labels with the "Title" and "Page Title" fields when using screen readers like JAWS. The fix ensures proper label reading and improves ADA compliance across page creation, properties, and move workflows. (SITES-27149)
* Fixed missing visual label for comment input fields in timeline. Corrected missing visual labels for "comment" input fields under the timeline section to improve accessibility. The update ensures that screen readers can accurately announce the field labels. This experience enhances form navigation and submission for all users, particularly those individuals that rely on assistive technologies. (SITES-26903)
* Fixed keyboard accessibility for ellipsis button in timeline comments. Enabled keyboard navigation for the ellipsis (three dots) button next to comments under the timeline section. Users can now access and interact with the button using the tab key, improving accessibility for users who rely on keyboard-only navigation. (SITES-26891)
* Improved NVDA/Narrator announcements for search results in selection dialog boxes. Updated the Open Selection dialog box to announce whether search results are found or not when using screen readers, such as NVDA or Narrator. This improvement helps users relying on assistive technologies understand the outcome of their search actions without needing visual confirmation. (SITES-26883)
* Corrected ARIA role for ellipsis icon beside comment input field. Updated the ellipsis (three dots) icon beside the comment input field to use the correct ARIA role, ensuring screen readers can accurately identify the element. This improvement enhances accessibility compliance and improves the experience for users relying on assistive technologies. (SITES-26881)
* Corrected invalid ARIA attributes in Coral UI components. Updated Coral UI components to ensure all ARIA attributes use valid values, improving accessibility-compliance. In particular, cases were addressed where invalid values like `aria-modal="dialog"` were incorrectly assigned. This enhancement enables screen readers to interpret dialog box elements correctly, improving accessibility for users relying on assistive technologies. (SITES-26873)
* Improved visibility and tooltips for icons in Reflow scenarios. Enhanced the Reflow behavior to ensure tooltips display correctly for **Download**, **Reprocess assets**, and **Checkout** icons. Focused on an accessibility issue where icons and their labels became invisible when the viewport resized or browser zoom settings changed. This fix supports users with low vision by maintaining visibility and providing proper icon descriptions during Reflow. (SITES-26871)
 

#### Admin user interface{#sites-adminui-65-lts-sp1}

* Fixed an accessibility issue where JAWS did not announce list roles or provide navigation and activation instructions in the Create Site dialog box. (SITES-30661)
* Screen reader support for status messages in the Sites filter view works as expected, ensuring users receive clear and timely feedback when switching between views. (SITES-24992)
* The Date Picker in the Filters Rail displays fully within its container, providing adequate touch target size and eliminating clipping issues. (SITES-24988) 
* Selected filter tags now use semantic HTML and aria-labels that match the visual presentation, ensuring accurate role support and clear actions for assistive technologies. (SITES-24980) 
* Added an aria-label attribute to the References Rail region to provide a unique, descriptive label for screen reader users and ensure consistent landmark identification across the page. (SITES-24973)
* Updated the References Rail to use relative units for sizing and positioning, enabling content to scale and remain fully functional when zoomed to 400% at a 1280x1024 viewport. (SITES-24972) 
* Confirmed table elements in the Sites Home Page List View contain proper column header roles, enabling screen readers to announce headers for each data cell. (SITES-24942)
* NVDA now announces the Modified date in the Tree Directory, ensuring screen reader users receive complete asset detail information. (SITES-24782) 
* Fixed issue where the NVDA screen reader announced incomplete text for items in the Tree Directory component in AEM Sites. NVDA now reads full text for each item, improving accessibility and compliance. (SITES-24780) 
* Added keyboard accessibility to the Window Splitter in the Tree Directory, enabling users to resize the left side bar using only a keyboard. (SITES-24779) 
* Updated Help menu search results to include correct ARIA roles for list items, ensuring screen readers announce links properly for improved accessibility. (SITES-24729) 
* Fixed an issue where screen readers did not announce the "X of Y results" status message. Or, the "no results found" message after applying filters in the Sites Filter panel, ensuring users receive proper confirmation of results. (SITES-24720) 
* Corrected missing role assignments for navigation links in the App navigation. Added appropriate ARIA roles to ensure that screen readers correctly identify and announce navigation elements. (SITES-24719) 
* Replaced incorrect grid role markup for selected filter tags with button elements and added accessible names, ensuring screen readers correctly announce and identify the tags. (SITES-24717) 
* Added screen reader announcements for the References Rail status message when performing multiple selections, ensuring users receive confirmation of changes. (SITES-24678) 
* Corrected search field behavior so that the first result is not automatically announced. Screen readers now announce the number of results that are found, enabling users to navigate the list without incorrect focus announcements. (SITES-24658) 
* Removed incorrect `aria-label` attributes from non-interactive static elements in the List View to prevent screen readers from announcing misleading or irrelevant information. (SITES-24515) 
* Updated the checkbox in the first column of the List View to use the Title column text for its accessible name, ensuring screen readers accurately convey the purpose of the form field. (SITES-24514) 
* Added proper ARIA attributes and live region support to announce loading status messages to screen reader users when navigating through content. (SITES-24481) 
* Updated responsive design to eliminate horizontal scrolling when content is zoomed to 400% with a viewport width of 1280×1024, ensuring full visibility without side scrolling. (SITES-24308) 
* Corrected focus navigation in the Sites Admin UI to follow a logical order, returning focus to the "Select All" button after pressing Esc and moving focus to the next interactive element after pressing Tab. (SITES-24307) 
* Updated focus order in the Sites Admin UI so the breadcrumbs button in the `<betty-titlebar-title>` element receives focus in the correct sequence during keyboard navigation. (SITES-24305) 
* Verified skip link functionality to ensure it moves keyboard focus to the main content area, allowing keyboard users to bypass header elements and access content efficiently. (SITES-24061) 


#### Classic user interface{#sites-classicui-65-lts-sp1} 

Fixed an issue in Classic UI where checkbox labels were missing and HTML displayed as encoded text in multiple UI elements, including Date Search and non-standard interfaces. (SITES-31822) 

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

AEM now prevents performance degradation caused by malformed XMP metadata in image assets. Assets that contain invalid or non-compliant XMP property names, such as those with numeric segments or unqualified structures, no longer trigger repeated warning logs during processing. The system filters out problematic metadata to ensure that asset ingestion and validation is complete without errors. (SITES-30683)

<!--
#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1} -->

#### [!DNL Content Fragments] - Fragments editor{#sites-fragments-editor-65-lts-sp1}

Other authors can still publish Content Fragments even when another author checks them out, which is contrary to the intended behavior of the checkout feature. This fix prevents other users from seeing or using the publish buttons in the authoring interface when a Content Fragment is checked out. (SITES-30578)

<!--
#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1} -->

#### Component console{#sites-component-console-65-lts-sp1}

Fixed an issue in the Product List Component where the "Select All" checkbox added only the first 20 SKUs from the initial page instead of all SKUs in the search results. (SITES-29191)

#### Core backend{#sites-core-backend-65-lts-sp1}

Improperly formatted XMP metadata triggered an error during processing of image assets in the `ValidationDataServlet`. The fix ensures compliant metadata handling and avoids redundant parsing of invalid properties. (SITE-30683)

<!--
#### Core Components{#sites-core-components-65-lts-sp1}

#### Campaign integration{#sites-campaign-integration-65-lts-sp1}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}

#### Launches{#sites-launches-65-lts-sp1}

#### Link Checker{#sites-link-checker-65-lts-sp1} -->

#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp1}

* Fixed a JavaScript error `ns.ui.alert is not a function` that occurred when re-enabling ghost component inheritance in AEM 6.5 On-prem. (SITES-31993)
* Fixed an issue where the Rollout "Later" option allowed continuing without selecting a date in AEM 6.5. (SITES-31374)

#### Page editor{#sites-pageeditor-65-lts-sp1}

* Resolved an issue in the Teaser Modal where the Link & Actions tab continued displaying error styling, icons, and the aria-invalid attribute after valid data entry and error resolution. (SITES-25527) 
* Fixed an issue in the Teaser Modal text editor where the Lists and Paragraphs buttons did not convey their expanded or collapsed state to screen readers, ensuring accurate aria-expanded attribute updates. (SITES-25365) 
* Fixed an issue in the Demographics Toolbar where adjusting the Cart Slider with keyboard input moved focus to the Cart button instead of retaining focus on the slider, improving navigation efficiency for keyboard users. (SITES-25324) 
* Added an accessible name to the Cart Slider in the Demographics Toolbar by assigning a value to its associated `<label>` element. This fix improved compatibility with assistive technologies and enhancing usability for screen reader users. (SITES-25322) 
* Added ARIA roles and accessible names to buttons inside the Demographics Toolbar drop-down. This fix enabled proper identification by assistive technologies and improved navigation for keyboard and screen reader users. (SITES-25315) 
* Adjusted the Demographic Toolbar layout to prevent content overflow beyond the viewport at 200% browser zoom, ensuring all controls remain accessible without horizontal scrolling. (SITES-25309) 
* Corrected focus management in the Demographic Toolbar to keep keyboard focus on the activated button instead of resetting focus to the toolbar's starting position. (SITES-25306) 
* The button label overlap functions as designed, using a tooltip to display the label when modes with similar screen widths are active. (SITES-25285) 
* The annotation modal includes a visible submit button, allowing users to submit annotations without relying on the Escape key or clicking outside the modal. (SITES-25281) 
* The annotation modal includes a pen icon button that allows users to submit annotations, providing a clear and accessible submission method. (SITES-25269) 
* Corrected screen reader announcements for the Annotate and Close Annotate buttons to provide accurate, relevant feedback and remove unrelated or confusing information. (SITES-25268) 
* Canvas sections in AEM Editor pages now support full keyboard accessibility. Users can activate section titles and edit buttons using only the keyboard, without relying on mouse hover. This update ensures compliance with WCAG 2.1.1 and improves usability across components (such as Teaser, Image, Carousel, Layout, Timewarp, and Annotation modals). (SITES-25256) 
* Removed unnecessary horizontal scrolling in the Carousel Modal at 320px width to ensure all content displays within the viewport without requiring side-to-side navigation. (SITES-25254) 
* Removed unnecessary horizontal scrolling in the Image Modal at 320px width to ensure all content displays within the viewport without requiring side-to-side navigation. (SITES-25244) 
* Removed unnecessary horizontal scrolling in the Teaser Modal at 320px width to ensure all content displays within the viewport without requiring side-to-side navigation. (SITES-25242) 
* Enabled keyboard navigation for the `List` and `Paragraph Format` pop-up menu, both in the Teaser Modal. This fix allows users to access and navigate these menus using arrow keys. (SITES-25235) 
* Corrected screen reader announcements for the Annotate and Close Annotate buttons to provide accurate, relevant feedback aligned with the associated actions. (SITES-25234) 
* Improved the Help button label in the Teaser Modal to describe its purpose clearly and provide meaningful context for all users, including assistive technology users. (SITES-25224) 
* Improved the emulator ruler for screen reader users by associating ruler measurements with their respective devices. Also, replacing the tooltip with an aria-describedby element. (SITES-24955) 
* No fix was implemented because the Edit button functions as intended and provides informational context rather than performing an action. (SITES-24950) 
* Confirmed focus order on the Editor page follows a logical sequence, allowing users to navigate through all interactive elements without skipping or looping back unexpectedly. (SITES-24937) 
* Confirmed Preview mode canvas updates text spacing correctly when users apply custom text spacing settings, ensuring consistent formatting across all content areas. (SITES-24936) 
* The verified Preview button no longer triggers context or state changes in focus, ensuring users activate the button intentionally before the page view updates. (SITES-24784) 
* Added correct ARIA role assignments to App navigation links, enabling screen readers to identify accurately and announce navigation items for improved accessibility. (SITES-24718) 
* Updated the Change Filters button to announce expanded and collapsed states to screen readers, removed redundant ARIA attributes, and adjusted labeling to provide clear, non-duplicative descriptions. (SITES-24713) 
* Added screen reader announcements for search results status messages in the Link selection dialog box, ensuring users receive confirmation when results load or no matches are found. (SITES-24700) 
* Added screen reader announcements for the loading state of the Image Modal, ensuring users receive feedback when the modal is loading and ready for interaction. (SITES-24697) 
* Resolved an accessibility issue where the sticky header obscured Teaser Modal content at 200% and 400% zoom, ensuring full visibility and usability when using page magnification. (SITES-24523)
* Added a status message with the number of search results to the Search/Filter field, enabling screen readers to announce results to users. (SITES-24506) 
* Added screen reader announcements for the number of search results in the Search/Filter field, ensuring users receive immediate feedback when results load. (SITES-24505) 
* Added an accessible name to the tab list in the Side Rail panel, enabling screen readers to announce its purpose in compliance with WAI-ARIA guidelines. (SITES-24492) 
* Added descriptive labels to ambiguous editor icons, ensuring all users clearly understand each button's function. (SITES-24480) 
* Enabled full keyboard accessibility for section titles and action buttons in the Canvas view, ensuring consistent operation for mouse and keyboard users. (SITES-24479) 

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Universal editor {#sites-universal-editor-65-lts-sp1}

* Fixed a race condition in QueryTokenService that caused bad logins when multiple requests with query parameters triggered before the login-token service returned a result. (SITES-30659)
* Fixed an issue in UniversalEditorURLService where saving an array of mapped paths in Felix ConfigMgr kept only the first item. (SITES-30292) 

### [!DNL Assets]{#assets-65-lts-sp1}

Fixed an issue where syncing assets from remote DAM to Sites local AEM removed the published status and replication-related properties from assets. (Assets-48958)

<!--
#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp1}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp1}



### [!DNL Forms]{#forms-65-lts-sp1}


#### Forms Designer 

#### Forms

#### Forms JEE 
 
#### Forms Captcha {#forms-captcha-65-lts-sp1} 

#### XMLFM {#forms-xmlfm-65-lts-sp1}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp1}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp1} -->



### Foundation {#foundation-65-lts-sp1}

<!--
#### Apache Felix {#foundation-apachefelix-65-lts-sp1}

#### Campaign{#foundation-campaign-65-lts-sp1}

#### Cloud Services{#foundation-cloudservices-65-lts-sp1}



#### Communities {#foundation-communities-65-lts-sp1}

#### Content distribution{#foundation-content-distribution-65-lts-sp1}

#### CRX {#foundation-crx-65-lts-sp1}

#### Granite{#foundation-granite-65-lts-sp1} -->

#### HTL{#foundatoin-htl-5-lts-sp1}

Resolved OSGi dependency cycles that blocked the HTL script engine factory from functioning, ensuring proper service resolution and script execution. (Granite-58275)

#### Integrations{#foundation-integrations-65-lts-sp1}

* Removed usage of commons-httpclient 3.x from the `com.adobe.cq.cq-analytics-integration` bundle and replaced it with `org.apache.httpcomponents.httpclient` 4.5.13.B0001 to align with the latest AEM 6.5 LTS standards. (CQ-4360586)
* Removed the deprecated Search&Promote integration bundle from AEM to eliminate unused components and reduce maintenance overhead. (CQ-4358030)
* Added new backend test cases for the SiteCatalyst integration to improve analytics validation and ensure more comprehensive coverage. (CQ-4359991)
* Fixed an issue in Launch Config's Properties section where the Company and Property drop-downs did not appear. Also, Save and Close triggered errors despite all mandatory fields being filled, and incorrect error messages displayed for Company and Property when only the Title field was empty. (CQ-4359853)
* Removed the `searchpromote` servlet path entry from version 6.6 to align with the removal of the Search&Promote bundle. (CQ-4359523)
* Fixed HTTP test cases for the Target repository to ensure accurate validation and improved test reliability. (CQ-4359022)
* Removed Guava caching usage from the integration-adobeims-console module to eliminate Guava library dependencies. (CQ-4358710) 
* Validated DTM integration workflows, inbox tasks, and project functionality in AEM 6.6 to ensure proper operation in AEM 6.5. (CQ-4358151)
* Validated Content Insight functionality in AEM 6.6 to ensure compatibility and proper operation in AEM 6.5. (CQ-4357774)
* Validated Cloud Services functionality in AEM 6.6 to ensure compatibility and proper operation in AEM 6.5. (CQ-4357773)
* Validated Adobe IMS Console integration in AEM 6.6 to ensure compatibility and proper operation in AEM 6.5. (CQ-4357772)
* Updated Jenkins pipeline for the Test&Target integration to run on Java 17, resolve failing Selenium tests, move select tests to Playwright, and ensure all unit tests pass. (CQ-4357770)
* Aligned DX integrations, workflow, inbox, and projects with the 6.6.0 branch by updating build and test pipelines. Also, resolving upgrade compatibility issues, and validating all affected services for stability and functionality. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Localization{#foundation-localization-65-lts-sp1}

* Localized the strings in the "Remove Access Control" dialog box from the "Permissions" list to display the correct translations. (GRANITE-59427) 
* Fixed an issue in the Model Editor's "Or Split Properties" Add Rule dialog box where multiple UI strings, including operators and field labels, appeared unlocalized. All strings now display with correct localization. (CQ-4354014) 
* Added missing translation for the "Show Description For" tooltip in the Workflow Models Edit dialog box. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Resolved an issue where AEM recreated or renamed existing configuration files under `/apps/system/config` during upgrades, replacing `.cfg.json` files with `.config` files. (GRANITE-58899)

#### Omnisearch{#foundation-omnisearch-65-lts-sp1}

Fixed an accessibility issue where placeholders incorrectly appeared as labels for input fields. This issue cause missing field labels in Search, AEM Experience Fragments, Content Fragments, and Content Fragment Models. (Granite-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projects{#foundation-projects-65-lts-sp1}

* Resolved an issue that displayed an incorrect error pop-up when deleting a project in Calendar view, despite successful project deletion. (CQ-4358890)
* Fixed an issue in Firefox where the "Asset Collection" card footer in Project view overlapped the card border. The footer now aligns correctly without overlapping. (CQ-4353317)

#### Quickstart{#foundation-quickstart-65-lts-sp1} 

* Updated the uninstall script to adjust the version range for the Guava bundle, preventing it from being blocklisted when installed through the Package Manager. (GRANITE-59559)
* Fixed an issue in the Replication UI that displayed an error (`#1660`) when editing replication agents by correcting the handling of classic checkboxes in the interface. (GRANITE-58302)
* Resolved multiple startup errors for the S3 datastore when running AEM 6.5 LTS with JDK 21 by addressing missing service permissions, updating configuration handling, and ensuring required services initialize correctly. (GRANITE-57082)
* Defined the maintenance and sustenance strategy for AEM 6.5. This fix included the following:
    * Service Pack cadence.
    * Hotfix cadence.
    * Parallel support with AEM 6.6.
    * Updated support matrix.
    * Add-on ownership responsibilities. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Updated Sling ResourceAccessSecurity to version 1.1.2 to resolve a `ClassCastException` that occurred when multiple `ResourceAccessGate` references initialized `ResourceAccessSecurityImpl`. (NPR-42750)
* Fixed an issue in Adobe Stock integration where the License dialog box appeared grayed out. This issue was due to the removal of required input fields by the `sunt:initList` function. The function was found in the Coral Foundation client libraries. Updated the client libraries to retain the necessary fields, enabling proper license dialog box functionality. (NPR-42748) 
* Fixed unexpected JSP compilation error with `org.apache.sling.scripting.jsp 2.6.0`. (NPR-42640)

<!--
* Backported the fix for Sling Scripting issue that caused `DataTimeParseException` and `String.length()` null pointer exceptions during package installation. Updated Sling Scripting to version 2.8.3-1.0.10.6 to reduce installation errors and improve stability. (NPR-42640) -->

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### User interface{#foundation-ui-65-lts-sp1}

* Resolved issue in the AEM Author UI that limited the display of user groups to 41. This issue was due to a default batch limit in the Granite UI group picker component. Updated the component to display all groups without truncation. (NPR-42749)
* Resolved issue in the On-prem page creation wizard where required fields in multifield components were not revalidated when editing page properties. This issue, in turn, allowed authors to bypass validation and proceed with incomplete data. (GRANITE-58826)
* Corrected ARIA attributes for the help button in AEM to ensure that JAWS screen readers announce a clear, user-friendly label instead of displaying untranslated icon and text metadata. (GRANITE-55360) 

#### WCM{#foundation-wcm-65-lts-sp1}

* Added Java 17 support for AEM Translations by updating translation bundles, verifying Java package compatibility, removing deprecated dependencies, and ensuring full functionality through comprehensive testing. (CQ-4357525)
* Removed the flaky Evergreen test `com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` to prevent false failures during automated testing. (CQ-4298376) 

#### Workflow{#foundation-workflow-65-lts-sp1}

* Added the missing `data-detailsurl` attribute in inbox items to prevent undefined values from appearing in URLs when using AEM 6.5 LTS with Java 21. (GRANITE-60158)
* Fixed a NullPointerException in the `deactivate` method of the `WorkflowToPublishEventService` bundle when running AEM 6.5 LTS with Java 21, ensuring proper workflow service shutdown without errors. (GRANITE-58151)
* Updated the workflow index to support sharing, out-of-office customization, and resolution of timeline query issues. (GRANITE-52640)
* Updated the workflow index to support sharing, out-of-office customization features, and resolution of timeline query issues. (GRANITE-52294)
* Resolved increased error log failures during log comparison validation for a program upgrade to AEM release 10912, ensuring stable workflow execution. (GRANITE-44268)
* Updated the URL sanitization method in Workflow Repos to replace `url.searchParams` with `url.search`, improving XSS protection for vulnerable URLs. (CQ-4359585)
* Validated workflow, inbox, and Projects functionality in AEM 6.6 Forms to ensure proper operation and integration. (CQ-4358777)
* Implemented automation for releasing Workflow–Content artifacts through Jenkins, enabling streamlined and consistent deployment processes in AEM 6.5. (CQ-4358472)
* Fixed an issue in the Inbox Create Task workflow where the "Add Task" dialog box did not close after clicking Submit, despite the task being created, due to a JavaScript syntax error. (CQ-4355336)
* Fixed an issue that prevented saving Inbox view configuration due to a missing property definition for `isEndUserConfigurationEnabled`. (CQ-4287757) 

## Forms

### Forms Designer

* When a user exports the data for an XFA-based PDF using the exportDataAPI, the resulting XML shows discrepancies when compared with the XML data exported manually using Acrobat Reader. Values of some fields were missing in the output compared to the output generated from Acrobat Reader. (LC-3922791)
* Generating a tagged PDF with the Output Service in Workbench adds an unexpected label tag under the reference tag in a table of contents item. (LC-3922756)
* When flattening dynamic, fillable PDFs to PDF/A format using the Output Service, the dynamic state is not preserved. This issue leads to data loss and potential compliance issues, especially when tagging is enabled. (LC-3922708)
* When a user places field captions with bottom or right alignment in AEM Forms Designer, the tag tree includes only the caption without the corresponding value, leading to incomplete accessibility tagging. (LC-3922619)
* The QR codes in generated PDFs become unreadable. The alternative text for the QR codes also fails accessibility testing, affecting screen reader compatibility. (LC-3922551)
* When a user renders a letter in Agent UI, the content fails to display correctly due to the FormService render() API. (LC-3922461)
* When a user tries to create PDF/A files from XDPs with Sunken Square style in AEM Forms, it results in border rendering issues. (LC-3922180)
* Flattening dynamic forms bound to an XSD schema causes partial data loss, as some bound form data is not retained in the final PDF. (LC-3922008)
* When a user tries to export data from interactive PDFs using the extractData API in AEM Forms 6.5.13 and later versions, it results in missing data compared to manual export. (LC-3921983)
* Converting XDP forms to static PDFs with AEM Forms Designer or the Output service creates multiple `Link-OBJR` tags. The issues cause an accessibility compliance issue because a single unified link tag is expected. (LC-3921977)

### Adaptive Forms

* In AEM Forms, enabling "Allow Rich Text for Title" on the root panel causes "Exclude Title from Document of Record" on a nested panel to hide the root panel's title incorrectly. It does so in the generated Document of Record. (FORMS-19696)
* The system ignores the custom `sling:resourceType` assigned through `aem:afProperties` in a JSON schema. The custom resource type is ignored during rendering. (FORMS-19691)
* When a user submits an Adaptive Form with prefilled attachments using URIs, the form submission fails with a NullPointerException due to missing binary data. (FORMS-19371) (FORMS-19486)
* When a user uploads a PDF under the 'Forms and Documents' section, the timeline feature stops functioning. (FORMS-19407)(FORMS-19234)
* When a user uploads files using the out-of-the-box (OOTB) file attachment component in AEM Forms, security vulnerabilities are identified. The issue leads to potential interception of the submission process by unauthorized entities. (FORMS-19271)
* When a user configures an out-of-the-box Adaptive Form in AEM Forms to generate a Document of Record (DoR) automatically, the "Title" field in Acrobat Reader's Document Properties does not display the captured DoR title. By default, the form title does not appear in place of the filename. (FORMS-19263)
* When a user opens an Interactive Communication in Agent UI, the prefilled data cannot be completely erased; upon removal, it automatically refills with the same data. (FORMS-19151)
* When a user previews a date field in the Agent UI, the date unexpectedly changes. The issue occurs due to time zone discrepancies between the VM's UTC setting and the system's interpretation of the date. (FORMS-19115)
* When a user submits a form, file attachments may duplicate, leading to multiple uploads of the same file. (FORMS-19045)(FORMS-19051)
* Adding coordinators to policy sets in Document Security fails across both production and lower environments. (FORMS-18603, FORMS-18212, FORMS-19697)
* When a user clicks the "datepicker-calendar-icon" in desktop mode with an empty field, an error occurs due to the undefined _$focusedDate variable, disrupting associated custom scripts. (FORMS-18483)(FORMS-18268)
* When a customer previews a letter, the 'Amount in words' field fails to display or update number values incorrectly, leading to misalignment and missing spaces in the content. (FORMS-18437, FORMS-17330, FORMS-18209, FORMS-18557, CTG-4150848,FORMS-19614, LC-3922004)
* When a customer previews a saved letter on RHEL, the content misaligns, spaces are missing, and unexpected characters like 'x' appear. (FORMS-18422)(FORMS-17641)
* When a user navigates between tabs in AEM Forms, selecting components on the first tab becomes unresponsive. (FORMS-18345)
* When a user converts an HTML file to PDF using the WebToPDF option, the output PDF is missing the header section, including metadata and title tags. (FORMS-18223, FORMS-17835, FORMS-19642, FORMS-18224)
* In the AEM JEE Process Manager SDK, when a user invokes the retryAction(long actionOid) method, the system incorrectly retries the first action found in the tb_action_instance table. This workflow occurs even when a specific action ID is provided or when the ID is null, resulting in unintended behavior. (FORMS-18187)
* A user encounters issues where the saved draft and submission functionalities fail without displaying any error message. (FORMS-18069)
* Transitioning from XSD-based Foundation Components to Core Components prevents the implementation of cross-file references in JSON schemas, impacting Adaptive Forms migration. (FORMS-18065)
* When a user previews a letter in the Agent UI, the date field shows an incorrect value due to IC time conversion issues. These discrepancies arise from time zone differences between the VM environment and the system's interpretation of time (UTC versus local time). (FORMS-17988) (FORMS-17248)
* When a user previews letters using Notice IC templates in AEM Forms, PDF generation times vary significantly, from 1.5 seconds to more than 10 seconds, even on the same server. This inconsistency affects business critical workflows. (FORMS-17951)
* When a user binds a Scribble Signature object in an Adaptive Form to an XDP using the 'Data Sources' option, changes cannot be saved. The reason is due to persistent aspect ratio validation errors, even when using valid values. (FORMS-17587)
* When a user uses a specific XDP with many hidden fields for document fragments, AEM creates CRX nodes with the `cm:optional` property set to false, which causes the Interactive Communication (IC) submission to fail. (FORMS-17538)
* When a customer previews a letter, the numeric box field fails to handle negative values correctly when digit limits for Lead and Frac are defined. This issue occurs due to the use of parseFloat, which treats the minus sign as part of the number. (FORMS-17451)
* When a letter is previewed, the use of the "*" wildcard in the Adobe.json file is noticed, raising concern about its purpose and potential modification. (FORMS-17317)
* When a user uses a screen reader on the Apply for a Fixed Rate Saver joint account the headings are incorrectly announced as clickable, causing accessibility issues. (FORMS-17038)
* When a form is embedded, the generated iframe is missing a title attribute, leading to an accessibility compliance issue. (FORMS-17010)
* Downloading a form using the Forms Manager UI always includes associated dependencies, such as themes and fragments. (FORMS-15811)
* When a user accesses the form on mobile devices (iOS and Android&trade;), the 'next' and 'previous' buttons on the first page are disabled. However, the screen reader does not identify them as disabled. (FORMS-15773)
* When a user saves a large form with fragments and lazy loading enabled, it fails to retrieve drafts, disrupting the workflow. (FORMS-19890, FORMS-19808)
* Users experienced issues saving form properties for Adaptive Form based on Core Components. This error occurred because redundant scripts from the Adaptive Form based on Foundation Components editor are included, causing conflicts in the Adaptive Form based on Core Components. editor. (FORMS-17474)
* Users experienced issues with the Adobe Sign GovCloud Signature page not rendering in an iframe. (FORMS-16803)
* Users experienced errors when selecting references for Core Component Adaptive Forms (AF) fragments. The error message "Unable to render reference: Not an absolute path" appeared, preventing proper reference rendering. (FORMS-19678)
* Added support for multi-threaded conversion with Acrobat DC, enabling users to perform simultaneous Word, Excel, and PowerPoint document conversions to PDF documents more efficiently. (FORMS-21310)
* Added inclusion of `com.adobe.granite.toggle.impl.dev` bundle in AEM Service Pack 24, enabling more streamlined development processes by removing it from the Forms add-on. (FORMS-20139)
* Removed FeatureToggleRenderConditionServlet from forms-foundation and com.adobe.granite.toggle.impl.dev bundle from forms add-on. This update ensures that after forms add-on installation, the render condition resolves correctly, improving component functionality for customers. (FORMS-20138)
* Users experienced slow performance due to long-running queries in Adaptive Forms. This update backports query changes to improve efficiency. Customers can now create an index with the tag name aemformsAFReferences. (FORMS-21411)
* Users experienced misaligned header positions when converting HTML to Portable Document Format (PDF) using WebtoPDF. This issue affected consistency in document layout and readability of output. (FORMS-21502, FORMS-21540)
* Users experienced PDF/A-1b validation failures despite successful PreFlight verification. This issue affected document compliance checks for enterprise customers using PDF validation tools. (FORMS-20196)
* Users experienced untranslated strings in the UI, causing confusion and difficulty in understanding the interface. (FORMS-6542)
* Users experienced issues with email notifications. The Send Email Workflow Step failed to send emails, impacting automated communication processes. (FORMS-17961)
* Users experienced failing tests for forms workflows, which impacted their ability to complete workflow processes efficiently. (FORMS-16231)
* Users were unable to use the timeline feature of PDF files in AEM forms. This issue affected users' ability to track document changes and revisions effectively. When uploading any PDF under the 'Forms and Documents' section in the AEM forms area, the timeline view ceases to function. (FORMS-19408)
* Users experience a null pointer exception when interacting with OData. This cause interruptions in data retrieval processes. (FORMS-20348)
* Removed the google.common.collect library following the removal of Guava, an open-source Java library. This update ensures better compatibility and performance for enterprise customers using Adaptive Forms. (FORMS-17031)
* When Server-Side Validation (SSV) is enabled, form submissions may fail. If you encounter this issue, please contact [Adobe Support](https://business.adobe.com/in/support/main.html) for assistance. (FORMS-21966)

### Forms Captcha

* Added `Hcaptcha` and `Turnstile` support for Adaptive Forms based on Foundation Components. (FORMS-16562)
* Users experienced icon overlap issues in the `Create hCaptcha Configuration` dialog box. When filling required fields, the information icon overlapped the error icon, causing confusion during configuration setup. (FORMS-16916)
* Users experienced incorrect configuration being picked up for reCAPTCHA in Adaptive Forms based on Foundation Components. When the configuration container was not selected for a form, multiple configurations in the `conf/global` folder caused the issue. (FORMS-19237)
* Users experienced issues with reCAPTCHA not being rendered. This affected form submissions and security validation for enterprise customers. (FORMS-17136, FORMS-19596)
* Users experience an issue where the size of reCAPTCHA enterprise is not reflected in the User Interface (UI). (FORMS-16574)
* Users experienced issues with the ReCaptcha functionality due to an unclosed ResourceResolver in `ReCaptchaConfigurationServiceImpl`, causing intermittent validation failures during form submissions. (FORMS-19241)
* Users experienced issues with reCAPTCHA validation when forms are authored in Sites. AEM forms did not recognize the form name correctly, causing validation failures. (FORMS-20486)
* Users experienced form submissions even when the enterprise reCAPTCHA score was 1.0, leading to potential security risks. (FORMS-16766){{$include }}
* Improved reCAPTCHA alerting in Adaptive Forms by updating submit error codes to 400. Also, refined log alerts to distinguish between timeouts, expirations, and bot detection failures, enhancing troubleshooting accuracy and system observability. (FORMS-19240)
* Closed an unclosed ResourceResolver instance in ReCaptchaConfigurationServiceImpl to prevent potential resource leaks and improve system stability when using reCAPTCHA integrations in AEM Forms. (FORMS-19242)
* Improved CAPTCHA configuration handling for AEM Forms by ensuring the correct configuration binds to each form when multiple entries exist in the /conf/global folder. Prevents unintended use of incorrect CAPTCHA settings when the configuration container is not explicitly selected. (FORMS-19239)

### Forms Management UI

* Users experienced unlocalized strings in the `Forms` > `Create Watchfolder` >` Watchfolder` creation process. When creating a watched folder, strings such as `Watchfolder creation` and `Watchfolder created successfully` were not found, affecting the User Interface experience. (FORMS-15234)

## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

The platform of [!DNL Adobe Experience Manager] 6.5 LTS builds on top of updated versions of the OSGi-based framework (Apache Sling and Apache Felix) and the Java&trade; Content Repository: Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x is used as a servlet engine for the Quickstart.

### Java&trade; support  {#java-support}

* Support for Java&trade; 17 and Java&trade; 21.
* For optimal performance, override the default GC values with other values. For more information, see the [install and update](/help/sites-deploying/custom-standalone-install.md) section.
* Adobe distributes Java&trade; 17  and Java&trade; 21 maintenance updates for customer usage in AEM-related projects, when not publicly available from Oracle.

### Uberjar packaging {#uber-jar-packaging}

* There is a slight difference in Uberjar packaging of AEM 6.5 LTS. For more information, see [Update the AEM Uber Jar version](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Upgrade {#upgrade}

* For details about the upgrade procedure, see the [upgrade documentation](/help/sites-deploying/upgrade.md).

## Install and update {#install-update}

For setup requirements, see [installation instructions](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> If you are directly upgrading to LTS SP1 from old 6.5 SPs, please follow the instructions given for 6.5 to 6.5 LTS GA [upgrade](/help/sites-deploying/upgrade.md).


For detailed instructions, see the [upgrade documentation](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> For fresh AEM 6.5 LTS installations, index definitions must be installed separately. For more information, see [this article](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Install and update AEM Forms add-on {#install-update-aem-forms-add-on}

For detailed instructions, see [Performing an In-Place Upgrade](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).



## Supported platforms {#supported-platforms}

Find the complete matrix of supported platforms including support-level on [AEM 6.5 LTS technical requirements](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java&trade; 17/Java&trade; 21 are the recommended versions to use with AEM 6.5 LTS.


## Deprecated and removed features {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe continually reviews product capabilities to improve customer value by modernizing or replacing older features. These changes are made with careful attention to backward compatibility.

To communicate the impending removal or replacement of Adobe Experience Manager (AEM) capabilities, the following rules apply:

1. Announcement of deprecation comes first. While deprecated, capabilities are still available but are not further enhanced.
1. Removal of deprecated capabilities occurs in the following major release at the earliest. The actual target date for removal is planned for announcement later.

This process gives customers at least one release cycle to adapt their implementation to a new version or successor of a deprecated capability, before actual removal.

### Deprecated features {#deprecated-features}

This section lists features and capabilities that Adobe has deprecated in AEM 6.5 LTS. Typically, Adobe deprecates features before removing them in a future release and provides an alternative.


Customers are advised to review if they use the feature/capability in their current deployment, and make plans to change their implementation to use the alternative provided.

| Area | Feature | Replacement | Version (SP) |
| --- | --- | --- | --- |
| Sites | [SPA Editor](/help/sites-developing/spa-overview.md) | The preferred editors for managing headless content in AEM are:<br>- [The Universal Editor](/help/sites-developing/universal-editor/introduction.md) for visual editing.<br>- [The Content Fragment Editor](/help/assets/content-fragments/content-fragments-managing.md) for form-based editing. | 6.5 LTS GA |

### Removed features {#removed-features}

This section lists features and capabilities that have been removed from AEM 6.5 LTS. Prior releases had these capabilities marked as deprecated.

| Area | Feature | Replacement | Version (SP) |
| --- | --- | --- | --- |
| Commerce| AEM CIF Classic is not supported. | Migrate to [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions| Social/Communities is not supported. | No replacement available. | 6.5 LTS GA |
| Screens| Screens are not supported. | No replacement available. | 6.5 LTS GA |
| Assets| `dam-pim` and `dam-rating` are not supported as bundles are dependent on social. | No replacement available. | 6.5 LTS GA |
| Assets| `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` has been removed. | Use the alternate api `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` that has been added. | 6.5 LTS GA |
| Portal| AEM Portal Director is not supported. | No replacement available. | 6.5 LTS GA |
| Granite| Bundle `com.adobe.granite.socketio` is removed. | No replacement available. | 6.5 LTS GA |
| Granite| `com.adobe.granite.crx-explorer` is not supported. | No replacement available. | 6.5 LTS GA |
| Granite| `crx2oak` is not supported. | Pick the relevant version of [Oak-upgrade](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6.5 LTS GA |
| Adobe| `com.adobe.cq.cq-searchpromote-integration` is not supported. | No replacement available. | 6.5 LTS GA |
| Guava| All guava dependencies are now removed in AEM and hence the `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` bundle is not part of AEM. |Customers can add guava on their own if they are dependent on guava or replace guava code with java collections or other alternates if possible. | 6.5 LTS GA |
| `We.Retail`| `We-retail` sample site is not supported. | No replacement available. | 6.5 LTS GA |
|Open Source| `oak-solr-osgi` bundle is not supported.| No replacement available. | 6.5 LTS GA |
|Open Source| `org.apache.servicemix.bundles.abdera-parser`, `org.apache.servicemix.bundles.jdom` and `org.apache.sling.atom.taglib` are not supported.| No replacement available. | 6.5 LTS GA |
|Open Source| `org.apache.commons.io` packages are now exported from `org.apache.commons.commons-io`.| No change required. | 6.5 LTS GA |
|Open Source| `javax.mail` packages are being exported from the `com.sun.javax.mail` bundle.| No change required. | 6.5 LTS GA |
|Open Source| `org.apache.jackrabbit.api` packages now are exported from the `org.apache.jackrabbit.oak-jackrabbit-api` bundle.| No change required. | 6.5 LTS GA |
|Open Source| `com.github.jknack.handlebars` is not supported| Pick the relevant [version](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6.5 LTS GA |


## Known issues {#known-issues} 

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

<!-- REMOVED THIS SECTION AS PER CQDOC-23046
### Issue with JSP scripting bundle in AEM 6.5.21-6.5.23 and AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23, and AEM 6.5 LTS GA ship with the `org.apache.sling.scripting.jsp:2.6.0` bundle, which contains a known issue. The issue typically occurs under high load when the AEM instance handles many concurrent requests.

When this issue occurs, one of the following exceptions may appear in the error logs alongside references to `org.apache.sling.scripting.jsp:2.6.0`:

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

A hotfix [cq-6.5.lts.0-hotfix-NPR-42640](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) is available to resolve this problem. -->

### Dispatcher connection failure with SSL-only feature (Fixed in AEM 6.5 LTS SP1 and later){#ssl-only-feature}

>[!NOTE]
>
> This issue is only present in the AEM 6.5 LTS GA release.

When enabling the SSL-only feature in AEM deployments, there is a known issue that affects connectivity between the Dispatcher and AEM instances. After enabling this feature, health checks may fail and communication between Dispatcher and AEM instances can be disrupted. This issue specifically occurs when customers attempt to connect through `https + IP` from the Dispatcher to AEM instances. It is related to SNI (Server Name Indication) validation problems.

**Impact:**

* Health check failures with HTTP 400 response codes
* Broken traffic between Dispatcher and AEM instances
* Content cannot be properly served through the Dispatcher
* Connection failures when using HTTPS with IP addresses in Dispatcher configuration
* HTTP 400 "Invalid SNI" errors when connecting via HTTPS + IP

**Affected environments:**

* AEM deployments with Dispatcher configurations
* Systems where the SSL-only feature has been enabled
* Dispatcher configurations using `https + IP` connection method to AEM instances

**Solution:**
If you experience this issue, please contact Adobe Customer Support. A hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) is available to resolve this problem. Do not attempt to enable SSL-only features until applying the necessary hotfix.

## OSGi bundles and content packages included{#osgi-bundles-and-content-packages-included}

The following text documents list the OSGi bundles and Content Packages included in this [!DNL Experience Manager] 6.5 LTS, Service Pack 1 release:

* [List of OSGi bundles included in Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [List of Content Packages included in Experience Manager 6.5 LTS, Service Pack 1](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Restricted websites{#restricted-sites}

These websites are only available to customers. If you are a customer and need access, contact your Adobe account manager.

* [Product download at licensing.adobe.com](https://licensing.adobe.com/)
* [Contact Adobe Customer Support](https://experienceleague.adobe.com/en/docs/customer-one/using/home).
 
