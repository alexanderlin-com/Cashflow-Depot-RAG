# Cashflow Depot RAG
*Built from a tutorial. Broken. Rebuilt for scale, speed, and sanity.*

---

## 🚀 What This Is

A Retrieval-Augmented Generation (RAG) chatbot powered by:

- **LangChain** for prompt/tool orchestration  
- **Pinecone** for vector search  
- **OpenAI** for LLM output  
- **Streamlit** for frontend  

Forked from [LangChain-Pinecone-RAG](https://github.com/ThomasJanssen-tech/LangChain-Pinecone-RAG/tree/main), then *modified like hell* to work with real-world doc loads (300+ PDFs), forward-compatible Python versions, and tighter dev loops.

---

## 🔨 Major Improvements Over the Original

| Area              | Original            | My Upgrade                               |
|-------------------|---------------------|-------------------------------------------|
| Ingestion UX      | Silent, brittle     | Credential check + progress bar           |
| Input Handling    | Loose single-PDF    | Folder-based recursive doc loader         |
| Prompt Quality    | Shallow responses   | Deep, customized LLM system prompt        |
| Python Compatibility | Python ≤3.10    | Fully working on 3.13                     |
| Frontend          | Stock tutorial      | Branded & modified                        |
| Cleanup           | None                | `deingestion.py` kills your stale indexes |

---

## 🧠 Why I Made These Changes

### ✅ Credential Awareness  
Because eating a stack trace when your env isn’t set is trash. I made it fail loud and clear.

### ✅ Folder-Based Ingestion  
Tutorials are fine with 2 docs. I had **300+**. Subfolder crawl was non-negotiable.

### ✅ Progress Bar for Ingestion  
Because nothing feels worse than staring at your terminal, wondering if it died. Now you get live feedback.

### ✅ Python 3.13 Compatibility  
I live on the bleeding edge. I fix what breaks. You’re welcome.

### ✅ Prompt Engineering  
The default prompt gave me canned garbage. I rewrote it to force thoughtful, long-form answers tuned to my use case.

### ✅ De-Ingestion Script  
Pinecone ain’t free. If you’re iterating, you *need* index deletion on command. So I made it easy.




## Instructions (for myself) because I need em.

1. Local Development Setup

    Create Virtual Environment (Only do this once per project):
    ```python3 -m venv venv```

Activate Virtual Environment (Do this every time you open a new terminal for the project):
    ```source venv/bin/activate```

Install Dependencies:
    ```pip install -r requirements.txt```

2. Running Locally with Docker

    Build the Docker Image:
    ```docker build -t cashflow-depot-rag .```

Run the Container:
    ```docker run --rm -p 8501:8501 --env-file .env cashflow-depot-rag```

3. Deployment

    Automated Deployment:

        Push your changes to the main branch on GitHub. The GitHub Actions pipeline will handle the rest automatically.