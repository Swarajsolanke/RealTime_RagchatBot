# 🚀 Realtime RAG-based Chatbot

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-green?logo=fastapi)
![ChromaDB](https://img.shields.io/badge/ChromaDB-VectorDB-orange?logo=chromadb)
![Mistral](https://img.shields.io/badge/Mistral-7B-informational)
![GeminiAPI](https://img.shields.io/badge/Gemini-API-yellow)

A full-stack Retrieval-Augmented Generation (RAG) chatbot system using **ChromaDB**, **Mistral 7B (GGUF)** for local LLM inference, and **Gemini API** for document summarization. Features a custom HTML/CSS frontend with dynamic PDF upload and chatbot querying.

---

## 📁 Project Structure

```
RealTime_RagchatBot/
│
├── backend/
│   ├── api.py         # FastAPI backend API (serves chatbot)
│   ├── chain.py       # Core RAG logic (embedding + LLM response)
│   ├── ingest.py      # Index and embed documents into ChromaDB
│   └── chroma_db/     # ChromaDB persistent storage
│
├── data/
│   ├── pdfs/          # Initial PDF documents
│   ├── manuals/       # Additional manuals
│   └── chroma_db/     # Vector DB for embeddings
│
├── notebooks/         # Experiments and debugging
├── enhanced_chat_app.html # Frontend UI
├── requirements.txt   # Python dependencies
└── README.md          # You are here!
```

---

## ✨ Features

- 📄 PDF ingestion and semantic chunking
- 🧠 ChromaDB as persistent vector database
- 💬 Local inference using **Mistral-7B-Instruct** (.gguf) via llama.cpp/ctransformers
- ☁️ Gemini API for PDF summarization
- 🌐 FastAPI backend with REST endpoints
- 🎨 Custom HTML/CSS frontend interface
- 📎 Dynamic PDF upload and question answering

---

## 🌐 Demo Screenshots


![Chatbot UI]({D4EE90C3-735E-4A64-A9DA-FA0432BB1D56}.png)


![PDF Upload]({34578643-271A-44CC-A4F2-E6932EF41F6F}.png)


![Custom Query]({6F40EB12-E8D3-4172-A0B5-965CAB95F2AC}.png)

> **You can add custom PDFs and ask questions about them!**

---

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/Swarajsolanke/RealTime_RagchatBot.git
cd RealTime_RagchatBot
```

### 2. Create and Activate Virtual Environment

```bash
python -m venv rag_env
rag_env\Scripts\activate   # Windows
# source rag_env/bin/activate   # Linux/Mac
```

### 3. Install Requirements

```bash
pip install -r requirements.txt
```

### 4. Ingest and Index PDF Manuals

```bash
python backend/ingest.py
```
*This stores embeddings in persistent ChromaDB located in backend/chroma_db.*

### 5. Run the FastAPI Backend

```bash
uvicorn backend.api:app --reload
```
Visit FastAPI docs: [http://localhost:8000/docs](http://localhost:8000/docs)

### 6. Run the Frontend

Simply open `enhanced_chat_app.html` in your browser.

Or serve it with a static server:

```bash
python -m http.server 5500
```

---

## 🔍 How it Works

**RAG Pipeline:**
- 🧩 **Embedding:** `all-mpnet-base-v2` from Sentence Transformers
- 📚 **Storage:** ChromaDB (persistent vector store)
- 🤖 **LLM:** Mistral-7B-Instruct-v0.1 (.gguf) via ctransformers
- 💬 **Response:** Top-k relevant chunks + query passed to LLM for generation
- 📎 **Gemini API:** Used to summarize uploaded PDFs before ingestion

**PDF Upload + Summarization:**
- Upload a PDF using the frontend
- Gemini API extracts and summarizes content
- Summary is embedded and added to ChromaDB

---

## 🧰 Tech Stack

| Component         | Tool / Library                        |
|-------------------|---------------------------------------|
| Embeddings        | sentence-transformers (mpnet/MiniLM)  |
| Vector DB         | ChromaDB                              |
| LLM Inference     | ctransformers + Mistral 7B (.gguf)    |
| Summarization     | Google Gemini API                     |
| Backend API       | FastAPI                               |
| Frontend          | HTML + CSS                            |

---

## 📦 Main Dependencies

See `requirements.txt` for the full list. Key packages:
- fastapi
- uvicorn
- chromadb
- ctransformers
- sentence-transformers
- PyMuPDF
- requests
- openai
- python-dotenv

---

## ❗ Notes

- You must manually download the `.gguf` Mistral model and place it inside a `models/` folder at the project root.
- Ensure the ChromaDB directory exists before querying.
- Verify the Mistral model path in `chain.py` matches your setup.

---

## 💡 Sample Queries

- "What is the temperature description of Realme buds?"
- "What is low water alarm?"
- "How to reset a Dell Latitude laptop?"

---

## 🛠️ Troubleshooting

- ✅ Ensure ChromaDB directory exists before querying.
- ✅ Verify Mistral .gguf model path is correct in `chain.py`.
- ✅ Check tokenizer and generator are properly loaded with correct model path.
- ✅ If UI freezes, check browser console for network errors.

---

## 🤝 Contact & Contributions

Made with by Swaraj  Solanke

- For issues or suggestions, open a GitHub issue or email: **swarajsolanke02@gmail.com**
- GitHub: [https://github.com/Swarajsolanke/RealTime_RagchatBot.git]




