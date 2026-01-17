# ⚙️ OttoPilot Edge: Industrial-Grade SLM Agent

![Python](https://img.shields.io/badge/Python-3.11-blue) ![AI](https://img.shields.io/badge/AI-Llama3_8B-green) ![RAG](https://img.shields.io/badge/RAG-Hybrid-orange)

**OttoPilot Edge** is a hybrid AI agent designed to demonstrate **Small Language Model (SLM)** capabilities for intelligent automation. 

Unlike standard chatbots, this system features a **Semantic Router** that dynamically decides whether to answer queries using an internal Knowledge Base (Static PDFs) or Live Web Search (Real-time Data). This architecture mimics industrial maintenance agents that must switch between reading technical manuals and checking live sensor status.

## 🚀 Key Features

* **🧠 SLM-Powered (Small Language Model):** Built on **Llama-3-8B** (via Groq), optimized for low-latency and edge-deployment scenarios suitable for automation hardware.
* **🔀 Semantic Routing:** An intelligent decision layer that classifies user intent (e.g., *"Database"* vs. *"Real-time Search"*) to prevent hallucinations.
* **📚 Hybrid RAG:** Combines **Vector Search (ChromaDB)** for official university regulations with **DuckDuckGo** for live updates (strikes, weather, opening hours).
* **⚡ High Performance:** Uses **HuggingFace Embeddings** for CPU-efficient processing, removing the need for heavy local GPUs.

## 🛠️ Tech Stack

* **Core Logic:** Python 3.11, LangChain
* **Inference Engine:** Groq API (Llama-3-8B-8192)
* **Vector Database:** ChromaDB (Local persistence)
* **Embeddings:** HuggingFace (`all-MiniLM-L6-v2`)
* **Interface:** Streamlit
* **Tools:** DuckDuckGo Search

## 🏗️ Architecture

```mermaid
graph TD;
    User_Input-->Router;
    Router{Decision?};
    Router-->|Static Rule|Vector_DB[(PDF Knowledge Base)];
    Router-->|Live Event|Web_Search(DuckDuckGo);
    Vector_DB-->SLM[Llama-3-8B];
    Web_Search-->SLM;
    SLM-->Final_Answer;
