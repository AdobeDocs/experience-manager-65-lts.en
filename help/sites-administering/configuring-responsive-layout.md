---
title: Configuring Layout Container and Layout Mode
description: Learn how to configure Layout Container and Layout Mode.
topic-tags: operations
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
exl-id: 413f15c9-5b51-4d8d-8cf0-3e98608b9d9e
---
# Configuring Layout Container and Layout Mode{#configuring-layout-container-and-layout-mode}

Learn how to configure Layout Container and Layout Mode.

>[!TIP]
>
>This document provides an overview of responsive design for site administrators and developers describing how features are realized in AEM.
>
>For content authors, details of how to use responsive design features on a content page are available in the document [Responsive layout for your content pages.](/help/sites-authoring/responsive-layout.md)

## Overview {#overview}

[Responsive Layout](/help/sites-authoring/responsive-layout.md) is a mechanism for realizing [responsive web design](https://en.wikipedia.org/wiki/Responsive_web_design). This allows the user to create web pages that have a layout and dimensions dependent on the devices their users use.

AEM realizes responsive layout for your pages using a combination of mechanisms:

* [**Layout Container**](/help/sites-authoring/responsive-layout.md#adding-a-layout-container-and-its-content-edit-mode) component

  This component provides a grid-paragraph system to let you add and position components within a responsive grid. It can be used as the default parsys for your page and/or made available to authors in the component browser.

    * The default **Layout Container** component is defined under:

      /libs/wcm/foundation/components/responsivegrid

    * You can define layout containers:

        * As a component that the user can add to a page.
        * As the default parsys for the page.
        * Both.

          You can have the layout container as standard for the page, while allowing the user to add further layout containers within this; for example, to achieve column control.

* **[Layout Mode](/help/sites-authoring/responsive-layout.md#defining-layouts-layout-mode)**
  Once the layout container is positioned on your page you can use the **Layout** mode to position content within the responsive grid.

* [**Emulator**](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate)
  This lets you create and edit responsive websites that rearrange the layout according to device/window size by resizing components interactively. The user can then see how the content is rendered using the Emulator.

With these responsive grid mechanisms you can:

* Use breakpoints (that indicate device grouping) to define differing content behavior based on device layout.
* Hide components based on device group (define on which breakpoint a component will be hidden).
* Use horizontal snap to grid (place components into the grid, resize as required, define when they should collapse/reflow to be side-by-side or above/below).
* Realize column control.

>[!TIP]
>
>Adobe provides [GitHub documentation](https://adobe-marketing-cloud.github.io/aem-responsivegrid/) of the responsive layout as a reference that can be given to front-end developers allowing them to use the AEM grid outside of AEM, for example, when creating static HTML mock-ups for a future AEM site.

>[!NOTE]
>
>In an out-of-the-box installation, responsive layout has been configured for the [We.Retail reference site](/help/sites-developing/we-retail.md). [Activate the Layout Container component](#enable-the-layout-container-component-for-page) for other pages.

>[!CAUTION]
>
>Although the **Layout Container** component is available in the classic UI, its full functionality is only available in the touch-enabled UI.

## Activate Layout Mode for your Site {#activate-layout-mode-for-your-site}

These procedures are used to enable the **Layout** mode on your site.

### Configure the Breakpoints {#configure-the-breakpoints}

[Breakpoints](/help/sites-authoring/responsive-layout.md#selecting-a-device-to-emulate):

* Are used in responsive design.
* Can be defined:

    * On the page template, from where the settings are copied to any pages created with that template.
    * On the page node, from where the settings are inherited by any child pages.

* Define a title and a width:

    * The title describes the generic device grouping, with orientation if necessary; for example, phone, tablet, tabletlandscape.
    * The width defines the maximum width in pixels for that generic device grouping. For example, if the breakpoint phone has a width of 768 then that it the maximum width of the layout used for a phone device.

* Are visible as markers at the top of the page editor when you are using the emulator.
* Are inherited from the parent node hierarchy and can be overridden at will.
* There is a default (out-of-the-box) breakpoint which covers everything above the last *configured* breakpoint.

They can be defined using CRXDE Lite or XML.

>[!NOTE]
>
>If you are setting up a new project:
>
>* add breakpoints to the templates.
>
>If you are migrating an existing project (with existing content), you must:
>
>* add breakpoints to the templates
>* add the same breakpoints to the existing pages
>
>  As inheritance is in operation you can limit this to the root page of your content.

#### Configuring Breakpoints using CRXDE Lite {#configuring-breakpoints-using-crxde-lite}

1. Using CRXDE Lite (or equivalent), navigate to either:

    * Your template definition.
    * The `jcr:content` node of your page.

1. Under `jcr:content` create the node:

    * Name: `cq:responsive`
    * Type: `nt:unstructured`

1. Under this create the node:

    * Name: `breakpoints`
    * Type: `nt:unstructured`

1. Under the breakpoints node you can create any number of breakpoints. Each definition is a single node with the following properties:

    * Name: `<descriptive name>`
    * Type: `nt:unstructured`
    * Title: `String` * `<descriptive title seen in Emulator>`*
    * Width: `Decimal` * `<value of breakpoint>`*

#### Configuring Breakpoints using XML {#configuring-breakpoints-using-xml}

Breakpoints are located inside the `<jcr:content>` section of the `.context.html` under the appropriate template (or content) folder.

An example definition:

```xml
<cq:responsive jcr:primaryType="nt:unstructured">
  <breakpoints jcr:primaryType="nt:unstructured">
    <phone jcr:primaryType="nt:unstructured" title="{String}Phone" width="{Decimal}768"/>
    <tablet jcr:primaryType="nt:unstructured" title="{String}Tablet" width="{Decimal}1200"/>
  </breakpoints>
</cq:responsive>
```

### Add a Responsive Information Provider {#add-a-responsive-information-provider}

>[!NOTE]
>
>This is only needed if the page component is not based on the foundation page component.

Copy the following `cq:infoProviders` node structure into your parent page component:

`/libs/foundation/components/page/cq:infoProviders/responsive`

## Enable Component Resizing for the Page {#enable-component-resizing-for-the-page}

These procedures are required so you can resize components in the **Layout** mode.

### Set Layout Container as Main Parsys {#set-layout-container-as-main-parsys}

To set the main parsys of your page to be a layout container, define the parsys as:

`wcm/foundation/components/responsivegrid`

In either the:

* Page component
* Page template (for future use)

The following two examples illustrate the definition:

* **HTL:**

  ```html
  <sly data-sly-resource="${'par' @ resourceType='wcm/foundation/components/responsivegrid'}/>
  ```

* **JSP:**

  ```html
  <cq:include path="par" resourceType="wcm/foundation/components/responsivegrid" />
  ```

### Include the Responsive CSS {#include-the-responsive-css}

#### CSS for Breakpoints using LESS {#css-for-breakpoints-using-less}

AEM uses LESS to generate parts of the necessary CSS, these need to be included for your projects.

You will also must create a [client library](https://experienceleague.adobe.com/docs/) to provide additional configuration and function calls. The following LESS extract is an example of the minimum that you must add to your project:

```css
@import (once) "/libs/wcm/foundation/clientlibs/grid/grid_base.less";

/* maximum amount of grid cells to be provided */
@max_col: 12;

/* default breakpoint */
.aem-Grid {
  .generate-grid(default, @max_col);
}

/* phone breakpoint */
@media (max-width: 768px) {
  .aem-Grid {
    .generate-grid(phone, @max_col);
  }
}

/* tablet breakpoint */
@media (min-width: 769px) and (max-width: 1200px) {
  .aem-Grid {
    .generate-grid(tablet, @max_col);
  }
}
```

The base grid definition can be found under:

`/libs/wcm/foundation/clientlibs/grid/grid_base.less`

#### Styling Considerations {#styling-considerations}

Components held within a responsive container are resized (together with their respective HTML DOM elements) according to the responsive grid size. Therefore, in these circumstances, it is recommended to avoid (or update) definitions of fixed width (contained) DOM elements.

For example:

* Before:

    * `width=100px`

* After:

    * `max-width=100px`

#### Resizing and Adaptive Image Compliance {#resizing-and-adaptive-image-compliance}

Any resizing of a component within the grid will trigger the following listeners as appropriate:

* `beforeedit`
* `beforechildedit`
* `afteredit`

* `afterchildedit`

To properly resize and update the content of an adaptive image included in a responsive grid, you need to add an `afterEdit` set to `REFRESH_PAGE` listener into the `EditConfig` file of every contained component.

For example:

`<cq:listeners jcr:primaryType="cq:EditListenersConfig" afteredit="REFRESH_PAGE" />`

The adaptive image mechanism is made available via a script that controls selection of the correct image for the current size of the window. It activates after the DOM is ready or when receiving a dedicated event. Currently the page must be refreshed to properly reflect the result of the user's action.

>[!CAUTION]
>
>Custom stylesheet clientlibs must be loaded as part of the header for them to work properly on author and publish.

## Enable the Layout Container Component for Page {#enable-the-layout-container-component-for-page}

These tasks allow authors to drag instances of the **Layout Container** component onto the page.

### Enable the Layout Container Component for Page Editing {#enable-the-layout-container-component-for-page-editing}

To allow authors to add further responsive grids to the content pages you need to enable the Layout Container component for your page. You can do this using either:

* **Author Environment**

  Use [Design mode](/help/sites-authoring/default-components-designmode.md) to activate the **Layer Container** component for a page.

* **Component Definition**

  Use `allowedComponent` or a static include when defining the component.

### Configure the Grid of the Layout Container {#configure-the-grid-of-the-layout-container}

You can configure the number of columns available for each specific instance of layout container:

1. **Author Environment**

   You can configure the number of columns available for each specific instance of layout container.

   To do this, use [Design mode](/help/sites-authoring/default-components-designmode.md), then open the design dialog for the required container. Here you can specific how many columns will be available for positioning and sizing. The default is 12.

1. **XML**

   Definitions for the responsive grid are specified in:

   `etc/design/<*your-project-name*>/.content.xml`

   The following parameters can be defined:

    * Number of columns available:

        * `columns="{String}8"`

    * Components that can be added to the current component:

        * `components="[/libs/wcm/foundation/components/responsivegrid, ...`

## Nested Responsive Grids {#nested-responsive-grids}

There may be occasions when you find it necessary to nest responsive grids to support your project's needs. However, keep in mind that Adobe's recommended best practice is to keep the structure as flat as possible.

When you can not avoid using nested responsive grids, make sure:

* All containers (containers, tabs, accordions, etc.) have the property `layout = responsiveGrid`.
* Do not mix the property `layout = simple` in the container hierarchy. 

This includes all the structural containers from the page template.

The column number of the inner container should never be greater than that of the outer container. The following example satisfies this condition. While the column number of the outer container is 8 for the default (desktop) screen, the column number of the inner container is 4.

>[!BEGINTABS]

>[!TAB Example Node Structure]

```text
container
  @layout = responsiveGrid
  cq:responsive
    default
      @offset = 0
      @width = 8
  container
  @layout = responsiveGrid
    cq:responsive
      default
        @offset = 0
        @width = 4
    text
      @text =" Text Column 1"
```

>[!TAB Example Resulting HTML]

```html
<div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--default--8 aem-GridColumn--offset--default--0">
  <div id="container-c9955c233c" class="cmp-container">
    <div class="aem-Grid aem-Grid--8 aem-Grid--default--8 ">
      <div class="container responsivegrid aem-GridColumn--default--none aem-GridColumn aem-GridColumn--offset--default--0 aem-GridColumn--default--4">
        <div id="container-8414e95866" class="cmp-container">
          <div class="aem-Grid aem-Grid--4 aem-Grid--default--4 ">
            <div class="text aem-GridColumn aem-GridColumn--default--4">
              <div data-cmp-data-layer="..." id="text-1234567890" class="cmp-text">
                <p>Text Column 1</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

>[!ENDTABS]
