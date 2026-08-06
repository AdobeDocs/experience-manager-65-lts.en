---
title: Current Release Notes for Adobe Experience Manager 6.5 LTS, SP3
description: Find current release information for Adobe Experience Manager 6.5 LTS, Service Pack 3.
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
---

# Current release notes for Adobe Experience Manager 6.5 LTS, SP3 {#release-notes}

## Release information {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 LTS |
|---|---|
| Version | Service Pack 3 (SP3) <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack release |
| Date | August 20, 2026 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Download URL | [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.2.jar) |


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

<!-- **Mandatory Hotfix** – To avoid SNFE (SegmentNotFoundException) issues with offline compaction when installing SP2, install the hotfix described in [Known issues – Repository corruption during online compaction](#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146). -->

## What is included in [!DNL Adobe Experience Manager] 6.5 LTS, SP3 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP3 includes new features, key customer-requested enhancements, and bug fixes. This service pack strengthens [!DNL Sites] accessibility, [!DNL Content Fragments], MSM Live Copies, the GraphQL API, and Foundation stability. It also improves performance, security, and localization across the platform since the initial availability of 6.5 LTS in March 2025. [Install this Service Pack](#install-update) on 6.5 LTS.

<!-- ## Key features and enhancements -->



<!-- UPDATE THE EACH RELEASE -->

## Fixed issues in 6.5 LTS, Service Pack 3 {#fixed-issues}

### [!DNL Sites]{#sites-65-LTS-SP3}

* AEM 6.5 LTS, Service Pack 3 includes the Crosswalk bundles, content package, system users, service-user mappings, feature toggles, and required OSGi configuration. Fresh installations provide the Crosswalk prerequisites automatically and require only customer-specific runtime configuration. (SITES-41596)
* AEM 6.5 LTS, Service Pack 3 updates `cq-wcm-core` to support Crosswalk on Adobe Managed Services. The update adds template creation and Universal Editor access while removing obsolete custom code and feature toggles. (SITES-37657)


#### Accessibility {#sites-accessibility-65-lts-sp3}

* The Page Editor canvas now supports keyboard-only component management. Authors can use Insert Component, Cut, Paste, and Delete to add, reorder, and remove components. (SITES-25359) CRITICAL
* Keyboard users can now reorder table rows in Sites List View without using drag-and-drop gestures. Keyboard controls let users select a row, move it to another position, and complete the placement. (SITES-24946) CRITICAL

* The Custom Properties editor now supports keyboard interaction with its formatting controls. Authors can move focus among toolbar options, select a text style, and format property values using only a keyboard. (SITES-40333) MAJOR

* Keyboard focus now skips the side panel Components list when the available interaction requires drag and drop. This change prevents keyboard users from entering an unusable component-selection workflow. (SITES-40752)
* Closing an overlay now restores focus to its triggering control. Keyboard and screen-reader users no longer return to the overlay or lose their position in the interface. (SITES-40819)
* Keyboard navigation no longer moves focus to hidden page content. This change maintains a predictable focus sequence and prevents navigation disruptions. (SITES-41430)
* The Lock button now provides precise screen-reader feedback based on its title. Users hear a clear action label instead of a lengthy description. (SITES-41431)
* A visual indicator now identifies the selected option in the Change File or Folder list box. The indicator helps users understand the breadcrumb path and recognize the current folder. (SITES-25532)
* Screen readers now announce the ascending or descending sort direction once. A descriptive label clearly identifies the button action and removes duplicate feedback. (SITES-25534)
* AEM Sites now provides broader accessibility support across common authoring workflows. Updates improve keyboard interaction, interface labels, focus management, and assistive technology feedback. (SITES-38239)
* Toolbar items now display visible labels when they receive keyboard focus. Keyboard users can identify each control before they activate it. (SITES-40751)
* Keyboard and screen-reader users can now leave the Inbox menu without leaving it open. The menu closes automatically and preserves a clear navigation path. (SITES-25518)
* Color swatches now display a selected-state icon with sufficient contrast. The clearer indicator helps users recognize the active swatch across different background colors. (SITES-25523)
* The Edit Layout toolbar now reports the current device accurately to assistive technology. Device buttons no longer suggest that users can toggle each button on and off. (SITES-25524)
* The Search modal now displays the **Sort by** label with sufficient text contrast. The updated styling improves readability for users with low vision. (SITES-25531)
* Sites List View sort buttons now meet minimum contrast requirements. Users can identify each sort control and its state more easily against the table background. (SITES-25372)
* The Side Rail Assets list no longer reloads when the Filter field receives keyboard focus. Users can enter the field without unexpected content movement or repeated screen-reader loading announcements. (SITES-25377)
* Content Fragment sidebar tabs now provide consistent accessible labels. NVDA announces the tab name instead of announcing the selected subnavigation item. (SITES-25509)
* The Help menu now closes when keyboard or screen-reader focus moves outside it. Users can continue navigating header controls or page content without leaving the menu open. (SITES-25517)
* Text entered in Demographics toolbar fields now meets minimum contrast requirements. Users can read profile values more clearly against the text field background. (SITES-25318)
* The Page Information menu now displays focused options with sufficient text contrast. The clearer styling helps users track keyboard focus throughout the menu. (SITES-25321)
* Checkboxes in the Teaser, Image, and Carousel dialog boxes now expose their related instructions to screen readers. Users hear the supporting description when keyboard focus reaches each checkbox. (SITES-25364)
* Text editor controls now communicate their current state to assistive technology. Screen readers identify the active paragraph format and selected hyperlink target option. (SITES-25367)
* Screen readers now announce the **Rotate Device** button and current device orientation clearly. Activating the control reports the new orientation without using a label that describes the opposite action. (SITES-25292)
* Keyboard navigation now skips controls hidden inside the collapsed Demographics toolbar. Users can move through Layout Preview without encountering unavailable toolbar options. (SITES-25304)
* Text labels in the Demographics toolbar now meet minimum contrast requirements during Layout Preview. Users can read labels such as Recommended more clearly against the toolbar background. (SITES-25307)
* The Demographics toolbar now displays button focus indicators with sufficient contrast. Users can identify the active Commerce, Persona, or Device control during keyboard navigation. (SITES-25308)
* The Edit Layout toolbar uses a grouped focus indicator for the device selector. The outline includes the related **Select Device** and **Rotate Device** controls as part of the intended toolbar behavior. (SITES-25283)
* The Edit Layout toolbar no longer truncates the **iPhone 8 Plus** label when users select another device. The full device name remains visible across all button states. (SITES-25284)
* The Edit Layout ruler now provides measurement context to screen readers. Users hear a descriptive label and the measurement format instead of an unexplained series of numbers. (SITES-25287)
* The Edit Layout toolbar now highlights the **Desktop** button when desktop view is active. The visual indicator makes the current device selection clear. (SITES-25290)
* Keyboard focus now remains visible on the swatch button across all available colors. Added spacing prevents the focus indicator from blending into the selected swatch. (SITES-25253)
* Screen readers now identify the Timewarp Date field correctly. The field no longer provides misleading feedback that suggests it opens a dialog box. (SITES-25263)
* The Annotation button label now meets minimum contrast requirements in its default and hover states. Users can read the label clearly against the button background. (SITES-25267)
* Screen readers now announce meaningful labels for controls in the Annotation dialog box. Each button communicates its action without an unnecessary Annotation prefix. (SITES-25277)
* The Assets side rail Edit button now provides a larger touch target. Users can activate the control more reliably without selecting a nearby element. (SITES-25221)
* The Page Editor now uses a logical heading hierarchy. Screen readers identify the page title as the primary heading and side rail titles as subordinate headings. (SITES-25222)
* The Annotation dialog box now exposes its title as a semantic heading. Screen-reader users can identify the title and navigate the dialog box structure through heading commands. (SITES-25248)
* Screen-reader users now receive feedback when they filter the Insert New Component list. The search field describes its filtering behavior, and a status message reports the result count. (SITES-25251)
* The Side Rail Components panel now uses semantic list markup. Screen readers can announce the item count and support efficient list navigation. (SITES-25214)
* Info buttons now use larger icons in the Components panel. Users can locate and recognize each control more easily. (SITES-25217)
* Component titles now remain visible when users increase text spacing. Long titles wrap instead of truncating or overlapping nearby content. (SITES-25219)
* The Assets Side Rail **Edit** button now indicates that it opens a new browser tab. Visual and screen-reader cues prepare users before navigation. (SITES-25220)
* Annotation Mode now places keyboard focus on the annotation toolbar when the toolbar opens. Keyboard and screen reader users can move through the controls in a logical sequence without navigating backward from the **Close** button. (SITES-24996)
* Select buttons for Path and Tags fields no longer use a checkbox icon. The updated icon shows that the control opens a selection dialog box instead of changing a checked state. (SITES-25210)
* The Filter field in the Side Rail Components panel now has a valid accessible label. Screen readers announce the field purpose instead of relying on an icon or placeholder text. (SITES-25212)
* The Assets Side Rail now hides decorative thumbnails from screen readers. Users no longer hear the asset name twice when they navigate the asset grid. (SITES-25213)
* Accordion buttons in the Filters rail now display focus indicators with sufficient contrast. Keyboard users can track focus while navigating filter categories. (SITES-24986)
* The Filters rail now displays clear keyboard focus around radio buttons. Increased contrast helps users track their position across filter options. (SITES-24987)
* Loading status messages on the Filters page now meet minimum text contrast requirements. Users can read progress feedback while switching between Card View and List View. (SITES-24991)
* The page title in the Editor Canvas now uses semantic heading markup. Assistive technology can announce the title and include it in heading navigation. (SITES-24993)
* Expanding the Emulator menu now moves keyboard focus to the first menu item. Collapsing the menu keeps focus within the logical secondary toolbar sequence. (SITES-24954)
* Text within the Live View table now meets minimum contrast requirements. Users can read Live Copy details clearly during normal and hover states. (SITES-24956)
* The References rail now uses semantic heading markup for its title. Screen readers announce the heading during initial load and while users browse folders. (SITES-24967)
* Card links now describe their destinations clearly. Screen-reader users can identify each link without hearing the card's full metadata. (SITES-24975)
* Header menu buttons no longer tell screen readers that they open dialog boxes. Screen readers instead announce each button's expanded or collapsed state, which accurately describes the menu behavior. (SITES-24742)
* Text on the Delete button now provides sufficient contrast against its red background. Users can identify the action more easily before confirming deletion. (SITES-24772)
* Canvas cards no longer expose separate image and heading links that lead to the same destination. A single link reduces duplicate keyboard stops and repeated screen reader announcements. (SITES-24947)
* List View now displays the drag-and-drop button with greater visual prominence. Updated icon size, weight, and contrast make the control easier to locate and use. (SITES-24951)
* Header buttons now provide concise accessible names: Search, Apps, Help, Inbox, and User. Screen readers no longer announce redundant terms such as "clickable" or "graphic" during keyboard navigation. (SITES-24715)
* Links in App Navigation now display stronger visual emphasis. Increased text size and weight improve readability for users with low vision or color-vision differences. (SITES-24723)
* Inbox links now use semantic list markup. Screen readers can identify the links as a related group, announce the item count, and support more efficient navigation. (SITES-24730)
* Tooltip controls in the User Preferences dialog box now expose descriptive accessible names. Screen readers announce each control's purpose instead of saying "blank" before reading the tooltip content. (SITES-24732)
* Each Filter Rail landmark now includes a unique accessible label. Screen readers can distinguish the Filter Rail from other page regions and identify it during navigation. (SITES-24686)
* Editor dialog boxes now separate Help and Toggle fullscreen buttons from the heading element. Screen readers identify these interactive controls accurately and no longer announce them as headings. (SITES-24696)
* The CSV Report button now warns users before opening a new browser tab. Its accessible label communicates the behavior to screen reader and keyboard users before activation. (SITES-24704)
* The Filter Rail now loads labels for Saved Searches and Select Search Directory consistently. The Filters button no longer inserts label elements during focus, keyboard, or mouse interactions. (SITES-24706)
* The Close and Remove Location buttons now provide larger touch targets. Users can activate either control more reliably without selecting adjacent elements. (SITES-24530)
* The Remove Location button and its focus indicator now meet minimum contrast requirements. Stronger contrast helps users identify the control and track keyboard focus. (SITES-24531)
* Editor iframes now include descriptive titles across the canvas, side rails, component dialog boxes, and layout preview. Screen readers can identify each frame when focus enters it. (SITES-24650)
* Improved text contrast makes References Rail messages easier to read. The change clarifies prompts that request a selection or report unavailable references. (SITES-24666)
* The Components panel gives each information icon a meaningful accessible label. Screen readers consistently identify the control that shows a component description. (SITES-24500)
* Keyboard focus now surrounds the entire Show description button for Byline. The visible outline helps users track their position and avoid activating another control. (SITES-24503)
* The Teaser component dialog box no longer exposes the Help and Toggle fullscreen buttons as headings. Screen readers announce both controls as buttons and preserve the correct heading structure. (SITES-24525)
* The Adobe Experience Manager header control correctly reports its expanded or collapsed state. The control opens and closes navigation content, so screen readers receive valid state information. (SITES-24528)
* Filter results mark globe icons as decorative and remove their accessible names. Screen readers ignore the icons instead of announcing misleading descriptions. (SITES-3057)
* The Time Warp dialog box now associates time-entry errors with the corresponding Hours or Minutes field. Screen readers announce the affected field alongside the validation message. (SITES-10980)
* The selected content tree item no longer becomes part of the Change file or folder control label. Screen readers hear a clear control name without extra state text. (SITES-24496)
* Region landmarks in the Assets side rail now expose distinct accessible names. Screen reader users can identify and navigate each region without ambiguity. (SITES-24497)
* Screen readers now ignore the Carousel dialog box's decorative Help and Fullscreen icons. Keyboard navigation no longer triggers unnecessary icon announcements. (SITES-2912)
* Screen readers now skip decorative toolbar icons in the Teaser dialog box. Help, Fullscreen, formatting, and link controls no longer produce redundant announcements. (SITES-2934)


#### Admin user interface{#sites-adminui-65-lts-sp3}

* AEM now lets members of the Administrators group unlock pages and impersonate users. Group members can complete both administrative tasks through their existing access. (SITES-14732)
* Assets Admin View now updates an asset card after authors select **Revert to this Version** in the Timeline. The thumbnail displays the restored version immediately and no longer shows stale preview content. (SITES-46590)


#### Classic user interface{#sites-classicui-65-lts-sp3} 

Indonesian Language Copy properties display the correct ID language code. The References rail no longer substitutes IN when authors create or review an Indonesian Language Copy. (SITES-44918)


#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp3}

The Assets console now responds when users apply search filters. Changing a Content Fragment Model filter refreshes the results instead of leaving the current asset list unchanged. (SITES-38686) MAJOR


#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp3}

* The Assets page now localizes the tooltip for a locked Content Fragment. Users see the translated **Checked Out By** label when they hover over the lock indicator. (SITES-42531) MAJOR

* AEM localizes the Invalid name provided validation message during Content Fragment creation. Unsupported title characters no longer trigger English text across non-English interfaces. (SITES-19796)
* AEM translates the Content Fragment Models string during Content Fragment creation. The Assets interface no longer shows English text for that label in localized environments. (SITES-22336)
* Content Fragment services no longer rely on obsolete feature-toggle logic. The streamlined implementation removes toggle-dependent branches and keeps service pack behavior consistent. (SITES-38688)
* AEM translates the Later option during scheduled Content Fragment publication. The publishing workflow matches the active interface language. (SITES-42532)
* AEM translates the Main string in the Content Fragment download dialog box. The Elements section matches the active interface language. (SITES-42534)


#### [!DNL Content Fragments] - Fragment Editor{#sites-fragments-editor-65-lts-sp3}

* The Content Fragment Editor now positions Rich Text Editor dropdown menus correctly. Each menu stays aligned with its toolbar control and keeps nearby formatting controls visible. (SITES-44005) CRITICAL

* The Edit Content Fragment button now appears and works immediately for Reference Multifield entries. Authors no longer need to save, close, and reopen the parent Content Fragment before editing an embedded fragment. (SITES-43733) MAJOR

* The Content Fragment Editor shows one focus outline when authors select a multiline text field. The outline no longer duplicates or overlaps nearby controls. (SITES-39253)
* Content Fragment creation displays CJK placeholder text without italic styling. Japanese, Korean, Simplified Chinese, and Traditional Chinese characters retain their intended appearance. (SITES-43548)
* The Content Fragment Editor refreshes the status banner after authors save or publish a fragment. Authors can confirm Modified, Saved, or Published states without reloading the browser tab. (SITES-45897)
* The Content Fragment Editor validates fields consistently after Granite UI changes. Updated client libraries restore the expected validation behavior. (SITES-46650)


#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp3}

* GraphQL JSON responses now include embedded image references when DAM filenames contain spaces or non-ASCII characters. Client applications can retrieve and render these images without renaming the assets. (SITES-42191) MAJOR
* The Content Fragment GraphQL API now includes several query-processing and response-handling updates. The changes prevent duplicate cache headers and values, improve encoding, preserve persisted-query status information, handle empty headers, and return appropriate endpoint errors. (SITES-40159) MAJOR
* The PersistedQueryServlet now processes encoded variables in valid GraphQL persisted queries without recording false errors or warnings. Queries continue to return successful responses while logs reflect their actual execution status. (SITES-39354) MAJOR

* Reloading the GraphQL Endpoints page preserves the localized empty-state message. The page no longer reverts to English when no endpoints exist. (SITES-43586)


<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp3}-->


