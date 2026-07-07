1. What is LangChain, and how have you used it in a real project?

**LangChain** is a framework for building applications powered by Large Language Models (LLMs). It helps connect LLMs with data sources, APIs, tools, memory, and workflows.

**Real project example:** I used LangChain to build a **document Q&A chatbot** that reads PDFs, creates embeddings, stores them in a vector database, and uses an LLM to answer user questions based on the documents.

**Short answer:**
"LangChain is a framework for developing LLM-based applications. I used it to build a RAG chatbot that retrieves information from documents and generates accurate answers using an LLM."

2. Can you explain RAG and when you would use it versus fine-tuning?

**RAG (Retrieval-Augmented Generation)** is a technique where an LLM retrieves relevant information from external sources (like documents or databases) and uses that information to generate answers.

**Use RAG when:**

* You need up-to-date or private data.
* You want a chatbot to answer from company documents, manuals, or knowledge bases.
* You want to avoid retraining the model.

**Use fine-tuning when:**

* You want the model to learn a specific style, format, behavior, or task.
* You have a large amount of high-quality training examples.
* The knowledge itself does not change frequently.

**Short answer:**
"RAG is used to give an LLM external knowledge at runtime, while fine-tuning changes the model’s behavior through training. I would use RAG for dynamic company data and fine-tuning for specialized tasks or consistent output styles."

3. How does vector search work, and which vector databases have you worked with?


**Vector search** converts text into numerical vectors (embeddings). When a user asks a question, the query is also converted into a vector, and the system finds the most similar vectors using similarity search (such as cosine similarity). The retrieved documents are then passed to the LLM to generate an accurate answer.

**Vector databases I've worked with:**

* Pinecone – Cloud-based, scalable vector database for RAG applications.
* FAISS – Fast local vector search library developed by Meta.
* Chroma – Lightweight, open-source vector database for AI applications.

**Short answer:**
"Vector search works by converting text into embeddings and retrieving the most similar vectors using similarity search. I have worked with Pinecone, FAISS, and Chroma for building RAG-based applications."


4. What are embeddings and how do you choose the right embedding model?

**Embeddings** are numerical vector representations of text that capture its semantic meaning. They allow similar words or documents to be found using vector search, even if they don't contain the exact same keywords.

**How I choose an embedding model:**

* **Accuracy** for semantic search and retrieval.
* **Domain support** (general or specialized content).
* **Cost and latency** based on application needs.
* **Compatibility** with the LLM and vector database.

**Short answer:**
"Embeddings convert text into numerical vectors that capture semantic meaning. I choose an embedding model based on retrieval accuracy, domain relevance, cost, speed, and compatibility with the vector database and LLM. I've used embedding models from OpenAI and Hugging Face in RAG applications."

5. Explain how you implemented chunking in a RAG pipeline. What strategy did you use and why?

**Answer (Interview - Brief):**

"In my RAG pipeline, I used **recursive text chunking** with a chunk size of around **500–1000 tokens** and an overlap of **100–200 tokens**. The overlap helps preserve context between adjacent chunks so important information isn't lost at the boundaries.

I chose recursive chunking because it tries to split text at natural boundaries like paragraphs and sentences before splitting arbitrarily, which improves retrieval quality. After chunking, I generated embeddings for each chunk, stored them in a vector database, and retrieved the most relevant chunks during user queries."

**Short answer:**
"I used recursive text chunking with 500–1000 token chunks and 100–200 token overlap. This preserves context, improves retrieval accuracy, and creates meaningful chunks for embedding and vector search."


6. How do you handle prompt engineering in practice? Walk me through writing a prompt for a specific task.


**Answer (Interview - Brief):**

"In practice, I write prompts by clearly defining the **role**, **task**, **context**, **constraints**, and **expected output format**. I also include examples if needed to improve consistency.

For example, for a customer support chatbot:

**Prompt:**
*'You are a helpful customer support assistant. Answer the user's question using only the provided context. If the answer is not in the context, respond with "I don't know." Keep the answer concise and professional.'*

This approach reduces hallucinations and ensures the response follows the required format."

**Short answer:**
"I structure prompts with a clear role, task, context, constraints, and output format. For RAG applications, I instruct the model to answer only from the retrieved context and say 'I don't know' if the information is unavailable."


7. What is the difference between zero-shot, one-shot, and few-shot prompting?

**Zero-shot prompting:** The model performs a task without any examples—only instructions are provided.

**One-shot prompting:** The model is given one example before the actual task.

**Few-shot prompting:** The model is given multiple examples to help it understand the expected pattern or format.

**Short answer:**

* **Zero-shot:** Only instructions, no examples.
* **One-shot:** One example + task.
* **Few-shot:** Multiple examples + task for better accuracy and consistency.


