---
title: Ask Copilot for data from your model
description: Learn how to use Copilot to visualize data from your semantic model.
author: julcsc
ms.author: juliacawthra
ms.reviewer: shlindsay, rien
ms.service: powerbi
ms.subservice: powerbi-ai
ms.topic: conceptual
ms.date: 05/23/2025
LocalizationGroup: Create reports
no-loc: [Copilot]
ms.collection: ce-skilling-ai-copilot
#customer intent: As a report creator, I want to learn how to use Copilot in Power BI to visualize data from my semantic model.
---

# Ask Copilot for data from your model

[!INCLUDE [applies-no-desktop-yes-service](../includes/applies-no-desktop-yes-service.md)]

Copilot can answer questions with visuals created from your semantic model's data. Tell Copilot what you're looking for, and if the answer isn't already visualized on your report, Copilot will query your model and return the answer to your question in the form of a visual.

:::image type="content" source="media/copilot-ask-data-questions/data-question-skill-02.png" alt-text="Screenshot showing Copilot answer a question about data using a visual." lightbox="media/copilot-ask-data-questions/data-question-skill-02.png":::

## Before you start

Before you can use this feature, make sure you satisfy the [requirements for the use of Copilot](../create-reports/copilot-introduction.md#copilot-requirements).

[!INCLUDE [copilot-notes](../includes/copilot-notes.md)]

Q&A needs to be enabled for your model because Copilot uses the same underlying engine to build queries from your inputs. For most data sources, Q&A is enabled by default.

For some sources, like DirectQuery or Direct Lake models, you might need to enable Q&A manually, either in your semantic model settings in the Service or in your Data Load settings in Power BI Desktop. To learn more about the types of data sources Q&A supports, see [Data sources for natural language Q&A](../natural-language/q-and-a-data-sources.md).

## Use the feature

This capability allows Copilot to generate queries and return visuals based on data in your semantic model. It's available in both view and edit modes in Power BI. Both report authors and viewers can access this feature by asking Copilot for data related to their dataset or report.

## Supported question types

Copilot can answer questions using existing measures and columns in your semantic model, and questions that require Copilot to generate DAX queries to answer questions (described in the following section describing ad hoc calculations). Questions may include asking for existing measures filtered to a different region or span of time than they are on the report, a metric split into categories, or how a measure changes with time.

While the exact questions that Copilot can answer depends on the specifics of your model, here are some examples:

- **“Can you show me sales amount by region?”**  where both sales amount and region are already columns in the data.
- **“What were the top 5 selling products in North America last month?”** where product, region, and date are already columns in the data, and Copilot helps with top N filtering to produce the visual.
- **“Tell me the average price of gasoline per gallon over the last 30 days.”** where price per gallon is a measure already contained in the model, and Copilot helps by taking the average and filtering by relative date to produce the visual.
- **"Which customers bought cheese and wine?"** where cheese and wine are multiple instances from the same Product entity in the model.

Copilot also responds to follow up requests based on what you have already asked in your current session.

:::image type="content" source="media/copilot-ask-data-questions/data-question-follow-up-02.png" alt-text="Screenshot showing a follow-up question in the Copilot pane." lightbox="media/copilot-ask-data-questions/data-question-follow-up-02.png":::

## Ad hoc calculations for data questions

Copilot can also generate DAX queries to answer questions that require ad hoc calculations, such as creating new measures that aren't contained in the model. Examples of questions that Copilot can answer by creating a DAX query include the following:

* What was the year-over-year growth for sales?
* How many employees were hired before 2020?
* Calculate the ratio of cosmetic product orders to all products.
* Which customers didn't buy any products?

You can also verify the DAX query directly from the expanded view or launch DAX query view for further inspection. 

:::image type="content" source="media/copilot-ask-data-questions/data-question-answers-01.png" alt-text="Screenshot of copilot answering a question by creating a DAX query.":::


## Unsupported question types

Copilot can't currently answer questions that require generating new insights like anomaly detection, forecasting, or finding key influencers. The specific questions it can handle depend on your model and report visuals. However, here are some examples of unsupported questions:

- **"Why do our sales go down every July?”**

     This question involves generating deeper insights from the provided data.

- **"How many books do you think we will sell next year?"**

     This question asks for forecasting, which isn't currently supported.

## Reading the answer

Copilot provides an answer for you in the form of a visual. In text, it describes the visual it produced, including the fields it used to build or filter the visual.

You can expand the “How Copilot arrived at this” dropdown to learn more about how Copilot understood your question, and to ensure the correct fields, measures, or filters were chosen from your model.

:::image type="content" source="media/copilot-ask-data-questions/data-question-show-reasoning-02.png" alt-text="Screenshot showing the show reasoning section of a visual answer." lightbox="media/copilot-ask-data-questions/data-question-show-reasoning-02.png":::

You can see more detail about the **Data used** by selecting the link beside each *data used* element, as shown in the following image. 

:::image type="content" source="media/copilot-ask-data-questions/data-question-show-reasoning-details.png" alt-text="Screenshot showing the data details for a visual answer." lightbox="media/copilot-ask-data-questions/data-question-show-reasoning-details.png":::

You can also expand the visual to see it in more detail, and as a report author, you can even add these visuals directly to your report page – just select the "add to page" button below the visual.

:::image type="content" source="media/copilot-ask-data-questions/data-question-expand-02.png" alt-text="Screenshot showing the expand and add to page buttons of a visual answer." lightbox="media/copilot-ask-data-questions/data-question-expand-02.png":::

## Improve answer quality with linguistic modeling

When Copilot builds visuals from data in your semantic model, it references field names to determine which data might answer your question. Power BI authors can use linguistic modeling to improve Copilot's understanding of the questions report viewers might ask.

Authors can guide Copilot by:

- using unique and descriptive column and measure names so Copilot understands the data
- structuring the model according to Power BI's best practices
- adding synonyms to data field names to clarify business-specific terms for Copilot

To learn more about linguistic modeling and ways to streamline the process of improving your linguistic schema with Copilot, see [Intro to Q&A tooling to train Power BI Q&A](/power-bi/natural-language/q-and-a-tooling-intro).

## Limitations and considerations

There are a few other factors to consider at this time when using this capability:

- This capability is only available in the Power BI service. Support for Power BI Desktop is coming soon.
- The only supported language is English.
- This capability doesn't apply filters or slicers currently affecting visuals on the report page to the answers it generates inside the Copilot pane.
- The requirement to enable Q&A is unique to this Copilot capability. You can still use Copilot for other tasks, like [asking questions about content present in your report.](copilot-pane-summarize-content.md#answer-questions-about-your-report-content-in-the-copilot-pane)
- When a question is related to data in the semantic model, Copilot will use the semantic model to answer the question, otherwise it may answer from the [LLM's general knowledge.](https://go.microsoft.com/fwlink/?linkid=2325401)
- For additional limitations on data sources, see [Limitations of Power BI Q&A](../natural-language/q-and-a-limitations.md).

## Next steps

Copilot offers many more capabilities for you to take advantage of, from helping report authors to get started creating reports to helping report viewers parse and explore their data. See the [Overview of Copilot for Power BI](copilot-introduction.md) to learn more about everything Copilot can do.