#### [!DNL Content Fragments] - Model Editor{#sites-model-editor-65-lts-sp3}

* The Content Fragment Models console now displays uploaded thumbnails for configurations whose names contain localized characters. Authors no longer lose thumbnail previews when configuration names use non-English text. (SITES-39242) MAJOR

* The Content Fragment Model Editor displays localized **Field Label** text as soon as authors add a component to the canvas. Authors no longer need to save and reopen the model to see the translation. (SITES-45383)
* The Content Fragment Model Editor localizes the validation message shown when authors select an invalid model type for a Composite component. The message now matches the active locale instead of appearing only in English. (SITES-41117)
* The Content Fragment Model Editor localizes all text in the Model is locked dialog box. The dialog box no longer mixes English button labels and instructions with translated interface text. (SITES-28592)



#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp3}

The headless Content Fragment REST API bundle removes obsolete feature toggles and related conditional code. Supported API behavior remains unchanged, while the bundle retains only the toggles required for active features. (SITES-39113)



#### Component console{#sites-component-console-65-lts-sp3}

The Content Finder now lists assets whose names contain non-encodable characters without failing or generating exceptions. The Components Live Usage page also loads large result sets continuously without displaying empty rows during scrolling. (SITES-44672) MAJOR

<!--
#### Content API{#sites-content-api-65-lts-sp3}

