# Nestlé HR Policy Assistant — RAG Chatbot

An end-to-end Retrieval-Augmented Generation (RAG) application that enables employees to query Nestlé's HR policies through a conversational AI interface. Built using LangChain, FAISS, OpenAI GPT-3.5 Turbo, and deployed with Gradio.

---

## Project Overview

HR policy documents are lengthy and difficult to navigate. This project solves that by building an intelligent chatbot that:
- Reads and understands HR policy PDFs
- Retrieves the most relevant sections for any employee query
- Generates clear, grounded, conversational answers using GPT-3.5 Turbo
- Maintains conversation history for multi-turn dialogue

This is a real-world GenAI application demonstrating the full RAG pipeline from document ingestion to deployed UI.

---

## Architecture — RAG Pipeline

```
PDF Document
     |
PyPDFLoader (Document Ingestion)
     |
RecursiveCharacterTextSplitter (Chunking)
     |
OpenAI text-embedding-ada-002 (Embeddings)
     |
FAISS Vector Store (Semantic Search)
     |
Retriever (k=4 most relevant chunks)
     |
Custom PromptTemplate + ConversationBufferMemory
     |
GPT-3.5 Turbo (Answer Generation, temperature=0.2)
     |
Gradio Chatbot UI (Deployment)
```

---

## Tech Stack

| Component       | Technology                      |
|-----------------|---------------------------------|
| Language        | Python 3.x                      |
| LLM             | OpenAI GPT-3.5 Turbo            |
| Embeddings      | OpenAI text-embedding-ada-002   |
| Vector Store    | FAISS                           |
| RAG Framework   | LangChain                       |
| Document Loader | PyPDFLoader                     |
| Memory          | ConversationBufferMemory        |
| UI              | Gradio Blocks                   |

---

## Key Features

- End-to-end RAG pipeline from raw PDF to conversational AI
- FAISS semantic search retrieves top-4 relevant policy chunks per query
- Multi-turn conversation with context memory across the session
- Custom PromptTemplate ensures factual, professional HR responses
- Temperature set to 0.2 for consistent, grounded answers
- Clean Gradio Blocks interface with example questions and source citation

---

## Project Structure

```
Nestle-HR-Policy-RAG-Chatbot/
|
|-- nestle_hr_assistant_educational.ipynb   # Main project notebook
|-- data/
|   |-- nestle_hr_policy.pdf                # HR policy source document
|-- README.md                               # Project documentation
|-- requirements.txt                        # Dependencies
```

---

## How to Run

### 1. Clone the repository
```bash
git clone https://github.com/AjaykannaE/Nestle-HR-Policy-RAG-Chatbot.git
cd Nestle-HR-Policy-RAG-Chatbot
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Set your OpenAI API key
```python
import os
os.environ["OPENAI_API_KEY"] = "your-api-key-here"
```
Note: Never hardcode your API key. Always use environment variables.

### 4. Run the notebook
Open nestle_hr_assistant_educational.ipynb in Jupyter and run all cells. The Gradio UI will launch automatically.

---

## Requirements

```
langchain
langchain-openai
langchain-community
faiss-cpu
openai
pypdf
gradio
tiktoken
```

---

## Concepts Demonstrated

- **RAG vs Fine-tuning** — RAG chosen for dynamic, document-grounded responses without model retraining
- **Chunking strategy** — RecursiveCharacterTextSplitter with overlap to preserve context across chunk boundaries
- **Vector similarity search** — FAISS cosine similarity to find semantically relevant policy sections
- **Prompt engineering** — System prompt constrains the LLM to answer only from retrieved context
- **Memory management** — ConversationBufferMemory maintains dialogue history for follow-up questions

---

## Sample Interaction

```
User: What is Nestle's policy on annual leave?
Bot:  According to the HR policy, employees are entitled to [X] days of
      annual leave per year. Leave must be approved by the line manager
      at least [Y] days in advance...

User: What about sick leave?
Bot:  Following up on leave policies — for sick leave, Nestle provides...
```

---

## Business Use Case

This application can be adapted for any enterprise with large policy, compliance, or knowledge base documents — reducing HR query load and providing employees with instant, accurate policy information.

---

## Author

**Ajaykanna E**
AI/ML Engineer (Transitioning) | Simplilearn AI Engineer Master's — Distinction (2026)
ajaykanna.career@gmail.com
LinkedIn: https://linkedin.com/in/ajaykannae
Portfolio: https://ajaykannaeportfolio.netlify.app

---

Built as part of the Simplilearn AI Engineer Master's Program.
