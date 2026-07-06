# Architecture & Data Flow

Instead of a simple keyword search, this agent uses a multi-step verification pipeline to ground candidate claims in reality.

| Stage | Component | Action / Input | Output / Payload |
| :--- | :--- | :--- | :--- |
| **1. Ingestion** | **Document Parser** (`PyMuPDF`, `docx2txt`) | Reads user-uploaded Job Description (JD) and Candidate Resumes (PDF/DOCX). | Normalized Raw Text |
| **2. Extraction** | **LLM Skill Extractor** | Parses raw resume text to identify claimed skills and find embedded GitHub profile links. | GitHub Handle & Extracted Entities |
| **3. Verification** | **GitHub API Worker** | Pings the live GitHub API to check recent commit volume, active repositories, and primary languages. | `github_verification.json` |
| **4. Evaluation** | **LLM Evaluator Agent** | Cross-references the JD, parsed resume text, and live GitHub data using strict evaluation prompts. | Structured JSON (Score, Strengths, Weaknesses, Missing Skills) |
| **5. Fallback** | **TF-IDF Keyword Matcher** | Triggers automatically if the LLM provider times out or fails, ensuring the user still gets a baseline ranking. | Keyword Match Score |