#### Core backend{#sites-core-backend-65-lts-sp3}
-->

#### Core Components{#sites-core-components-65-lts-sp3}

* Multifield components now store a separate remote asset selection for each entry. Authors can select, change, and save remote images without duplicating one image across every multifield item. (SITES-42376) MAJOR
* ThumbnailServlet now stops processing after it redirects a request for a missing resource. This change prevents repeated null-pointer exceptions and excessive error logging during DAM and console browsing. (SITES-41238) MAJOR


#### Campaign integration{#sites-campaign-integration-65-lts-sp3}

The Campaign ContentServlet now preserves the JSON response content type during content requests. This change stops the repeated `WARN` and `ERROR` log entries that occurred after an upgrade from AEM 6.5.24. (SITES-46902) MAJOR


#### Experience Fragments{#sites-experiencefragments-65-lts-sp3}

Authors can now browse more than 40 templates while creating an Experience Fragment variation. Each additional page preserves the original folder filter and displays the next matching templates. (SITES-41531) MAJOR


<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp3} -->


#### Launches{#sites-launches-65-lts-sp3}

Launch promotion history now displays localized text in the Sites Timeline. The Timeline translates the messages "Created version of" and "before promoting launch" across supported locales. (SITES-13389)


<!-- #### Link Checker{#sites-link-checker-65-lts-sp3} -->



