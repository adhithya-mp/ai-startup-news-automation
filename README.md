# ai-startup-news-automation
An automated n8n workflow that collects AI Startup news, cleans the data, removes duplicates, filters hype articles, extracts structured fields using an LLM, and stores the final JSON output into Google Sheets. Includes error handling and a complete workflow diagram.
AI Startup News Automation

This project is an automated workflow built using n8n. Its goal is to collect the latest AI Startup news, clean the data, remove repeated articles, filter out hype or low-information content, extract important details using an LLM, and finally store the results in Google Sheets.

What the Workflow Does
1. Fetch AI Startup News
The workflow connects to the GNews API and collects the latest news about AI startups. The API returns raw JSON containing the title, description, content, source, and published date.

2. Clean the Article Data

Only the important fields are kept. Missing or empty fields are handled safely so the workflow will not fail if the API returns incomplete data.

3. Remove Repeated Articles

The workflow checks each article’s title and removes duplicates so that only one version of each news topic continues forward.

4. Filter Out Hype Articles

Articles that contain too many hype words or very little real information are removed. This ensures only meaningful and useful articles are processed.

5. Use Groq LLM to Extract Important Fields

Each cleaned article is sent to the Groq LLM, which extracts four key fields in a structured JSON format:

company_name

category

sentiment_score

is_funding_news

Error handling is added so the workflow continues even if the LLM output is incomplete.

6. Save the Final Output to Google Sheets

The processed and structured article data is added to a Google Sheet. Each article becomes one row in the sheet.

7. Workflow Files Included

This repository includes the full n8n workflow file (JSON) and a PDF diagram showing the steps in order. Both can be used to understand or rebuild the automation.
**How to Set Up This Workflow**

1.Open n8n.cloud (or your local n8n instance).

2.Go to Workflows → Import Workflow and upload the file:
ai-analyst-workflow.json

3.Add the required API keys inside n8n:

GNews API key (fetching AI startup news)

Groq API key (LLM for structured extraction)

Google Sheets credentials (to store results)

4.Open your Google Sheet and make sure it contains the following columns before running the workflow:

company_name

category

sentiment_score

is_funding_news

5.Go to the Google Sheets node in n8n and select your Sheet.

6.Click Execute Workflow to run the automation.

Once executed, the workflow will automatically fetch the news, clean and filter the articles, extract structured fields using Groq LLM, and save everything into your Google Sheet.
**Demo Files**

All demo files (video and screenshots) are stored here:
Google Drive Folder: https://drive.google.com/drive/folders/1f_tOUR9sRnkR_a-5i27NNPyzQWl0mltl?usp=drive_link

Contents:
- Demo video
- Workflow screenshots



