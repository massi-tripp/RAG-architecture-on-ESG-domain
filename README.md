# RAG Architecture for the ESG Domain
As part of the "Large Scale Data Management" course at the University of Milano-Bicocca, I developed an intelligent system based on the Retrieval-Augmented Generation (RAG) paradigm, specifically applied to the ESG (Environmental, Social, Governance) domain.

The goal of the project was to build a system capable of answering complex user queries by integrating unstructured ESG data, a semantic Knowledge Graph, and large language models (LLMs). The workflow consisted of several key stages:

- Data Acquisition and Preprocessing:
I selected and downloaded a comprehensive ESG dataset from the World Bank ESG Data Portal, covering 73 indicators across 200+ countries from 2010 to 2023. After thorough cleaning and transformation (e.g., wide-to-long reshaping, mapping continents, removing nulls), I generated over 116,000 textual chunks summarizing each ESG observation.

- Semantic Vectorization:
Each chunk was embedded using the all-MiniLM-L6-v2 model to obtain 384-dimensional semantic vectors, indexed with FAISS to enable efficient similarity search.

- Knowledge Graph Integration:
I enriched the system by creating an RDF-based Knowledge Graph using rdflib, representing ESG data in triples. This allowed SPARQL-based semantic expansion and structured context retrieval during query answering.

- RAG System Implementation:
The architecture was implemented using the LangChain framework. It combined vector-based document retrieval with local LLMs such as Phi-2 and Phi-3.5 Mini for answer generation. Metadata was included to contextualize responses geographically and temporally.

- Prompt Engineering:
I tested several prompting strategies: Direct Retrieval, Chain-of-Thought, Fallback Hybrid, and an optimized final prompt that integrated retrieval, KG context, and in-context examples. The optimized prompt achieved the highest accuracy (80%).

- Evaluation and Benchmarking:
A custom benchmark of 35 questions was designed to test ESG-related queries (Environmental, Social, Governance), out-of-scope handling, and different reasoning styles. I conducted both qualitative and quantitative evaluations using manual accuracy scoring and ROUGE-L metrics.

- Performance Analysis:
I analyzed the trade-off between response length, accuracy, and latency. The optimized method produced concise, accurate responses at the cost of higher computational time, while fallback strategies were faster but less reliable.

This project demonstrated how a carefully engineered RAG system, enhanced with semantic retrieval and prompt optimization, can effectively answer domain-specific questions in ESG analysis. It also serves as a replicable pipeline for building domain-specific question answering systems.
