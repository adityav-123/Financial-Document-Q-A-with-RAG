# 🎥 AI Financial Analyst: Chat with Your Documents

A Retrieval-Augmented Generation (RAG) system that lets users upload a dense PDF (like a company's 10-K report), process it, and ask natural language questions to get accurate, source-backed answers.

Runs entirely **locally** using open-source models — no API keys required.

---

## 🚀 Project Overview

LLMs are powerful but lack specific, timely, or private knowledge. This project solves that using a complete **RAG pipeline**:

* **Document Ingestion**: Extracts clean text from any PDF
* **Knowledge Base Creation**: Splits the text, generates embeddings, and stores them in a FAISS index
* **Contextual Answering**: Finds the most relevant text chunks for a given question and feeds them into an LLM for answer generation

---

## 🛠️ Tech Stack

* **Language**: Python
* **Libraries**: LangChain, HuggingFace Transformers, PyMuPDF, NumPy, Pickle
* **Vector Store**: FAISS (Facebook AI Similarity Search)
* **Embedding Model**: `sentence-transformers/all-MiniLM-L6-v2`
* **LLM**: `google/flan-t5-base`
* **Environment**: Jupyter Notebook

---

## 📂 Project Structure

```bash
financial_analyst_project/
├── NASDAQ_AAPL_2024.pdf           # Example source document
├── financial_analyst.ipynb        # Main Jupyter Notebook
├── extracted_report_text.txt      # Auto-generated: Plain text from PDF
├── report_chunks.pkl              # Auto-generated: Serialized text chunks
├── faiss_index/                   # Auto-generated: Vector store
└── requirements.txt               # Project dependencies
```

---

## ⚙️ How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/adityav-123/Financial-Document-Q-A-with-RAG.git
cd Financial-Document-Q-A-with-RAG
```

### 2. Set Up the Environment

```bash
python -m venv venv

# Activate it
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

pip install -r requirements.txt
```

### 3. Add a Document

Place the PDF you want to analyze in the main project directory.

### 4. Run the Notebook

Open and run `financial_analyst.ipynb` top-to-bottom.

Sections:

* **PDF Text Extraction**
* **Text Chunking**
* **Vector Store Creation**
* **Q\&A Inference**

*Note: The first time you run Q\&A, the models will download and may take a few minutes.*

---

## 🌊 Workflow: The RAG Pipeline

### 1. Text Extraction

* Uses PyMuPDF to parse the PDF and extract raw text with basic structure

### 2. Chunking

* Text is split into \~1000-character chunks with overlap
* Done using LangChain's `RecursiveCharacterTextSplitter`

### 3. Embedding + Indexing

* Each chunk is embedded using `all-MiniLM-L6-v2`
* Embeddings are stored in a **FAISS** vector store for fast similarity search

### 4. Retrieval + Generation

* User question ➔ embedded
* FAISS retrieves top relevant chunks
* Question + chunks are passed to `flan-t5-base` for answer generation

This ensures answers are grounded in the document.

---

## 🔮 Future Improvements

### 📈 UI for Upload & Chat

* Build a Streamlit or Gradio app for a front-end PDF upload + Q\&A interface

### 🧐 Try Larger Models

* Swap `flan-t5-base` with `Mistral`, `LLaMA`, or other open-source LLMs for better response quality

### ⏱️ Optimize Speed

* Use GPU acceleration for embedding + inference
* Try more efficient vector stores (e.g., `chromadb`, `qdrant`)

---

> 🌟 This project is a fully local, transparent alternative to commercial AI assistants for document analysis.
