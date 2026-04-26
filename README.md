# ReasonRAG: Human‑like Reasoning‑based Retrieval for RAG

> **Compare structured reasoning retrieval versus traditional vector similarity retrieval** – with full explainability and no vector database.

## 🔥 Why this project stands out

Most RAG systems treat documents as bags of chunks, losing the **inherent hierarchy** (chapters, sections, subsections).  
**ReasonRAG** navigates the document like a human:

1. **Parse PDF** into a tree of sections (using heading detection)
2. **Reason** at each node – the LLM decides which child section may contain the answer
3. **Retrieve** the exact section content
4. **Trace** every decision for full explainability

In parallel, a **Vector RAG baseline** (chunk + embed + FAISS) is provided for direct comparison.

## 🧠 Key Innovation

| Feature | ReasonRAG (Ours) | Vector RAG |
|--------|----------------|------------|
| Retrieval method | Reasoning over tree | Similarity search |
| Explainability | ✅ Full path trace | ❌ Opaque scores |
| Data representation | Hierarchical tree | Numerical embeddings |
| Handles structure | ✅ Directly | ❌ Lost |
| Speed | Slower (but smarter) | Fast |

## 🛠️ Built With

- [Gemini API](https://ai.google.dev/gemini-api) (free tier)
- [Sentence‑Transformers](https://www.sbert.net/) for embeddings
- [FAISS](https://github.com/facebookresearch/faiss) for vector index
- [pdfplumber](https://github.com/jsvine/pdfplumber) for PDF text extraction
- [tiktoken](https://github.com/openai/tiktoken) for token counting

## 📊 Evaluation (on your own document)

Run the notebook’s evaluation cell to compare answers side‑by‑side. For complex queries, ReasonRAG typically provides:
- More precise answers (exact section)
- No hallucination from merged chunks
- Fully auditable reasoning