#### MSM - Live Copies{#sites-msm-live-copies-65-lts-sp3}

* Content Fragment Live Copy folders now retain cq:rolloutConfigs when authors save unchanged properties. Authors can later update rollout settings without losing the existing configuration. (SITES-43729) CRITICAL

* Authors can now roll out component changes from the editable toolbar on a blueprint page. The rollout completes without a JavaScript error and propagates the changes to the Live Copy. (SITES-46052) MAJOR
* Authors can now complete MSM rollouts from blueprint pages after an upgrade. The rollout dialog box loads the available Live Copies and enables its rollout controls instead of remaining in a perpetual loading state. (SITES-43116) MAJOR

* Live Copy Overview now applies localized date formats throughout Relationship Status. The **Live Copy Source Last Modified**, L**ive Copy Last Modified**, and **Last rolled out** fields match the user's locale. (SITES-40756)
* Deactivating a blueprint parent and its child pages in one request now produces one rollout event per path. The rollout manager no longer runs duplicate actions for the same child page. (SITES-44987)


#### Page editor{#sites-pageeditor-65-lts-sp3}

* Authors can now create and apply tags with uppercase letters or spaces during one Page Properties save. AEM immediately stores the normalized tag value and preserves the page assignment. (SITES-42550) CRITICAL

