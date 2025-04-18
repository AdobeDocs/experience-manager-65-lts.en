---
title: Creating Content Fragment Models Headless Quick Start Guide
description: Define the structure of the content that you create and serve using Adobe Experience Manager's (AEM) headless capabilities by using Content Fragment Models.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
exl-id: 768a5d73-521f-47a5-b4a3-d1b0b77798f7
---
# Creating Content Fragment Models Headless Quick Start Guide {#creating-content-fragment-models}

Define the structure of the content that you create and serve using Adobe Experience Manager's (AEM) headless capabilities by using Content Fragment Models.

## What are Content Fragment Models? {#what-are-content-fragment-models}

[Now that you have created a configuration,](create-configuration.md) you can use it to create Content Fragment Models.

Content Fragment Models define the structure of the data and content that you create and manage in AEM. They serve as a kind of scaffolding for your content. When choosing to create content, your authors select from the Content Fragment Models you define, which guides them in creating content.

## How to Create a Content Fragment Model {#how-to-create-a-content-fragment-model}

An information architect would perform these tasks only sporadically as new models are required. For the purposes of this getting started guide, you are creating only one model.

1. Log into AEM and from the main menu select **Tools > Assets > Content Fragment Models**.
1. Click the folder that was made by creating your configuration.

   ![The models folder](assets/models-folder.png)
1. Click **Create**.
1. Provide a **Model Title**, **Tags**, and **Description**. You can also select/deselect **Enable model** to control whether the model is immediately enabled upon creation.

   ![Create a model](assets/models-create.png)
1. In the confirmation window, click **Open** to configure your model.

   ![Confirmation window](assets/models-confirmation.png)
1. Using the **Content Fragment Model Editor**, build your Content Fragment Model by dragging and dropping fields from the **Data Types** column.

   ![Drag and drop fields](assets/models-drag-and-drop.png)

1. Once you place a field, you must configure its properties. The editor automatically switches to the **Properties** tab for the added field where you can provide the mandatory fields.

   ![Configure properties](assets/models-configure-properties.png)
1. When you are finished building your model, click **Save**. 

1. The mode of the newly created model depends on whether you selected **Enable Model** when creating the model:
   * selected - the new model is already **Enabled**
   * not selected - the new model is created in **Draft** mode

1. If not already enabled, the model must be **Enabled** to use it. 
   1. Select the model that you created, and then click **Enable**.

      ![Enabling the model](assets/models-enable.png)
   1. Confirm enabling the model by tapping or clicking **Enable** in the confirmation dialog.

      ![Enabling confirmation dialog](assets/models-enabling.png)
1. The model is now enabled and ready to use.

   ![Model enabled](assets/models-enabled.png)

The **Content Fragment Model Editor** supports many different data types such as simple text fields, asset references, references to other models, and JSON data.

You can create multiple models. Models can reference other content fragments. Use [configurations](create-configuration.md) to organize your models.

## Next Steps {#next-steps}

Now that you have defined the structures of your Content Fragments by creating models, you can move on to the third part of the getting started guide and [create folders where you are storing the fragments.](create-assets-folder.md)

>[!TIP]
>
>For complete details about Content Fragment Models, see [Content Fragment Models documentation](/help/assets/content-fragments/content-fragments-models.md)