8. Have you built an AI agent with tools? How did you define and wire up the tools?


**Answer (Interview - Brief):**

"Yes. I built an AI agent using **LangChain** that could answer questions, search documents, and call external APIs. I defined each tool as a function with a clear description and input schema, then registered those tools with the agent. Based on the user's query, the LLM selected the appropriate tool, executed it, and used the result to generate the final response.

For example, I integrated a document retriever for RAG and a weather API as separate tools, allowing the agent to choose the right one automatically."

**Short answer:**
"Yes. I built a LangChain agent with tools such as a document retriever and external APIs. I defined each tool as a function with a description and input schema, registered them with the agent, and let the LLM decide which tool to call based on the user's request."

9. What is LangGraph and how is it different from a standard LangChain chain?

**Answer (Interview - Brief):**

**LangGraph** is a framework for building **stateful, multi-step AI agents** using a graph-based workflow. It supports branching, loops, memory, and human-in-the-loop interactions.

A **LangChain chain** follows a mostly **linear sequence** of steps, while **LangGraph** models workflows as a **graph**, allowing the agent to make decisions, revisit previous steps, and maintain state across the process.

**Short answer:**
"LangGraph is used to build stateful, graph-based AI agents with branching, loops, and memory. Unlike a standard LangChain chain, which executes tasks linearly, LangGraph supports complex workflows and multi-step agent reasoning."

10. How do you evaluate the quality of a RAG system? What metrics do you use?

**Answer (Interview - Brief):**

"I evaluate a RAG system by measuring both **retrieval quality** and **answer quality**.

**Metrics I use:**

* **Retrieval Precision/Recall** – Checks whether the correct documents are retrieved.
* **Context Relevance** – Measures how relevant the retrieved chunks are to the query.
* **Answer Faithfulness** – Verifies that the answer is grounded in the retrieved context and avoids hallucinations.
* **Answer Relevance/Correctness** – Evaluates whether the response correctly answers the user's question.
* **Latency** – Measures how quickly the system responds.

I also perform manual testing with a benchmark set of question-answer pairs to validate real-world performance."

**Short answer:**
"I evaluate RAG using retrieval precision/recall, context relevance, answer faithfulness, answer correctness, and latency. I also test with benchmark Q&A datasets to ensure accurate and reliable responses."

11. Explain the ReAct prompting pattern and when you would use it for an agent.

**Answer (Interview - Brief):**

**ReAct (Reason + Act)** is a prompting pattern where an AI agent alternates between **reasoning** about a problem and **taking actions** by calling tools or APIs. The agent observes the results of those actions and continues until it reaches the final answer.

I use ReAct when an agent needs to perform **multi-step tasks**, such as searching documents, querying databases, calling APIs, or using calculators before generating a response.

**Short answer:**
"ReAct combines reasoning and tool use. The agent thinks about the next step, calls the appropriate tool, observes the result, and repeats until it can answer. I use it for multi-step tasks that require external tools or data."

12. What is semantic caching and how did you implement it to reduce LLM API costs?

**Answer (Interview - Brief):**

**Semantic caching** stores answers based on the **meaning** of a query rather than the exact text. When a new query arrives, its embedding is compared with cached query embeddings. If the similarity score is above a threshold, the cached response is returned instead of calling the LLM, reducing API costs and improving response time.

In my RAG project, I generated embeddings for user queries, stored them in a vector database, and performed a similarity search before invoking the LLM. If a similar query was found, I returned the cached response; otherwise, I generated a new answer and added it to the cache.

**Short answer:**
"Semantic caching uses embeddings to find semantically similar previous queries. I implemented it by storing query embeddings and responses in a vector database, checking similarity before calling the LLM, and serving cached answers when the similarity exceeded a threshold. This reduced API costs and improved latency."

13. How do you handle streaming responses from an LLM in a web application?


**Answer (Interview - Brief):**

"In a web application, I enable the LLM's **streaming** mode so tokens are generated incrementally instead of waiting for the full response. On the backend, I stream the tokens using **Server-Sent Events (SSE)** or **WebSockets**, and the frontend updates the UI in real time as new tokens arrive. This improves the user experience by reducing perceived latency."

**Short answer:**
"I enable LLM streaming, send tokens to the frontend using SSE or WebSockets, and update the UI as each token arrives. This provides faster, real-time responses and a better user experience."

14. What is the difference between ConversationBufferMemory and ConversationSummaryMemory?

**Answer (Interview - Brief):**

**ConversationBufferMemory** stores the **entire conversation history**, providing full context but using more tokens as the conversation grows.

**ConversationSummaryMemory** stores a **summarized version** of the conversation, reducing token usage while preserving the key information.

