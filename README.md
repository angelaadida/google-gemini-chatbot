# 🤖 Google Gemini Personal Virtual Assistant

A conversational AI chatbot built with **Google Gemini 1.5 Flash**, **RAG (Retrieval-Augmented Generation)**, **LangChain**, and **Gradio** — featuring both text and voice interaction.

---

## 🌟 Features

- 🧠 **RAG Architecture** — Retrieves relevant context from a vector database before generating responses
- 🎙️ **Speech-to-Text (STT)** — Voice input using OpenAI Whisper
- 🔊 **Text-to-Speech (TTS)** — Audio responses using Silero TTS
- 🌐 **Agentic Tools** — Calls external APIs (e.g. real-time time & date from TimeAPI)
- 💬 **Gradio UI** — Clean chat interface with microphone support

---

## 🏗️ Architecture

```
User Input (Text / Voice)
        ↓
  [STT - Whisper]         ← Voice input
        ↓
   RAG Pipeline
  ┌─────────────────────────────────┐
  │  Query → ChromaDB Retriever     │
  │       → Relevant Context        │
  │       → Gemini 1.5 Flash (LLM)  │
  │       → Response                │
  └─────────────────────────────────┘
        ↓
  Agentic Tools (Time/Date API)
        ↓
  [TTS - Silero]          ← Voice output
        ↓
   Gradio Chat UI
```

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| LLM | Google Gemini 1.5 Flash |
| Embeddings | Google Text Embedding 004 |
| Vector DB | ChromaDB |
| Framework | LangChain |
| UI | Gradio |
| STT | OpenAI Whisper (via HuggingFace) |
| TTS | Silero TTS (via TorchHub) |
| External API | TimeAPI.io |
| Language | Python |

---

## 📁 Project Structure

```
google-gemini-chatbot/
│
├── Google_gemini_chatbot.ipynb   # Main notebook
├── intents.json                  # Knowledge base for RAG
├── chroma_db/                    # Vector store (auto-generated)
└── README.md
```

---

## 🚀 How to Run

### 1. Install Dependencies
```bash
pip install gradio
pip install langchain-google-genai
pip install langchain langchain_community jq
pip install chromadb
pip install torchaudio omegaconf
```

### 2. Set Up API Key
```python
import os
os.environ['GOOGLE_API_KEY'] = "your_google_api_key_here"
```
Get your free API key at: https://ai.google.dev/pricing

### 3. Run the Notebook
Open `Google_gemini_chatbot.ipynb` in Jupyter or Google Colab and run all cells.

### 4. Launch Gradio UI
The last cell launches a Gradio interface — open the local URL in your browser.

---

## 💡 How It Works

### RAG Pipeline
1. Load knowledge base from `intents.json`
2. Generate embeddings using **Google Text Embedding 004**
3. Store in **ChromaDB** vector store
4. On user query → retrieve top-1 relevant document
5. Feed context + query into **Gemini 1.5 Flash**

### Agentic Tools
The assistant can call external APIs to answer dynamic questions:
- *"What time is it?"* → calls TimeAPI.io
- *"What is today's date?"* → calls TimeAPI.io

### Voice Interaction
- **Input**: Microphone → Whisper STT → text query
- **Output**: Text response → Silero TTS → audio playback

---

## 📊 Example Interactions

| Query | Response Type |
|-------|--------------|
| "Hi!" | Greeting from knowledge base |
| "Tell me about yourself" | RAG-retrieved context |
| "What time is it now?" | Real-time API call |
| "What is Gemini?" | LLM general knowledge |

---

## 👩‍💻 Author

**Angela** — Data Scientist | AI • ML • GenAI • RAG  
📍 Kuala Lumpur, Malaysia  
🔗 [GitHub](https://github.com/angelaadida)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
