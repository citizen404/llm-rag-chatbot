# DesteneeAI LLM RAG Chatbot — Numerology AI Assistant

## Overview
This project is a production-oriented LLM chatbot that generates 
personalized numerology-based analyses using Retrieval-Augmented 
Generation (RAG).

The system combines structured user inputs (name, birth date, time, and 
location) with domain-specific knowledge extracted from PDF documents and 
transcribed video content. The chatbot retrieves relevant context and uses 
an LLM (OpenAI GPT or Llama-3) to generate grounded, explainable 
responses.

While numerology is a belief-based domain, this project focuses on 
**applied LLM system design**, data pipelines, routing logic, and 
cost/latency trade-offs rather than domain claims.

---

## Key Features
- RAG-based question answering over custom knowledge base
- Hybrid input processing: structured parameters + unstructured documents
- Modular prompt design with controlled context injection
- Support for multiple LLM providers (OpenAI, Llama-3)
- Subscription-ready architecture (Stripe; first analysis free)
- Designed with production constraints in mind

---

## Architecture

User Input
├── Structured data (name, birth date, time, location)
└── Free-form question
↓
Query Router
├── Direct LLM
└── RAG Pipeline
↓
Vector Store (Embeddings)
↓
Context Assembly
↓
LLM Response

---

## Data Sources
- PDF documents with domain-specific knowledge
- Transcribed educational video content
- Structured metadata (date/time/place of birth)
- External geolocation data (latitude/longitude by city)

---

## RAG Pipeline
1. Document ingestion and chunking
2. Embedding generation
3. Vector similarity search (top-k)
4. Context injection into prompt
5. LLM generation with source grounding

The system prioritizes **clarity, reproducibility, and debuggability** 
over maximal retrieval recall.

---

## Prompting Strategy
- Separation of system, context, and user instructions
- Explicit grounding instructions to reduce hallucinations
- Controlled tone and response structure
- Defensive prompting against prompt injection

---

## Trade-offs Considered
- **Latency vs. response quality**
- **Cost vs. retrieval depth**
- **Simplicity vs. flexibility**
- **Determinism vs. creativity**

Design choices intentionally favor transparency and predictable behavior.

---

## Failure Modes
- Missing or low-relevance retrieval results
- Context window overflow
- Ambiguous user inputs
- Domain inconsistency across sources

These cases are logged and surfaced for future evaluation improvements.

---

## Evaluation
Basic offline evaluation is implemented to:
- Validate retrieval relevance
- Detect hallucinated responses
- Track regression across prompt or data changes

---

## Subscription & Monetization
The system is designed for a subscription-based model:
- First personalized analysis is free
- Ongoing access via Stripe subscriptions
- LLM usage and cost tracked per user/session

---

## Tech Stack
- **Language:** Python
- **LLMs:** OpenAI GPT / Llama-3
- **Embeddings & Vector Store:** FAISS / Chroma
- **Data Processing:** PDF parsing, transcript ingestion
- **Backend (planned):** REST API
- **Payments (planned):** Stripe

---

## Future Work
- Compatibility analysis between partners
- Multimodal input: palm image analysis (hand lines)
- Streaming responses
- Advanced query routing
- Online evaluation and A/B testing

---

## Disclaimer
This project demonstrates applied LLM and RAG system design. It does not 
make scientific claims about numerology and is intended for educational 
and engineering purposes.

---

## Author: citizen404
Built as an applied ML & systems engineering project focused on real-world 
LLM usage patterns and production considerations. 
