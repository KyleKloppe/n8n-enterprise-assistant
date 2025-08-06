# RAG-Based Enterprise Knowledge Assistant (n8n)

A modular, privacy-conscious internal AI assistant that helps employees quickly retrieve information from company documents and data — powered by **n8n**, **local or cloud LLMs**, and **vector search**. This project is designed to be deployable even in **offline or restricted environments**.

---

## 🧠 Features

- 📎 **Document Ingestion & Chunking** from Google Drive, Dropbox, or local folders
- 📚 **Embeddings & Indexing** via Pinecone, FAISS, or Qdrant
- 🔍 **Smart Query Routing** to detect summarization vs. calculation
- 📊 **On-the-fly Python/Pandas Calculations** for numeric queries
- 🧾 **Source-Cited Responses** grounded in real company data
- 💬 **Slack / Email / API Integration** to query assistant easily
- 🔒 **Offline Mode Support** using local LLMs + vector DBs

---

## 🧰 Tech Stack

| Component | Options / Tools |
|----------|-----------------|
| Vector DB | Pinecone (cloud), FAISS/Qdrant (local) |
| Embeddings | OpenAI, HuggingFace, Ollama-compatible local models |
| LLM | GPT-4, GPT-3.5, Mistral, Phi (via Ollama) |
| Automation | [n8n](https://n8n.io/) Workflows |
| Optional Compute | Python via Pandas or external command |

---

## 📦 Repository Structure

```bash
/n8n-enterprise-assistant/
├── README.md                # You're here!
├── workflows/
│   ├── ingestion.n8n.json   # Watches Drive, chunks, embeds, indexes
│   ├── query.n8n.json       # Handles queries, retrieval, and response
│   └── sync.n8n.json        # Optional cron-based reindexing
├── prompts/
│   └── base_prompt.txt      # Assistant instructions to LLM
├── scripts/
│   └── pandas_runner.py     # Python code for numeric queries
├── examples/
│   └── sample_QA.md         # Realistic example queries & answers
├── diagrams/
│   └── system_diagram.png   # High-level workflow architecture
└── docs/
    └── deployment_guide.md  # Setup notes and best practices
```

---

## 🚀 How It Works

### 1. Document Ingestion
- Watches a company Google Drive folder or shared directory
- Extracts file contents (PDF, DOCX, Markdown, CSV)
- Splits into overlapping chunks
- Generates embeddings and indexes them in the vector DB

### 2. Query Workflow
- Triggered via Slack, HTTP request, or email
- Detects if the query requires:
  - 🔹 Summarization → pulls relevant chunks
  - 🔹 Numeric analysis → loads spreadsheet and runs pandas
- Assembles a context block and routes it to the LLM
- Returns a clear, source-cited answer

---

## 🧪 Sample Use Cases

- 🧾 “What’s our PTO rollover policy?”
- 📊 “Compare average sales from 2021 vs. 2024”
- 🧼 “List all upcoming security compliance dates”
- 📣 “Summarize all marketing meeting notes from Q2”

---

## 🛡️ Security / Offline Considerations

- No external API calls when using local Ollama models and FAISS
- Vector DB can run on-premise
- No document or query data leaves your local infrastructure
- Prompt includes anti-hallucination and safety instructions

---

## 📈 Future Additions

- Feedback form for query satisfaction rating
- PDF export of responses for compliance
- Admin dashboard to view query patterns
- Azure AD / Google SSO login protection

---

## 📣 Want to Contribute?
This project is still under active development. Feedback, issues, or pull requests welcome!

---

## 📌 Status
🧪 **Prototype complete. Ready for business testing.**

If your company handles sensitive info and wants to try AI-powered search safely — this is for you.

> Built with ❤️ using n8n, Ollama, and secure AI design practices.