**When to use:**

* **ConversationBufferMemory:** Best for short conversations where full context is important.
* **ConversationSummaryMemory:** Best for long conversations to save tokens and reduce costs.

**Short answer:**
"ConversationBufferMemory keeps the full chat history, while ConversationSummaryMemory keeps a summarized version. I use BufferMemory for short chats and SummaryMemory for long conversations to reduce token usage and API costs."

15. How do you implement output validation for structured data coming from an LLM?


 **Answer (Interview - Brief):**

"I use **structured output schemas** with validation libraries such as **Pydantic**. I define the expected fields, data types, and required constraints, then validate the LLM's response against the schema. If validation fails, I either retry with a stricter prompt or use automatic error handling to regenerate the output."

**Short answer:**
"I define a schema using Pydantic, validate the LLM's structured output against it, and retry or regenerate the response if validation fails. This ensures consistent and reliable JSON outputs."

16. How do temperature and top-p affect LLM output, and how do you set these in practice?

**Answer (Interview - Brief):**

**Temperature** controls the randomness of the output.

* **Low (0–0.3):** More deterministic and consistent.
* **High (0.7–1.0):** More creative and diverse.

**Top-p (nucleus sampling)** limits token selection to the smallest set of tokens whose cumulative probability reaches *p*.

* **Lower top-p (e.g., 0.8):** More focused responses.
* **Higher top-p (e.g., 1.0):** More diverse responses.

**In practice:**

* For **RAG, Q&A, and code generation**, I use **temperature = 0–0.2** for accurate, consistent answers.
* For **content writing or brainstorming**, I use **temperature = 0.7–0.9** for more creativity.
* I typically leave **top-p at 1.0** and mainly adjust temperature, since changing both together often provides little additional benefit.

**Short answer:**
"Temperature controls randomness, while top-p controls the range of candidate tokens considered during generation. For RAG and factual tasks, I use a low temperature (0–0.2) and usually keep top-p at 1.0. For creative tasks, I increase the temperature to around 0.7–0.9."


17. How have you implemented hybrid search combining keyword and vector search?

**Answer (Interview - Brief):**

"I implemented **hybrid search** by combining **keyword search (BM25)** with **vector similarity search**. When a user submits a query, I run both searches in parallel. The keyword search captures exact matches, while the vector search retrieves semantically similar content. I then merge and rerank the results before passing the top documents to the LLM.

This approach improves retrieval accuracy because it handles both exact keyword queries and natural language queries effectively."

**Short answer:**
"I combined BM25 keyword search with vector search. I executed both in parallel, merged and reranked the results, and sent the top-ranked documents to the LLM. This improved retrieval by capturing both exact keyword matches and semantic similarity."

18. What is an agent loop and how do you prevent it from running indefinitely?
**Answer (Interview - Brief):**

"An **agent loop** is the cycle where an AI agent repeatedly **reasons, selects a tool, executes it, observes the result, and decides the next step** until it reaches a final answer.

To prevent it from running indefinitely, I set a **maximum iteration limit**, define clear **termination conditions** (such as when the task is completed or a final answer is generated), and add **timeouts** and **error handling**. I also monitor repeated actions and stop the agent if it keeps calling the same tool without making progress."

**Short answer:**
"An agent loop is the repeated cycle of reasoning and tool execution. I prevent infinite loops by setting a maximum number of iterations, defining clear stop conditions, using timeouts, and detecting repeated tool calls without progress."

19.  How do you manage secrets and API keys securely in an Agentic AI application? 

**Answer (Interview - Brief):**

"I never hardcode API keys in the source code. I store secrets in **environment variables** or a **secret management service**. The application reads them securely at runtime. I also use role-based access, rotate keys regularly, and avoid logging or exposing secrets in responses. In production, I use services like cloud secret managers or vault solutions."

**Short answer:**
"I manage API keys using environment variables or a secret manager, never hardcode them, restrict access with IAM/roles, rotate keys regularly, and ensure they are never logged or exposed to users."


20. Explain how you would add a human-in-the-loop step to an agent workflow.

**Answer (Interview - Brief):**

"I add a **human-in-the-loop (HITL)** step by introducing an approval checkpoint before the agent performs critical actions. The agent completes its reasoning, prepares a proposed action, and pauses. A human reviews, approves, rejects, or modifies the action. Based on that decision, the workflow either continues, retries, or stops.

This is especially useful for high-risk tasks such as financial transactions, deleting data, sending emails, or making important business decisions."

**Short answer:**
"I add a human approval step before critical actions. The agent pauses after generating a proposed action, waits for user approval or edits, and then continues or stops based on the decision. This improves safety and accuracy."