* Scrolling through the style menu no longer removes the highlight from the selected style. Authors can confirm their current selection while reviewing other available options. (SITES-30874) MAJOR

* The Rich Text Editor Link button now opens when authors access AEM through HTTP. Link creation no longer triggers a `crypto.randomUUID` error. (SITES-39467)
* Authors can now copy and paste configured Content Fragment components into empty layout containers. The pasted component retains its original Content Fragment reference and no longer displays the *Choose an experience variation* error. (SITES-41586)
* The Image Editor now honors custom crop ratios during hybrid inline editing. Each image drop target uses its own configuration, so crop selections apply in a correct manner outside full-screen mode. (SITES-45771)

<!--
#### Replication{#sites-replication-65-lts-sp3}

#### Rich Text Editor{#sites-rte-65-lts-sp3}

#### Template Editor{#sites-template-editor-65-lts-sp3}

#### Universal editor {#sites-universal-editor-65-lts-sp3}

### [!DNL Assets]{#assets-65-lts-sp3}

#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp3}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp3}
-->



<!--
### [!DNL Forms]{#forms-65-lts-sp3}
-->



### Foundation {#foundation-65-lts-sp3}

#### AEM Context Service {#foundation-aem-context-service-65-lts-sp3}

AEM 6.5 LTS introduces AEM Context Service support. The rollout adds service APIs, agent integration, AMS provisioning, Experience Cloud integration, production monitoring, operational runbooks, and usage reporting. (GRANITE-65148)

#### Apache Felix {#foundation-apachefelix-65-lts-sp3}

The AEM mail service now continues sending email when intermittent configuration errors occur. Administrators no longer need to restart the Day Communique 5 Mailer bundle to restore email delivery. (GRANITE-66817) MAJOR

<!--
#### Campaign{#foundation-campaign-65-lts-sp3}

#### Cloud Services{#foundation-cloudservices-65-lts-sp3}

#### Communities {#foundation-communities-65-lts-sp3}

#### Content distribution{#foundation-content-distribution-65-lts-sp3}

#### CRX {#foundation-crx-65-lts-sp3}

#### Granite{#foundation-granite-65-lts-sp3}

#### HTL{#foundation-htl-5-lts-sp3}

#### Integrations{#foundation-integrations-65-lts-sp3}

#### Jetty{#foundation-jetty-65-lts-sp3}
-->

#### Localization{#foundation-localization-65-lts-sp3} 

* The Operations console now localizes previously untranslated text across Health Reports. Users see translated status messages, warnings, maintenance results, and performance information. (NPR-44280) MAJOR

* The Audit Log Maintenance task now displays a localized disclaimer. Administrators see the compliance and legal guidance in their selected language before they configure automated audit-log purging. (NPR-44188)
* The Edit User page now displays a localized error when users reorder modified profiles. The message clearly explains that changed profiles cannot move until users save their changes. (NPR-44282)
* AEM now localizes tooltips throughout the Content Fragment List properties. The translated guidance explains model selection, tag filtering, content paths, item limits, and sort settings. (SITES-14969)
* Component Help links in the Template Editor now open localized documentation. Authors reach guidance that matches their selected language instead of English-only component pages. (SITES-15058)
* The Component Policy editor now localizes errors that report an unmodifiable resource or a failed node creation. Template authors receive these messages in their selected language. (SITES-17475)

<!-- #### Omnisearch{#foundation-omnisearch-65-lts-sp3} -->

#### Operations Dashboard{#foundation-operations-dashboard-65-lts-sp3}

The `/system/health/systemalive.json` endpoint now remains available after customers upgrade AEM LTS. A corrected servlet context configuration prevents HTTP 404 responses and supports health-monitoring systems that rely on the endpoint. (GRANITE-69457) CRITICAL

