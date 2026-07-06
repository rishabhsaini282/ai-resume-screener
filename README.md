# AI Resume Ranking Agent 🚀

**🌟 [Try the Live Demo Here!](https://aidevdayindia.org/agents/recruitment-agents/resume-ranking.html)**

An intelligent, full-stack recruitment tool that uses Large Language Models (LLMs) to automatically screen and rank candidate resumes against a specific Job Description. 

## Features

... *(keep the rest of your README exactly the same)* ...
## Features
* **AI-Powered Scoring:** Uses OpenRouter (Gemini/GPT/Claude) to evaluate resumes based on required skills and experience.
* **Smart Fallback System:** Automatically cascades through a chain of AI models to ensure 100% uptime, falling back to a keyword-matching algorithm if APIs are unavailable.
* **Privacy-First Processing:** Processes candidate resumes entirely in-memory (no disk I/O) to protect Personally Identifiable Information (PII).
* **Live GitHub Scraping:** Automatically extracts GitHub URLs from resumes and fetches live repository data to assess a developer's real-world code.

## Tech Stack

* **Backend:** FastAPI (Python), Uvicorn, PyPDF, python-docx
* **Frontend:** HTML, JavaScript, CSS (Vanilla)
* **AI Integration:** OpenRouter API 

## How to Run Locally

1. Clone the repository.
2. Create a virtual environment: `python -m venv .venv` and activate it.
3. Install dependencies: `pip install -r backend/requirements.txt`
4. Create a `.env` file in the `backend` folder with your API keys:

## 👨‍💻 About the Creator

Rishabh Saini is an AI Tools & Content Engineer passionate about artificial intelligence, automation, and creative technology. He is currently working with AgileWoW, an AI and Agile-focused learning and consulting platform that helps teams and organizations adopt modern AI-driven workflows and agile practices.

[LinkedIn](https://www.linkedin.com/in/rishabh-saini-ba9832290/)
