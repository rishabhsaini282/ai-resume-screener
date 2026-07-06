# AI Recruitment Agent

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.109+-009688.svg?logo=fastapi)](https://fastapi.tiangolo.com)

A full-stack, AI-powered agent designed to give engineering teams a high-signal first pass on inbound resumes. Instead of just doing semantic search on keywords, this agent reads the resume, extracts the candidate's GitHub profile, pings the live GitHub API to verify their commits and languages, and scores the grounded reality against your Job Description (JD). 

**[View the Live Demo (Hosted Version)](https://aidevdayindia.org/agents/recruitment-agents/resume-ranking.html)**

## Core Features

* **Multi-Format Parsing:** Natively handles unstructured text extraction from PDFs and DOCX files (no third-party parsing APIs required).
* **Live GitHub Verification:** Doesn't just trust the resume. If a GitHub link is present, the agent fetches public repository data, recent commit activity, and primary languages to validate technical claims.
* **Deterministic Structured Output:** Forces the LLM to return strict JSON containing a 0-100 score, specific matched skills, identified weaknesses, and missing key terms.
* **Keyword Fallback:** If the LLM provider goes down or times out, the system degrades gracefully to a TF-IDF keyword matching algorithm to ensure you still get a baseline ranking.

## How It Works

This isn't a wrapper around a single prompt. It's a localized pipeline:
1. `DocumentProcessor`: Converts uploads to normalized text using `PyMuPDF` and `python-docx`.
2. `SkillExtractorAgent`: A lightweight LLM call to find the GitHub handle and a raw list of claimed skills.
3. `GitHubWorker`: Uses a GitHub PAT to query the candidate's public activity.
4. `EvaluatorAgent`: The heavy LLM call. It takes the JD, the parsed resume, and the GitHub JSON payload, and outputs a strict scoring schema.

## Quickstart (Local Setup)

Clone the repo and run it locally. We use FastAPI for the backend and a lightweight vanilla JS frontend.

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/ai-recruitment-agent.git
cd ai-recruitment-agent

# 2. Set up the virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure environment variables
cp .env.example .env
# Edit .env and add your OpenAI API key and GitHub PAT

# 5. Run the FastAPI server
uvicorn main:app --reload --port 8000
```

##  About the Creator

Rishabh Saini is an AI Tools & Content Engineer passionate about artificial intelligence, automation, and creative technology. He is currently working with AgileWoW, an AI and Agile-focused learning and consulting platform that helps teams and organizations adopt modern AI-driven workflows and agile practices.

[LinkedIn](https://www.linkedin.com/in/rishabh-saini-ba9832290/)
