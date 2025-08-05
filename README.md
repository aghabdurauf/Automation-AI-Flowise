# Automation-AI-Flowise
A powerful, modular AI-driven automation framework built using Flowise, designed to simplify workflows, automate decision-making, and integrate intelligent agents with real-world business data. This repo empowers users to create custom AI agents that can chat, extract insights, process documents, and trigger automation across tools and platforms.

# 🧠 RAG ChatAgent for Insurance Portfolio – Powered by Flowise

An intelligent Retrieval-Augmented Generation (RAG) chatbot tailored for **Insurance companies**, designed using **Flowise**, Groq, and Llama 3 LLMs. It delivers real-time, context-aware Q&A responses by ingesting portfolio documents via API and using vector-based document search.

---

## 🔧 Tech Stack

| Component        | Technology                             |
|------------------|-----------------------------------------|
| Document Loader  | API-based ingestion                    |
| Embeddings       | Ollama Embedding                      |
| Chat Agent       | Flowise Groq Agent                    |
| Chat Model       | `llama3-70b-8192` (via Groq)          |
| Vector DB        | In-Memory (Planned: Pinecone - latest release) |

---

## 💡 Features

- ✅ RAG pipeline using LLM + Vector Store
- ✅ API-based dynamic document loading
- ✅ Seamless Flowise interface for customization
- ✅ Contextual Insurance product Q&A
- ✅ Pluggable into web apps, CRMs, or WhatsApp bots

---

## 🧠 Use Cases

- Customer support for policyholders
- Pre-sales and onboarding assistants
- Internal knowledge assistant for agents
- Claims and underwriting query automation

---

## 🚀 Deployment Guide

### 1. Requirements
- Python 3.10+
- Node.js 18+
- Ollama installed locally
- Flowise Desktop or Docker setup
- Groq API key
- Pinecone API key (optional for future upgrade)

### 2. Steps

#### Install Flowise
```bash
npm install -g flowise
flowise start
```

#### Install Ollama (If not installed)
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama run llama3:70b
```

#### Load ChatAgent
1. Open Flowise UI (usually at http://localhost:3000)
2. Import JSON file from below (or use your own)
3. Set Document Loader to "API"
4. Use Ollama Embedding in the embedding node
5. Use ChatModel: `llama3-70b-8192` with Groq provider

#### Upgrade to Pinecone (Optional)
- Signup at [Pinecone.io](https://www.pinecone.io)
- Create environment & index
- Get API Key & Index URL
- Replace VectorDB node with Pinecone configuration

---

## 📦 Flowise JSON Export

> 📁 `flowise_rag_insurance.json`

```json
{
  "id": "insurance-chatagent",
  "name": "Insurance RAG ChatBot",
  "nodes": [
    {
      "id": "doc-loader",
      "type": "DocumentLoader",
      "label": "API Document Loader",
      "data": { "sourceType": "api", "apiUrl": "https://your-insurance-api.com/docs" }
    },
    {
      "id": "embed-node",
      "type": "Embeddings",
      "label": "Ollama Embedding",
      "data": { "model": "ollama-embedding" }
    },
    {
      "id": "vector-store",
      "type": "VectorStore",
      "label": "In-Memory Vector Store",
      "data": {}
    },
    {
      "id": "chat-agent",
      "type": "ChatAgent",
      "label": "Groq Agent",
      "data": {
        "llmProvider": "groq",
        "model": "llama3-70b-8192",
        "temperature": 0.2
      }
    }
  ],
  "edges": [
    { "source": "doc-loader", "target": "embed-node" },
    { "source": "embed-node", "target": "vector-store" },
    { "source": "vector-store", "target": "chat-agent" }
  ]
}
```

> Replace the `apiUrl` with your real endpoint.

---

## 🔗 Resources

- [Flowise Docs](https://docs.flowiseai.com/)
- [Groq](https://console.groq.com/)
- [Ollama](https://ollama.com/)
- [Pinecone Docs](https://docs.pinecone.io/)

---

## 🤝 Contributing
Pull requests are welcome! If you have enhancements like better document chunking, fine-tuned embeddings, or more efficient pipeline logic, feel free to fork and PR.


---

## ✨ Author
**Agha Abdul Rauf**

**Connect with me on [LinkedIn](https://www.linkedin.com/in/abdurauf555)**
