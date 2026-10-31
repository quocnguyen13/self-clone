---
type: analysis
status: verified
sources: ["[[raw/anthropic-contextual-retrieval.md]]"]
created: "2026-10-29"
updated: "2026-10-29"
tags: ["information-retrieval"]
---
# How does Contextual Retrieval combine embedding and BM25, and where does reranking fit

**Question:** HOw does Contextual Retrieval combine embedding and BM25, and where does reranking fit?

## Answer
Contextual Retrieval works at preprocessing time. An LLM writes a short context for each chunk, and that context is added to the start of the chunk, which then feeds both indexes: the embedding index (Contextual Embeddings) and the BM25 index (Contextual BM25). At query time the system runs as hybrid RAG: BM25 finds exact matches, embeddings find chunks with similar meaning, and rank fusion merges the two lists and removes duplicates. Reranking comes after this first retrieval and before generation: a reranker scores the top 150 chunks against the query, and only the top 20 go to the model. Each layer lowered the retrieval failure rate further, from 5.7% to 1.9% in the source's tests. The cost is an extra query-time step, offset in part because the generating model reads fewer chunks.

## Evidence
- The generated context, usually 50–100 tokens, is added to the chunk before embedding and before the BM25 index is built ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/concepts/Contextual Retrieval]]
- Hybrid steps: BM25 finds top chunks by exact match, embeddings find top chunks by semantic similarity, then "combine and deduplicate results … using rank fusion techniques", and the top-K chunks go into the prompt ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/sources/Source - Contextual Retrieval]]
- Why use both: an embedding model can miss an exact string such as "TS-999", which BM25 finds ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/concepts/BM25]]
- Reranking steps: retrieve the top 150 chunks, pass them with the query through a reranking model that scores each chunk, keep the top 20, send those to the model. The tests used the Cohere reranker ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/concepts/Reranking]]
- Failure rate (1 − recall@20, top 20 chunks, Gemini Text 004, averaged across domains), from a 5.7% baseline: contextual embeddings 3.7% (−35%); adding contextual BM25 2.9% (−49%); adding reranking 1.9% (−67%) ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/concepts/Contextual Retrieval]]
- Reranking "reduces cost and latency because the model is processing less information" ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/concepts/Reranking]]
- Reranking also adds a step at query time, which adds a small amount of latency even though the reranker scores chunks in parallel. Reranking more chunks gives better accuracy but adds latency and cost ([[raw/anthropic-contextual-retrieval.md]]), via [[wiki/concepts/Reranking]]

## Caveats and gaps
- There is only one source, and it comes from the vendor: Anthropic tests a method that runs on its own model and caching feature. The wiki has no independent replication.
- The clip has gaps. The text never describes the 5.7% baseline setup, and the charts and the Appendix I results table are images only.
- The source names no rank-fusion method; it says only "rank fusion techniques". (general knowledge) A common choice is Reciprocal Rank Fusion, which scores each chunk 1/(k + rank) in each list and adds the scores.
## Related
- [[wiki/concepts/Contextual Retrieval]]
- [[wiki/concepts/BM25]]
- [[wiki/concepts/Reranking]]
