# forecasting-qa-news
A dataset of binary forecasting questions augmented with news articles, designed to evaluate LLM forecasting capabilities. 


## Dataset Purpose

The dataset consists of 614 **binary real-world forecasting question** sourced from [Metaculus](https://www.metaculus.com/), a community forecasting platform. The questions span the period from October 1, 2021, to July 15, 2024, and all have been resolved.
Each question is associated with:

- A **natural language question** about a real-world event.
- The **final resolved outcome** ("yes" or "no").
- **Description** providing background information about the question
- **Resolution criteria** detailing the conditions under which the question is resolved
- **News articles** retrieved before the resolution date, to simulate human forecasting context.
- **LLM-generated summaries** of the news articles related to the forecasting question.


## Dataset Schema

Each entry in the dataset (stored in `forecasting_qa_news.json`) has the following fields:

| Field | Description |
|-------|-------------|
| `id` | Unique question ID from Metaculus|
| `question` | Forecasting question in natural language |
| `answer` | Final resolution: `"yes"` or `"no"` |
| `description` | Background information about the question from Metaculus |
| `description_text` | Cleaned, plain-text version of the description  |
| `resolution_criteria` | Explanation of how the question resolves |
| `resolution_criteria_text` | Cleaned plain-text version of the resolution criteria |
| `categories` | List of topic categories |
| `gnews_query` | Search query used to find news articles |
| `news_articles` | List of news articles related to the forecasting question |
| `created_time` | When the question was created on Metaculus|
| `publish_time` | When the question was published on Metaculus |
| `resolve_time` | When the question was resolve on Metaculus |
| `days_open` | Number of days the question remained open  on Metaculus|

### News Article Format

Each `news_articles` entry includes:
- `url`: Original news source
- `title`: Headline of the article
- `text`: Full article body 
- `authors`: List of author names
- `publish_date`: Date of publication
- `summary`: Generic summary
- `summary_llm`: Question-related summary generated via GPT-3.5-turbo
- `keywords`: Article keywords extracted via NLP methods

## Demo Notebook

See [`notebooks/explore_dataset.ipynb`](notebooks/explore_dataset.ipynb) for an interactive exploration of the dataset, including:
- Sample entries
- Category distribution
- Article statistics