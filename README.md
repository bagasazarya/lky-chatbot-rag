# lky-chatbot-rag
TECHNICAL APPROACH & ARCHITECTURE:

1. Data Ingestion & Knowledge Base (RAG):
- Source Material: Curated transcripts of Lee Kuan Yew’s speeches, memoirs ("From Third World to First"), and key parliamentary debates.
- Chunking & Vector Store: Documents were chunked into 500-token segments with 50-token overlap, embedded using OpenAI's text-embedding-3-small, and indexed in a vector store (Pinecone / ChromaDB) for semantic retrieval.

2. RAG Retrieval & Prompt Engineering:
- System Prompt: Mandates strict adherence to LKY's worldview, tone, and logical framework (Pragmatism, Meritocracy, Rule of Law, Geo-Strategic Balance).
- Context Injection: For any user query, the top-3 most relevant historical text chunks are retrieved and injected into the LLM system context before generating a response.

3. Evaluation & Guardrails (Bonus Implementation):
- RAG Triad Evaluation: Evaluated using metrics for Context Relevance, Groundedness, and Answer Relevance to prevent hallucination.
- Fallback Strategy: If a question falls completely outside LKY's domain or historical scope (e.g., modern crypto speculative trading), the bot responds using LKY’s core underlying principles (caution, fundamental value, risk management) rather than making up fictional historical quotes.

WHAT WENT WRONG & LESSONS LEARNED:
- Initial Challenge: Early prompt iterations resulted in a response that sounded like a generic polite AI assistant rather than the decisive, candid, and sharp tone of Lee Kuan Yew.
- Resolution: Refined the system prompt to explicitly restrict overly sympathetic "AI fluff" and instructed the model to adopt LKY’s characteristic directness, historical references, and emphasis on hard realities.
