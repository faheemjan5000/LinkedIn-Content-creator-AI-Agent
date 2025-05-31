# LinkedIn-Content-creator-AI-Agent

![image](https://github.com/user-attachments/assets/f618a058-f1c7-4a14-8a0f-5b3a72ae3d3e)

# LinkedIn Content Creator Workflow (n8n)

This repository contains an automated n8n workflow designed to generate engaging, professional LinkedIn posts based on current content trends.

## 🚀 Workflow Overview

This n8n workflow helps content creators synthesize insights from recent articles into polished LinkedIn posts using AI. It:

1. **Reads a topic from Google Sheets** where the status is marked "To Do".
2. **Queries recent articles** related to the topic using the Tavily API.
3. **Processes the content** with Google Gemini (via LangChain) to generate a concise, professional post.
4. **Updates Google Sheets** with the generated content and status set to "Created".

---

## 🛠️ Tech Stack

- **n8n**
- **Google Sheets**
- **Tavily Search API**
- **Google Gemini AI (via LangChain)**
- **OpenAI Agent node (LangChain Agent)**

---

## 📋 Prerequisites

To use this workflow, ensure the following:

- A [Google account](https://accounts.google.com/) with access to Google Sheets.
- Tavily API key (for content fetching): [https://www.tavily.com](https://www.tavily.com)
- Google Gemini/PaLM API access (via LangChain or direct credentials).
- An n8n environment with access to:
  - Google Sheets OAuth credentials
  - Tavily API key stored securely
  - Google Gemini API key or credentials

---

## 🔧 Setup Instructions

1. **Import the Workflow JSON** into your n8n instance.
2. **Set up credentials**:
   - Google Sheets OAuth2
   - Tavily API token (as `Bearer YOUR_API_KEY`)
   - Google Gemini (LangChain) credentials
3. **Configure your spreadsheet**:
   - Must contain columns: `Topic`, `Content`, `Status`
   - Ensure at least one row with `Status = "To Do"` for execution
4. **Manually trigger the workflow** or automate using a schedule or webhook trigger.

---

## 🧠 Workflow Logic

```mermaid
graph TD
    A[Manual Trigger] --> B[Read Topic from Google Sheets]
    B --> C[Search Articles with Tavily]
    C --> D[Generate Post with LangChain Agent & Gemini AI]
    D --> E[Write Post to Google Sheets as 'Created']