#### Platform{#foundation-platform-65-lts-sp3}

The default HTL expression-option allow list now recognizes `decorationTagName` and `cssClassName`. Rendering the standard responsive grid no longer fills `error.log` with repeated unknown-option warnings. (GRANITE-67152)

<!--
#### Projects{#foundation-projects-65-lts-sp3}

#### Oak {#foundation-oak-65-lts-sp3}

#### Quickstart{#foundation-quickstart-65-lts-sp3} 
-->


#### Security{#foundation-security-65-lts-sp3}

The **Copy Group** action now opens the expected form instead of displaying a blank page. Administrators can enter a new group ID and description, then duplicate an existing security group. (NPR-44302) MAJOR


<!-- #### Sling{#foundation-sling-65-lts-sp3} -->


#### Translation{#foundation-translation-65-lts-sp3}

Translation projects now maintain accurate status counts as workflows progress. Launch creation and status propagation follow the expected workflow behavior, eliminating inconsistent project metadata. (NPR-43420)


#### User interface{#foundation-ui-65-lts-sp3}

* The Country/Region label now appears in the selected interface language. Localized interfaces no longer display the English label. (NPR-43883)
* Selecting a sibling page now activates **Select** in composite multifield path pickers. Authors can confirm the new path without enlarging the browser window or repeating the selection. (GRANITE-69323)


<!-- #### WCM{#foundation-wcm-65-lts-sp3} -->


#### Workflow{#foundation-workflow-65-lts-sp3}

* Workflow Package pages now support the Content Tree and editable Resource Definition components in the Touch UI Page Editor. Authors can navigate package content and inspect or update its components without using the Classic UI. (GRANITE-67348) MAJOR
* The Touch UI Page Editor now renders the Content Tree for Workflow Package pages. Authors can inspect the package structure and edit Resource Definition components through the same editor. (GRANITE-67186) MAJOR

* The workflow variable dialog now displays the correct controls for Form Data Model, JSON, XML, and Document variables. Authors no longer see raw HTML markup when they create these non-primitive variables. (GRANITE-67915)



## About [!DNL Experience Manager Foundation] {#experience-manager-foundation}

The platform of [!DNL Adobe Experience Manager] 6.5 LTS builds on top of updated versions of the OSGi-based framework (Apache Sling and Apache Felix) and the Java&trade; Content Repository: Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x is used as a servlet engine for the Quickstart.

### Java&trade; support  {#java-support}

* Support for Java&trade; 17 and Java&trade; 21.
* For optimal performance, override the default GC values with other values. For more information, see the [install and update](/help/sites-deploying/custom-standalone-install.md) section.
* Adobe distributes Java&trade; 17  and Java&trade; 21 maintenance updates for customer usage in AEM-related projects, when not publicly available from Oracle.

### Uberjar packaging {#uber-jar-packaging}

The UberJar for AEM 6.5 LTS SP3 uses the AEM 6.5 LTS UberJar version 6.6.3. You can retrieve the corresponding UberJar artifacts from the Maven Central Repository. Unlike AEM 6.5, AEM 6.5 LTS separates public APIs and deprecated APIs into two different artifacts.

To compile against the public APIs, use the following:

    ```xml
    <dependency>
        <groupId>com.adobe.aem</groupId>
        <artifactId>uber-jar</artifactId>
        <version>6.6.3</version>
        <classifier>apis</classifier>
        <scope>provided</scope>
    </dependency>
    ```

If your code also depends on deprecated APIs, add the following:

    ```xml
    <dependency>
        <groupId>com.adobe.aem</groupId>
        <artifactId>uber-jar</artifactId>
        <version>6.6.3</version>
        <classifier>deprecated-apis</classifier>
        <scope>provided</scope>
    </dependency>
    ```

