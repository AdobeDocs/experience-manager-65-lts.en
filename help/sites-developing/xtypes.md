---
title: Use xtypes (Classic UI)
description: Learn about all the xtypes that are available with Adobe Experience Manager
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4a78de53-33bf-4999-ba3c-7d0bc33196a4
---
# Use xtypes (Classic UI){#using-xtypes-classic-ui}

This page describes all the xtypes that are available with Adobe Experience Manager (AEM).

In the ExtJS language, an xtype is a symbolic name given to a class. You can read the "Component XTypes" paragraph of the [Overview of ExtJS 2](https://docs.sencha.com/) for a detailed explanation about what an xtype is and how it can be used.

For more information on all the available widgets in AEM, see the [widget API documentation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

To find out in which components a given xtype is used in AEM, you can use the following `Xpath` query in CRXDE. Just replace 'checkbox' with the xtype that you are interested in:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>This page describes the usage of ExtJS xtypes within the classic UI.
>
>Adobe recommends that you use the standard, modern, [touch-enabled UI](/help/sites-developing/touch-ui-concepts.md) based on [Coral UI](/help/sites-developing/touch-ui-concepts.md#coral-ui) and [Granite UI](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Listed below are the available xtypes in Adobe Experience Manager:

* `annotation`

  [CQ.wcm.Annotation](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Annotation` is a special window. It has a form in its body and a button group in its footer. It is typically used to edit content, but can also display information only.

* `arraystore`

  [CQ.Ext.data.ArrayStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Formerly known as `SimpleStore`.

  A small helper class to make creating [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s from Array data easier. An `ArrayStore` is automatically configured with a [CQ.Ext.data.ArrayReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `asseteditor`

  [CQ.dam.AssetEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Asset Editor` is used in DAM Admin.

* `assetreferencesearchdialog`

  [CQ.wcm.AssetReferenceSearchDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `AssetReferenceSearchDialog` is a dialog box that pops up in case a page references assets or tags.

* `blueprintconfig`

  [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `BlueprintConfig` provides a panel to view the Live Copies of a Blueprint and edit this Blueprint properties ( sync trigger and sync actions ).

* `blueprintstatus`

  [CQ.wcm.msm.BlueprintStatus](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The BlueprintStatus provides a panel to view and edit a Blueprint and its Live Copies relationships. Browsing is done through a [CQ.wcm.msm.BlueprintStatus.Tree](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), edition through a [CQ.wcm.msm.BlueprintConfig](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) and a [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `box`

  [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Base class for any [Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) that is to be sized as a box, using width and height.

  BoxComponent provides automatic box model adjustments for sizing and positioning and works correctly within the Component rendering model.

* `browsedialog`

  [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The BrowseDialog lets the user browse the repository to select a path. It is typically used through a [BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `browsefield`

  [CQ.form.BrowseField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Deprecated: Use [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) instead**

* `bulkeditor`

  [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `BulkEditor` provides a search engine and a grid to edit search results.

  The `BulkEditor` must be inserted in an HTML form (required by import functionality). This works perfectly with a [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `bulkeditorform`

  [CQ.wcm.BulkEditorForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The BulkEditorForm provides [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) surrounded by an HTML form. The standalone version of the [CQ.wcm.BulkEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). An HTML form is required for import button.

* `button`

  [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Simple Button class

* `buttongroup`

  [CQ.Ext.ButtonGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Container for a group of buttons.

* `chart`

  [CQ.Ext.chart.Chart](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The CQ.Ext.chart package provides the capability to visualize data with flash-based charting. Each chart binds directly to an CQ.Ext.data.Store enabling automatic updates of the chart. To change the look and feel of a chart, see the [chartStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) and [extraStyle](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config options.

* `checkbox`

  [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Single checkbox field. Can be used as a direct replacement for traditional checkbox fields.

* `checkboxgroup`

  [CQ.Ext.form.CheckboxGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A grouping container for [CQ.Ext.form.Checkbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) controls.

* `clearcombo`

  [CQ.form.ClearableComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The ClearableComboBox is a non-editable combo box with a trigger to clear its value.

* `colorfield`

  [CQ.form.ColorField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The ColorField lets the user enter a color hex value either directly or using a [CQ.Ext.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `colorlist`

  [CQ.form.ColorList](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The ColorList lets the user choose a color from an editable list.

* `colormenu`

  [CQ.Ext.menu.ColorMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A menu containing a [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Component.

* `colorpalette`

  [CQ.Ext.ColorPalette](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Simple color palette class for choosing colors. The palette can be rendered to any container.

* `combo`

  [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A combobox control with support for autocomplete, remote-loading, paging, and many other features.

  A ComboBox works in a similar manner to a traditional HTML &lt;select&gt; field. The difference is that to submit the [valueField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), you must specify a [hiddenName](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) to create a hidden input.

* `component`

  [CQ.Ext.Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Base class for all `Ext` components. All subclasses of Component may participate in the automated `Ext` component lifecycle of creation, rendering, and destruction which is provided by the [Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) class. Components may be added to a Container through the [items](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config option at the time the Container is created.

* `componentextractor`

  [CQ.wcm.ComponentExtractor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The ComponentExtractor lets the user extract components from a website/page.

* `componentselector`

  [CQ.form.ComponentSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A grouped, ordered selection of available Components.

* `componentstyles`

  [CQ.form.ComponentStyles](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `compositefield`

  [CQ.form.CompositeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Base class for panel based, complex form fields which include one form field or a group of form fields.

* `container`

  [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Base class for any [CQ.Ext.BoxComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) that may contain other Components. Containers handle the basic behavior of containing items, namely adding, inserting, and removing items.

  The most commonly used Container classes are [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), and [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `contentfinder`

  [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The ContentFinder is a specialized two-column [Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) which contains the actual Content Finder on the left and the Content Frame on the right.

* `contentfindertab`

  [CQ.wcm.ContentFinderTab](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinderTab is a specialized panel providing features used in the tab panels of the [CQ.wcm.ContentFinder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Typically, it features a search form - the Query Box - and a data view to display the search.

* `cq.workflow.model.combo`

  [CQ.wcm.WorkflowModelCombo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The WorkflowModelCombo is a customized [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) that shows a list of available workflow models.

* `cq.workflow.model.selector`

  [CQ.wcm.WorkflowModelSelector](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The WorkflowModelSelector combines a WorkflowModelCombo with a thumbnail image of the workflow, and buttons to create and edit workflow models.

* `createsitewizard`

  [CQ.wcm.CreateSiteWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The CreateSiteWizard is a step-by-step wizard to create (MSM) sites.

* `createversiondialog`

  [CQ.wcm.CreateVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The CreateVersionDialog is a dialog box that allows creating a version of a page.

* `customcontentpanel`

  [CQ.CustomContentPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The CustomContentPanel is a special panel for use in [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html): Its contents are retrieved from and submitted to a different URL than the other fields in the dialog box.

* `cycle`

  [CQ.Ext.CycleButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A specialized SplitButton that contains a menu of [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) elements. The button automatically cycles through each menu item on each click, raising the button's [change](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) event (or calling the button's [changeHandler](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) function, if supplied) for the active menu item.

* `dataview`

  [CQ.Ext.DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A mechanism for displaying data using custom layout templates and formatting. DataView uses an [CQ.Ext.XTemplate](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) as its internal templating mechanism, and is bound to an [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) so that as the data in the store changes the view is automatically updated to reflect the changes.

* `datefield`

  [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It provides a date input field with a [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) drop-down and automatic date validation.

* `datemenu`

  [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A menu containing an [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Component.

* `datepicker`

  [CQ.Ext.DatePicker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A pop-up date picker. This class is used by the [DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) class to allow browsing and selection of valid dates.

* `datetime`

  [CQ.form.DateTime](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The DateTime lets the user enter a date and a time by combining [CQ.Ext.form.DateField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) and [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `dialog`

  [CQ.Dialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The Dialog is a special window. It has a form in its body and a button group in its footer. It is typically used to edit content, but can also display information only.

* `dialogfieldset`

  [CQ.form.DialogFieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The DialogFieldSet is a [FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for use in [Dialogs](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `directstore`

  [CQ.Ext.data.DirectStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A small helper class to create an [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) configured with an [CQ.Ext.data.DirectProxy](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) and [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) to make interacting with an [CQ.Ext.Direct](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Server-side [Provider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) easier.

* `displayfield`

  [CQ.Ext.form.DisplayField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A display-only text field which is not validated and not submitted.

* `editbar`

  [CQ.wcm.EditBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The EditBar lets the user edit content using buttons on a bar.

  Although not listed here, EditBar has all the members of [CQ.wcm.EditBase](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editor`

  [CQ.Ext.Editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A base editor field that handles displaying/hiding on demand and has some built-in sizing and event handling logic.

* `editorgrid`

  [CQ.Ext.grid.EditorGridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  This class extends the [GridPanel Class](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) to provide cell editing on selected [columns](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). The editable columns are specified by providing an [editor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in the [column configuration](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editrollover`

  [CQ.wcm.EditRollover](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The EditRollover lets the user edit content through double-click and provides more editing actions through a context menu. The editable area is indicated with a frame when the mouse is rolling over the content.

* `feedimporter`

  [CQ.wcm.FeedImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The FeedImporter lets the user import RSS or Atom feeds and create pages for each feed entry.

* `field`

  [CQ.Ext.form.Field](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Base class for form fields that provides default event handling, sizing, value handling and other functionality.

* `fieldset`

  [CQ.Ext.form.FieldSet](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Standard container used for grouping items within a [form](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `fileuploaddialogbutton`

  [CQ.form.FileUploadDialogButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The FileUploadDialogButton creates a button that opens a new dialog box for uploading a file via the FileUploadField. Can be used inside edit dialog boxes where the upload must happen in a separate form.

* `fileuploadfield`

  [CQ.form.FileUploadField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The FileUploadField lets the user select a single file to be uploaded.

* `findreplacedialog`

  [CQ.wcm.FindReplaceDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The FindReplaceDialog is a dialog box for finding and replacing tokens in a page and its child pages.

* `flash`

  [CQ.Ext.FlashComponent](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `grid`

  [CQ.Ext.grid.GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  This class represents the primary interface of a component-based grid control to represent data in a tabular format of rows and columns.

* `groupingstore`

  [CQ.Ext.data.GroupingStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A specialized store implementation that provides for grouping records by one of the available fields. Used with an [CQ.Ext.grid.GroupingView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) to prove the data model for a grouped GridPanel.

* `heavymovedialog`

  [CQ.wcm.HeavyMoveDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The HeavyMoveDialog is a dialog box for moving a page and its child pages, also considering reactivation of previously activated pages ('heavy' move).

* `hidden`

  [CQ.Ext.form.Hidden](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A basic hidden field for storing hidden values in forms that must be passed in the form submit.

* `historybutton`

  [CQ.HistoryButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The HistoryButton is a small helper class to provide back and forward buttons easily. Usually two related instances are required: The forward button instance is a simple button linked to the back button instance which handles the history.

* `htmleditor`

  [CQ.Ext.form.HtmlEditor](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It provides a lightweight HTML Editor component. Safari does not support some toolbar features, so the system automatically hides them when needed. Noted in the config options where appropriate.

  The editor's toolbar buttons have tooltips defined in the [buttonTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) property.

* `iframedialog`

  [CQ.IframeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A plain dialog box showing the contents of an iframe and allowing for forms in iframes.

* `iframepanel`

  [CQ.IframePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A panel containing an iframe. It provides easy creation of iframes, an iframe load event, and easy access to the iframe's contents.

* `inlinetextfield`

  [CQ.form.InlineTextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The InlineField is a text field which is displayed as a label when not in focus.

* `jsonstore`

  [CQ.Ext.data.JsonStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A small helper class to make creating [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s from JSON data easier. A JsonStore is automatically configured with a [CQ.Ext.data.JsonReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `label`

  [CQ.Ext.form.Label](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basic Label field.

* `languagecopydialog`

  [CQ.wcm.LanguageCopyDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The LanguageCopyDialog is a dialog box for copying language trees.

* `linkchecker`

  [CQ.wcm.LinkChecker](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The LinkChecker is a tool to check external links in a site.

* `listview`

  [CQ.Ext.list.ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CQ.Ext.list.ListView is a fast and light-weight implementation of a [Grid-like](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) view.

* `livecopyproperties`

  [CQ.wcm.msm.LiveCopyProperties](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The LiveCopyProperties provides a panel to view and edit Live Copy properties ( relationship inheritance, sync trigger, and sync actions ).

* `lvbooleancolumn`

  [CQ.Ext.list.BooleanColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A Column definition class which renders boolean data fields. See the [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config option of [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for more details.

* `lvcolumn`

  [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  This class encapsulates column configuration data to be used in the initialization of a [ListView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvdatecolumn`

  [CQ.Ext.list.DateColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A Column definition class which renders a passed date according to the default locale, or a configured [format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). See the [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config option of [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for more details.

* `lvnumbercolumn`

  [CQ.Ext.list.NumberColumn](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A Column definition class which renders a numeric data field according to a [format](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) string. See the [xtype](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config option of [CQ.Ext.list.Column](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for more details.

* `mediabrowsedialog`

  [CQ.MediaBrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Deprecated: Use [Content Finder](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) to browse media instead.**

  The MediaBrowseDialog is a dialog box for browsing the media library.

* `menu`

  [CQ.Ext.menu.Menu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A menu object. The container to which you can add menu items. Menu can also serve as a base class when you want a specialized menu based off of another component (like [CQ.Ext.menu.DateMenu](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for example).

  Menus can contain either [menu items](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), or general [Component](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s.

* `menubaseitem`

  [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The base class for all items that render into menus. BaseItem provides default rendering, activated state management, and base configuration options shared by all menu components.

* `menucheckitem`

  [CQ.Ext.menu.CheckItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It adds a menu item that contains a checkbox by default, but can also be part of a radio group.

* `menuitem`

  [CQ.Ext.menu.Item](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A base class for all menu items that require menu-related functionality (like submenus) and are not static display items. Item extends the base functionality of [CQ.Ext.menu.BaseItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) by adding menu-specific activation and click handling.

* `menuseparator`

  [CQ.Ext.menu.Separator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It adds a separator bar to a menu, used to divide logical groups of menu items. Generally, you add one it by using "-" in your call to add() or in your items config rather than creating one directly.

* `menutextitem`

  [CQ.Ext.menu.TextItem](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It adds a static text string to a menu, used as either a heading or group separator.

* `metadata`

  [CQ.dam.form.Metadata](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Metadata` provides a set of fields to determine the information required for a metadata field as used, for example, on Asset Editor pages.

  It provides the following fields:

* `multifield`

  [CQ.form.MultiField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `MultiField` is an editable list of form fields for editing multi-value properties.

* `mvt`

  [CQ.form.MVT](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The Multivariate Testing component can be used to define and edit a set of images that are presented as alternating banners. Click through rate statistics are gathered per banner.

* `notificationinbox`

  [CQ.wcm.NotificationInbox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `NotificationInbox` allows the user to subscribe to WCM actions and manage notifications.

* `numberfield`

  [CQ.Ext.form.NumberField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Numeric text field that provides automatic keystroke filtering and numeric validation.

* `offlineimporter`

  [CQ.wcm.OfflineImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `OfflineImporter` is a tool to import and convert Microsoft&reg; Word documents to AEM pages. This feature allows content to be edited offline using a word processor.

* `ownerdraw`

  [CQ.form.OwnerDraw](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `OwnerDraw` can contain custom HTML code (either entered directly or retrieved from a URL).

* `paging`

  [CQ.Ext.PagingToolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  As the number of records increases, the time required for the browser to render them increases. Paging is used to reduce the amount of data exchanged with the client.

* `panel`

  [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A `panel` is a container that has specific functionality and structural components that make it the perfect building block for application-oriented user interfaces.

  Panels, by virtue of their inheritance, are from [CQ.Ext.Container](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `paragraphreference`

  [CQ.form.ParagraphReference](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The paragraph reference field lets you browse pages and select one of their paragraphs. It consists of a trigger field and an associated paragraph browse dialog box.

* `password`

  [CQ.form.Password](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Password` is like a [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) but keeps its value private, allowing users to enter sensitive data.

* `pathcompletion`

  [CQ.form.PathCompletion](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Deprecated: Use [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) instead**

* `pathfield`

  [CQ.form.PathField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `PathField` is an input field designed for paths with path completion and a button to open a [CQ.BrowseDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for browsing the server repository. It can also browse page paragraphs for advanced link generation.

* `progress`

  [CQ.Ext.ProgressBar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  An updateable progress bar component. The progress bar supports two different modes: manual and automatic.

  In manual mode, you are responsible for showing, updating (via [updateProgress](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) and clearing the progress bar as needed from your own code. This method is most appropriate when you want to show progress.

* `propertygrid`

  [CQ.Ext.grid.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A specialized grid implementation intended to mimic the traditional property grid as typically seen in development IDEs. Each row in the grid represents a property of some object, and the data is stored as a set of name/value pairs in [CQ.Ext.grid.PropertyRecord](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s.

* `propgrid`

  [CQ.PropertyGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `PropertyGrid` is a generic grid used for displaying and editing properties of objects.

* `quicktip`

  [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `@xtype quicktip` - A specialized tooltip class for tooltips that can be specified in markup and automatically managed by the global [CQ.Ext.QuickTips](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) instance. See the QuickTips class header for additional usage details and examples.

* `radio`

  [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Single `radio` field. Same as Checkbox, but provided as a convenience for automatically setting the input type. The browser automatically groups radio buttons when each radio button in the group uses the same name.


* `radiogroup`

  [CQ.Ext.form.RadioGroup](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A grouping container for [CQ.Ext.form.Radio](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) controls.

* `referencesdialog`

  [CQ.wcm.ReferencesDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `ReferencesDialog` is a dialog box for displaying references on a page.

* `restoretreedialog`

  [CQ.wcm.RestoreTreeDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `RestoreTreeDialog` is a dialog box for restoring a previous version of a tree.

* `restoreversiondialog`

  [CQ.wcm.RestoreVersionDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The RestoreVersionDialog is a dialog box for restoring a previous version of a page.

* `richtext`

  [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `RichText` provides a form field for editing styled text information (rich text).

  The `RichText` component currently provides the following features:

* `rolloutplan`

  [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The RolloutPlan provides a dialog box to watch a page rollout progress. A [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) starts the RolloutPlan.

* `rolloutwizard`

  [CQ.wcm.msm.RolloutWizard](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `RolloutWizard` provides a wizard for rolling out a page. RolloutWizard starts a [CQ.wcm.msm.RolloutPlan](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `searchfield`

  [CQ.form.SearchField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `SearchField` provides a search field that provides the results in a drop-down list which can be used for searching the repository.

* `selection`

  [CQ.form.Selection](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Selection` lets the user choose between several options. The options can be part of the configuration or loaded from a JSON response. The Selection can either be rendered as drop-down (select), or a combobox (select plus free text entry).

* `sidekick`

  [CQ.wcm.Sidekick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Sidekick` is a floating helper providing the user with common tools for page editing.

* `siteadmin`

  [CQ.wcm.SiteAdmin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `SiteAdmin` is a console providing WCM administration functions.

* `siteimporter`

  [CQ.wcm.SiteImporter](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `SiteImporter` lets the user import complete websites and create initial projects.

* `sizefield`

  [CQ.form.SizeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `SizeField` lets the user enter the width and height (for example, for an image).

* `slider`

  [CQ.Ext.Slider](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Slider which supports vertical or horizontal orientation, keyboard adjustments, configurable snapping, axis clicking and animation. It can be added as an item to any container. For example, usage: ...

* `slideshow`

  [CQ.form.Slideshow](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The Slideshow component lets you define and edit a set of images and image titles. Users can view the set as a slideshow.

  The Slideshow component is based on the [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) component.

* `smartfile`

  [CQ.form.SmartFile](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The SmartFile is an intelligent file uploader.

  If a Flash plugin (version &gt;= 9) is installed, uploads are executed using the SWFupload library that provides a convenient way to handle uploads.

* `smartimage`

  [CQ.form.SmartImage](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The SmartImage is an intelligent image uploader. It provides tools to process an uploaded image, for example, a tool to define image maps and an image cropper.

  The component is designed for use in a separate dialog box tab.

* `spacer`

  [CQ.Ext.Spacer](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Used to provide a sizable space in a layout.

* `spinner`

  [CQ.form.Spinner](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Spinner` is a trigger field for numeric, date, or time values. The value can be increased and decreased by using the provided up and down triggers, the scrolling wheel, or keys.

* `splitbutton`

  [CQ.Ext.SplitButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A `splitbutton` that provides a built-in drop-down arrow that can fire an event separately from the default click event of the button. Typically, it is used to display a drop-down menu that provides additional options to the primary button action, but any custom handler can provide the `arrowclick` implementation.

* `static`

  [CQ.Static](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Static` can be used to display arbitrary text or HTML.

* `statistics`

  [CQ.wcm.Statistics](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Statistics` displays the page impressions as a chart. The widget lets you select a period for which the statistics should be displayed.

* `store`

  [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Store` class encapsulates a client-side cache of [Record](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) objects which provide input data for Components such as the [GridPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), the [ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), or the [DataView](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `suggestfield`

  [CQ.form.SuggestField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `SuggestField` provides the user with suggestions based on their entry.

* `switcher`

  [CQ.Switcher](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `Switcher` provides a button group for the header bar in a console to switch between Websites, Digital Assets, Tools, Workflow, and Security.

* `tableedit`

  [CQ.form.TableEdit](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Deprecated: Use [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) instead.**

* `tableedit2`

  [CQ.form.TableEdit2](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `TableEdit2` provides a widget for creating tables.

* `tabpanel`

  [CQ.Ext.TabPanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A basic tab container. TabPanels can be used exactly like a standard [CQ.Ext.Panel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for layout purposes, but also have special support for containing child Components ([`items`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `tags`

  [CQ.tagging.TagInputField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ```
  CQ.tagging.TagInputField
  ```

  is a form widget for entering tags. It has a pop-up menu for selecting from existing tags, includes auto-completion and many other features.

* `textarea`

  [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Multiline text field. Can be used as a direct replacement for traditional `textarea` fields, plus adds support for auto-sizing.

* `textbutton`

  [CQ.TextButton](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `TextButton` provides a text link with the capabilities of a [CQ.Ext.Button](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `textfield`

  [CQ.Ext.form.TextField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basic text field. Can be used as a direct replacement for traditional text inputs, or as the base class for more sophisticated input controls (like [CQ.Ext.form.TextArea](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) and [CQ.Ext.form.ComboBox](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `thumbnail`

  [CQ.form.Thumbnail](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `timefield`

  [CQ.Ext.form.TimeField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It provides a time input field with a time drop-down and automatic time validation. Example usage: ...

* `tip`

  [CQ.Ext.Tip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype tip This is the base class for [CQ.Ext.QuickTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) and [CQ.Ext.Tooltip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) that provides the basic layout and positioning that all tip-based classes require. This class can be used directly for simple, statically positioned tips.

* `titleseparator`

  [CQ.menu.TitleSeparator](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It adds a separator bar to a menu, used to divide logical groups of menu items. The separator can also carry a title.

* `toolbar`

  [CQ.Ext.Toolbar](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basic `Toolbar` class. Although the [`defaultType`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) for Toolbar is [`button`](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), Toolbar elements (child items for the Toolbar container) can be virtually any type of Component. Toolbar elements can be created explicitly via their constructors.

* `tooltip`

  [CQ.Ext.ToolTip](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A standard `tooltip` implementation for providing additional information when hovering over a target element. @xtype tooltip.

* `treegrid`

  [CQ.tree.TreeGrid](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype `treegrid`

* `treepanel`

  [CQ.Ext.tree.TreePanel](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `TreePanel` provides tree-structured UI representation of tree-structured data.

  [TreeNode](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s added to the `TreePanel` can each contain metadata used by your application in their [attributes](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) property.

* `trigger`

  [CQ.Ext.form.TriggerField](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  It provides a convenient wrapper for `TextFields` that adds a clickable trigger button (looks like a combobox by default). The trigger has no default action, so you must assign a function to implement the trigger click handler by overriding [onTriggerClick](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). You can create a `TriggerField` directly, as it renders exactly like a combobox.

* `uploaddialog`

  [CQ.UploadDialog](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  The `UploadDialog` lets the user upload files to the repository Creates a new UploadDialog.

* `userinfo`

  [CQ.UserInfo](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Toolbar item to display the current user name and allow user actions like editing user properties and impersonation.

* `viewport`

  [CQ.Ext.Viewport](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A specialized container representing the viewable application area (the browser viewport).

  The `Viewport` renders itself to the document body, and automatically sizes itself to the size of the browser viewport and manages window resizing. There may only be one Viewport created.

* `window`

  [CQ.Ext.Window](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A specialized panel intended for use as an application window. Windows are floated, [resizable](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), and [draggable](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) by default. Windows can be [maximized](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) to fill the viewport, restored to their prior size, and can be [minimize](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)d.

* `xmlstore`

  [CQ.Ext.data.XmlStore](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A small helper class to make creating [CQ.Ext.data.Store](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)s from XML data easier. An `XmlStore` is automatically configured with a [CQ.Ext.data.XmlReader](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

  `cqinclude` - A pseudo xtype that includes widget definitions from a different path in the repository. It is most commonly used in page dialog boxes. There is no actual JavaScript widget class for this xtype. The `CQ.Util` class processes it by using the `formatData()` function.