See also [Update the AEM Uber Jar version](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Upgrade {#upgrade}

* For details about the upgrade procedure, see the [upgrade documentation](/help/sites-deploying/upgrade.md).
* For detailed upgrade instructions, see the [Upgrade Guide for AEM Forms 6.5 LTS SP1 on JEE](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

## Best practices for AEM 6.5 LTS Service Pack upgrades

<!-- THE INFORMATION UNDER THIS HEADING CAME FROM CQDOC-23078 -->

Applies to: AEM 6.5 LTS (On-Premise) customers installing Service Pack 3 (SP3). SP3 is delivered as a Quickstart JAR.

**Why this upgrade practice matters**
SP2 for AEM 6.5 LTS ships as a Quickstart JAR rather than a ZIP to install through Package Manager. On-premise customers upgrade by replacing the Quickstart JAR, unpacking it, and restarting. This method is consistent with Adobe's standard upgrade procedure.


**Recommended upgrade flow (Author or Publish)**

1. Verify that your AEM 6.5 LTS instance is healthy and accessible.
1. Download the Quickstart JAR (for example, `cq-quickstart-6.6.x.jar`) from Software Distribution. 
1. Stop the running instance. 
1. In the AEM install directory (outside `crx-quickstart/`), replace the previous Quickstart JAR with the SP3 JAR.
1. Unpack the JAR:

        ```java
        java -jar cq-quickstart-6.6.x.jar -unpack
        ```

    (Adjust heap flags as needed.)

1. Rename the unpacked JAR to match the role and port, for example `cq-author-4502.jar` or `cq-publish-4503.jar`.
1. Start AEM and confirm the upgrade in the UI (Help > About) and logs.

**Best practices**

* Run the upgrade in lower / test environments before production.
* Take a full, restorable backup (repository plus any external datastores) before you begin.
* Review Adobe's in-place upgrade guidance and technical requirements (Java 17/21 recommended for LTS).

>[!NOTE]
>
>File names shown above (for example, `cq-quickstart-6.6.x.jar`) reflect the Quickstart artifact naming observed for this LTS release; always use the exact file name you download from Software Distribution. 

## Install and update{#install-update}

For setup requirements, see [installation instructions](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> If you are directly upgrading to LTS SP1 from old 6.5 SPs, follow the instructions given for 6.5 to 6.5 LTS GA [upgrade](/help/sites-deploying/upgrade.md).


For detailed instructions, see the [upgrade documentation](/help/sites-deploying/upgrade.md), as the same documentation applies for LTS Service Pack updates.

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

Adobe continually reviews and evolves product capabilities to deliver greater customer value by modernizing or replacing legacy features. These changes are implemented with careful consideration for backward compatibility.

To ensure transparency and allow adequate planning, Adobe follows this deprecation process for Adobe Experience Manager (AEM):

* Deprecation is announced first. Deprecated capabilities remain available but are no longer enhanced.
* Removal occurs no earlier than the next major release. The planned removal timeline is communicated separately.
* A minimum of one release cycle is provided for customers to transition to supported alternatives before a capability is removed.

### Deprecated features {#deprecated-features}

This section lists features and capabilities that Adobe has deprecated in AEM 6.5 LTS. Typically, Adobe deprecates features before removing them in a future release and provides an alternative.

Customers are advised to review whether they use the feature / capability in their current deployment. Make plans to change your implementation to use the alternative provided.

| Area | Feature | Replacement | Version (SP) |
| --- | --- | --- | --- |
| Sites | Content Fragment text summarization | No replacement available. | |
| Quickstart | Mongo APIs | Mongo APIs are now deprecated and are planned for removal in future releases. | 6.5 TS SP2 |
| Sites | Content Fragment support in the AEM Assets REST API | AEM 6.5 LTS SP2 provides modern OpenAPIs for Content Fragment and Model Management, so the older Content Fragment Support endpoints in the AEM Assets REST API are now deprecated.<br>Adobe intends to keep these older endpoints available until an end-of-life announcement. Adobe does not plan further enhancements for the deprecated endpoints. |  6.5 LTS SP2 |
| Sites | [SPA Editor](/help/sites-developing/spa-overview.md) | The preferred editors for managing headless content in AEM are:<br>- [The Universal Editor](/help/sites-developing/universal-editor/introduction.md) for visual editing.<br>- [The Content Fragment Editor](/help/assets/content-fragments/content-fragments-managing.md) for form-based editing. | 6.5 LTS GA |
| [!DNL Foundation] | Support for com.adobe.granite.oauth.server | Adobe IMS Integration | |

### Removed features {#removed-features}

This section lists features and capabilities that have been removed from AEM 6.5 LTS. Prior releases had these capabilities marked as deprecated.

* Support for RDBMK for Adobe CRX repository persistence has been removed.
* In clustered environments, MongoMK is now the only supported option for repository persistence.

| Area | Feature | Replacement | Version (SP) |
| --- | --- | --- | --- |
| Commerce| AEM CIF Classic is not supported. | Migrate to [AEM CIF](/help/commerce/cif/migration.md). | 6.5 LTS GA |
| Solutions| Social / Communities is not supported. | No replacement available. | 6.5 LTS GA |
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

### AEM Forms

* In Configuration Manager, Database Initialization fails during Bootstrap in AEM Forms 6.5 LTS JEE Turnkey Custom mode when no modules or only limited components are selected. The failure is due to a missing dependency (xalan-2.7.2.jar), resulting in an error. Adding the JAR file to Adobe-livecycle-jboss.ear\lib resolves the issue. (FORMS-24690)
* On Forms JEE LTS Service Pack 2 deployments running on WebSphere&reg; Liberty Profile, email functionality fails. When attempting to use email features, the server logs an error: `Could not convert socket to TLS`. (FORMS-24692)
* On Forms JEE LTS running on JBoss&reg;, email-related functionality fails. When attempting to use email features, the server logs an error: `Error IMAPProvider not a subtype`. To resolve this issue, install the hotfix from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/adobe-core-jboss.ear). (FORMS-24892)

### Repository corruption during online compaction after offline compaction (GRANITE-65146) {#repository-corruption-during-online-compaction-after-offline-compaction-granite-65146}

Users can experience repository corruption during online compaction if offline compaction was previously run on the JCR repository. A `SegmentNotFoundException` (SNFE) can occur in this scenario and can lead to repository corruption.

To resolve the issue, install the Hotfix from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-65388-1.0.zip). Because the hotfix includes a low-level `oak-segment-tar` bundle, the instance restarts after installation.

Plan for the downtime of the instance when applying it. For offline compaction, use the corresponding [`oak-run` jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar), also available on Software Distribution.

>[!NOTE]
>
> * For any `oak-run` operations, use the [`oak-run` 1.88.1-B006 jar](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/oak-run-1.88.1-B006.jar).
>
> * Start AEM by setting the system property `oak.compaction.legacy=true`.

### Missing `com.adobe.granite.apicontroller` bundle in AEM 6.5 LTS SP2 (GRANITE-67640) {#missing-apicontroller-bundle-granite-67640}

The `com.adobe.granite.apicontroller` bundle is missing in AEM 6.5 LTS SP2. This bundle controls how OSGi bundles are resolved and can prevent bundles from resolving to other bundles, which is useful for limiting exposed APIs.

To use this functionality, install the hotfix from [Software Distribution](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.2-hotfix-GRANITE-67640-1.0.zip).

>[!NOTE]
>
> To ensure that the default configuration of `com.adobe.granite.apicontroller` introduces no unintended resolution restrictions that affect existing custom implementations, verify the bundle status of all installed bundles after installing the hotfix.

### JSON comments no longer supported in Sling-Initial-Content (SP2) {#json-comments-no-longer-supported-in-sling-initial-content}

This issue affects OSGi bundle developers and administrators who deploy bundles that use `Sling-Initial-Content` with JSON files.

Starting with AEM 6.5 LTS SP2, JSON files used in `Sling-Initial-Content` bundles no longer accept comments (`//` or `/* */`). Earlier AEM releases accepted comments because the `javax.json` provider was lenient about this. AEM 6.5 LTS SP2 upgraded `org.apache.sling.jcr.contentloader` to version 2.6.0, which switched the JSON parser to `jakarta.json`. While the [JSON specification (RFC 8259)](https://datatracker.ietf.org/doc/html/rfc8259) does not define syntax for comments, earlier AEM releases accepted them due to the leniency of the `javax.json` provider. The `jakarta.json` provider does not offer this extension.

The failure is silent: content nodes fail to load at bundle activation with no error surfaced to the installer. If content is unexpectedly missing after upgrading to SP2, check the OSGi installer logs for JSON parsing errors. To identify affected bundles, search for `//` or `/* */` inside JSON files listed under `Sling-Initial-Content` manifest headers.

>[!CAUTION]
>
> To avoid content loading failures after upgrading to AEM 6.5 LTS SP2, remove all comments from JSON files in your `Sling-Initial-Content` bundles.

### Install required Oak indexes for Sites Headless APIs{#site-headless-api}

Some APIs that moved to Sites Headless require additional Oak indexes for full functionality.

To use the following features, install the `cq-dam-cfm-indices` package:

* List Content Fragment Models
* List Content Fragments
* Search API
* Workflows

Download the index package [cq-dam-cfm-indices](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fcq-dam-cfm-indices-1.1.5.zip) from the Adobe Software Distribution portal. 

### Dispatcher connection failure with SSL-only feature (Fixed in AEM 6.5 LTS SP1 and later){#ssl-only-feature}

>[!NOTE]
>
> This issue is only present in the AEM 6.5 LTS GA release.

When enabling the SSL-only feature in AEM deployments, there is a known issue that affects connectivity between the Dispatcher and AEM instances. After enabling this feature, health checks fail and communication between Dispatcher and AEM instances is disrupted. This issue specifically occurs when customers attempt to connect through `https + IP` from the Dispatcher to AEM instances. It is related to SNI (Server Name Indication) validation problems.

**Impact**

* Health check failures with HTTP 400 response codes.
* Broken traffic between Dispatcher and AEM instances.
* Content cannot be properly served through the Dispatcher.
* Connection failures when using HTTPS with IP addresses in Dispatcher configuration.
* HTTP 400 "Invalid SNI" errors when connecting via HTTPS + IP.

**Affected environments**

* AEM deployments with Dispatcher configurations.
* Systems where the SSL-only feature has been enabled.
* Dispatcher configurations using `https + IP` connection method to AEM instances. 

**Solution**

If you experience this issue, contact Adobe Customer Support. A hotfix [cq-6.5.lts.0-hotfix-CQ-4359803](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) is available to resolve this problem. Do not attempt to enable SSL-only features until applying the necessary hotfix.

## OSGi bundles and content packages included{#osgi-bundles-and-content-packages-included}

The following zip files contain the text documents that list the OSGi bundles and content packages included in this Experience Manager 6.5 LTS Service Pack release:

* [OSGi bundles](/help/release-notes/assets/65lts_sp2_bundles.zip) 
* [Content packages](/help/release-notes/assets/65lts_sp2_packages.zip)

## Restricted websites{#restricted-sites}

These websites are only available to customers. If you are a customer and need access, contact your Adobe account manager.

* [Product download at licensing.adobe.com](https://licensing.adobe.com/)
* [Contact Adobe Customer Support](https://experienceleague.adobe.com/en/docs/support-resources/adobe-support-tools-guide/adobe-customer-support-experience).
 
