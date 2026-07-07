21. Your RAG chatbot keeps returning factually wrong answers even though the correct information is in the knowledge base. How do you debug this?


**Answer (Interview - Brief):**

"I debug a RAG chatbot by checking each stage of the pipeline:

1. **Verify document ingestion** – Ensure the correct documents were indexed.
2. **Check chunking** – Adjust chunk size and overlap if important context is being split.
3. **Evaluate embeddings** – Confirm the embedding model captures the document semantics well.
4. **Inspect retrieval** – Verify the correct chunks are being retrieved by tuning `top-k` or using hybrid search.
5. **Review the prompt** – Make sure the LLM is instructed to answer only from the retrieved context.
6. **Check reranking** – Use a reranker to improve the relevance of retrieved chunks if needed.
7. **Evaluate outputs** – Measure retrieval quality, faithfulness, and answer correctness, then iterate based on the results.

**Short answer:**
"I debug by checking document indexing, chunking, embeddings, retrieval quality, prompt design, and reranking. I verify that the correct context is retrieved and ensure the LLM is instructed to answer only from that context."

22. You are asked to build a chatbot that answers questions about a 500-page technical manual. Walk me through your approach from scratch.


**Answer (Interview - Brief):**

"I would build this as a **RAG-based chatbot**.

1. **Ingest the document** – Extract text from the 500-page PDF and clean it.
2. **Chunk the content** – Split it into meaningful chunks (around 500–1000 tokens with overlap).
3. **Generate embeddings** – Create embeddings for each chunk using an embedding model.
4. **Store in a vector database** – Store the embeddings in a vector database like Pinecone or Chroma.
5. **Retrieve relevant chunks** – Convert the user's question into an embedding and retrieve the most relevant chunks using vector or hybrid search.
6. **Generate the answer** – Pass the retrieved context and the user's question to the LLM with a prompt instructing it to answer only from the provided context.
7. **Evaluate and optimize** – Measure retrieval quality, faithfulness, and latency, then improve chunking, prompts, or retrieval as needed."

**Short answer:**
"I would extract and chunk the manual, generate embeddings, store them in a vector database, retrieve relevant chunks for each query, and use an LLM with a RAG prompt to generate answers grounded in the retrieved context. Then I'd evaluate and optimize retrieval accuracy and response quality."

23. A user reports the AI agent is taking 10 seconds to respond. What steps do you take to diagnose and fix the latency? 

**Answer (Interview - Brief):**

"I would profile the entire pipeline to identify where the latency occurs.

1. **Measure each stage** – Embedding generation, vector search, LLM inference, tool/API calls, and network latency.
2. **Optimize retrieval** – Reduce `top-k`, improve indexing, or use hybrid search only when needed.
3. **Optimize the prompt** – Shorten prompts and reduce unnecessary context to lower token usage.
4. **Use a faster model** – Choose a smaller or faster LLM if it meets quality requirements.
5. **Enable streaming** – Stream responses so users see output immediately.
6. **Add caching** – Use semantic caching for repeated queries and cache embeddings where possible.
7. **Parallelize tasks** – Run independent tool calls or retrieval operations concurrently.

**Short answer:**
"I would profile each step of the pipeline, identify the bottleneck, optimize retrieval and prompts, reduce token usage, enable streaming, use caching, parallelize tasks where possible, and switch to a faster model if needed."

24. You have deployed an agent and a user found a way to make it ignore its system prompt by saying 'ignore all previous instructions.' How do you defend against this?

**Answer (Interview - Brief):**

"I defend against prompt injection by treating all user input as untrusted. I use a strong system prompt that has higher priority than user instructions, validate and sanitize inputs, and ensure the agent follows only trusted instructions. I also restrict tool access with permission checks, validate tool outputs, and use guardrails to detect and block prompt injection attempts. For RAG, I instruct the model to use only the retrieved context and ignore any malicious instructions inside documents."

**Short answer:**
"I protect against prompt injection by using a strong system prompt, treating user input as untrusted, adding input validation and guardrails, restricting tool access, and ensuring the agent follows only trusted instructions rather than commands like 'ignore previous instructions.'"

25. You need to build an agent that can query a SQL database. How do you do it safely?

**Answer (Interview - Brief):**

"I would build the SQL agent with security as the top priority.

1. Use a **read-only database user** so the agent cannot modify or delete data.
2. Restrict access to only the required tables and columns.
3. Validate and sanitize user input to prevent SQL injection.
4. Generate only **SELECT** queries and block commands like `INSERT`, `UPDATE`, `DELETE`, `DROP`, or `ALTER`.
5. Validate or review generated SQL before execution.
6. Limit the number of returned rows and set query timeouts.
7. Log and monitor all executed queries for auditing.

**Short answer:**
"I use a read-only database account, allow only SELECT queries, validate inputs and generated SQL, restrict table access, set query limits and timeouts, and log all queries. This keeps the SQL agent secure while allowing safe data retrieval."


26. Your team is using GPT-4 for everything but costs are getting out of control. How do you reduce costs without killing quality?


**Answer (Interview - Brief):**

"I would reduce costs by optimizing the pipeline instead of relying on GPT-4 for every request.

1. Use a **smaller, cheaper model** for simple tasks and reserve GPT-4 for complex reasoning.
2. Implement **semantic caching** to reuse responses for similar queries.
3. Reduce **prompt and context size** by retrieving only the most relevant chunks.
4. Optimize **chunking** and `top-k` retrieval to avoid sending unnecessary tokens.
5. Use **streaming** and batch requests where appropriate.
6. Monitor token usage and optimize prompts regularly.
7. Fine-tune or use specialized models for repetitive tasks if cost-effective.

**Short answer:**
"I reduce costs by routing simple tasks to smaller models, using semantic caching, minimizing prompt and context size, optimizing retrieval, monitoring token usage, and reserving GPT-4 only for complex queries. This maintains quality while significantly lowering API costs."

27. You are asked to add memory to a chatbot so it remembers what users told it in previous sessions. How do you build this?

**Answer (Interview - Brief):**

"I would implement **persistent memory** by storing user-specific information in a database instead of keeping it only in the conversation context.

1. Assign each user a unique ID.
2. Store conversation history and important user preferences in a database or vector database.
3. On a new session, retrieve the relevant memories using the user ID.
4. Summarize long conversations to reduce token usage.
5. Inject only the relevant memories into the prompt before calling the LLM.
6. Update the stored memory after each conversation while respecting privacy and user consent.

This allows the chatbot to remember preferences and past interactions across sessions without exceeding the model's context window."

**Short answer:**
"I store user-specific memories in a persistent database, retrieve relevant information at the start of each session, summarize long histories, and include only the relevant memories in the prompt. This enables the chatbot to remember users across sessions while keeping token usage low."

28. You join a project mid-way and find there are no tests for any of the LLM-powered features. What do you do?

**Answer (Interview - Brief):**

"I would start by creating a **test suite** for the LLM features.

1. Build a benchmark dataset of representative prompts and expected outputs.
2. Add **unit tests** for prompt formatting, parsing, and tool calls.
3. Add **integration tests** for the complete RAG or agent workflow.
4. Evaluate LLM responses using metrics such as **answer correctness, faithfulness, and relevance**.
5. Add **regression tests** to compare outputs after prompt or model changes.
6. Automate the tests in the CI/CD pipeline so every change is validated before deployment.

This helps catch regressions and ensures the system remains reliable as it evolves."

**Short answer:**
"I would create benchmark datasets, add unit and integration tests, evaluate response quality with metrics like correctness and faithfulness, add regression tests, and automate everything in the CI/CD pipeline."

29. A client wants a chatbot that answers questions about their products but should never recommend competitor products. How do you enforce this?


**Answer (Interview - Brief):**

"I would enforce this using multiple layers of control:

1. **System prompt** – Clearly instruct the model to answer only about the client's products and not recommend competitors.
2. **RAG** – Retrieve information only from the client's approved product documentation and knowledge base.
3. **Guardrails** – Add rules to detect and block competitor recommendations in the response.
4. **Output validation** – Check the generated response before sending it to the user and regenerate if it violates the policy.
5. **Testing** – Create test cases with competitor-related questions to verify the chatbot consistently follows the policy.

**Short answer:**
"I would use a strong system prompt, retrieve answers only from the client's knowledge base, add guardrails and output validation to block competitor recommendations, and test the chatbot with competitor-related queries to ensure compliance."

30. You need to index and make searchable 50,000 PDF documents. What is your ingestion pipeline strategy?

**Answer (Interview - Brief):**

"For 50,000 PDFs, I would build a scalable, asynchronous ingestion pipeline.

1. **Extract text** from each PDF and clean the content.
2. **Chunk the text** into 500–1000 token chunks with overlap.
3. **Generate embeddings** for each chunk in batches.
4. **Store embeddings** and metadata (document ID, page number, section) in a vector database.
5. **Use parallel processing** with queues/workers to process many PDFs concurrently.
6. **Track ingestion status**, log failures, and retry failed jobs.
7. **Support incremental indexing**, so only new or updated PDFs are reprocessed.
8. **Optimize retrieval** with metadata filters and, if needed, hybrid search (BM25 + vector search).

**Short answer:**
"I would build a parallel ingestion pipeline that extracts text, chunks documents, generates embeddings in batches, stores them with metadata in a vector database, uses queues and workers for scalability, retries failed jobs, and supports incremental re-indexing."

31. Your agent sometimes loops calling the same tool 5 to 6 times before stopping. How do you fix this?


**Answer (Interview - Brief):**

"I would first inspect the agent logs to understand why it's repeatedly calling the same tool. Then I would:

1. Set a **maximum iteration limit** to stop infinite loops.
2. Detect **repeated tool calls** with the same input and terminate or ask the user for clarification.
3. Improve the **system prompt** so the agent knows when to stop and return a final answer.
4. Validate tool outputs to ensure the agent receives the information it expects.
5. Use **LangGraph state** or memory to track previous actions and avoid repeating them.
6. Add logging and monitoring to identify recurring loop patterns and refine the workflow.

**Short answer:**
"I would set a maximum iteration limit, detect repeated tool calls with the same inputs, improve the agent prompt and stopping conditions, validate tool outputs, and use state tracking to prevent the agent from repeating the same action."


32. How would you approach building a multi-language chatbot that needs to support English, Hindi, and Spanish?

**Answer (Interview - Brief):**

"I would design the chatbot with multilingual support from end to end.

1. **Detect the user's language** automatically or let the user choose it.
2. Use a **multilingual LLM** that supports English, Hindi, and Spanish.
3. Build a **multilingual RAG pipeline** using multilingual embedding models so retrieval works across languages.
4. Store document metadata, including language, and apply language-based filtering when retrieving.
5. Return responses in the **same language** as the user's query.
6. Test with native-language datasets to evaluate accuracy, retrieval quality, and translation consistency.

**Short answer:**
"I would detect the user's language, use a multilingual LLM and multilingual embeddings, retrieve the relevant documents in the appropriate language, and generate responses in the user's language. I would also evaluate the chatbot with multilingual test cases to ensure quality."

33. You discover that your production chatbot has been leaking sensitive customer data from one user's conversation into another user's response. How do you handle this?

**Answer (Interview - Brief):**

"This is a **high-priority security incident**, so I would act immediately.

1. **Contain the issue** by disabling the affected feature or rolling back the deployment.
2. **Identify the root cause**—check session management, memory isolation, caching, conversation IDs, and retrieval logic to ensure user data is properly separated.
3. **Fix the issue** by enforcing strict user/session isolation, scoping retrieval and memory by user ID, and clearing any shared or incorrect caches.
4. **Validate the fix** with security and regression tests to confirm no cross-user data leakage.
5. **Monitor production** closely after deployment and review logs to understand the scope of the incident.
6. **Notify stakeholders and affected customers** as required by company policy and applicable privacy regulations.

**Short answer:**
"I would treat it as a critical security incident: contain it immediately, identify the root cause, enforce strict user/session isolation, fix any shared memory or caching issues, validate with security tests, monitor production, and follow the organization's incident response and notification procedures if required."


34. You need to build an agent that can browse the web to answer questions. What tools and approaches would you use? 

**Answer (Interview - Brief):**

"I would build the agent using **LangChain** or **LangGraph** with a web search tool and browser tool.

1. Use a **search API** to find relevant web pages.
2. Retrieve and extract content from trusted websites.
3. Summarize the retrieved information with an LLM.
4. Use a **ReAct** or tool-calling agent so it can decide when to search the web.
5. Add source citations, timeouts, and error handling.
6. Cache frequent searches and restrict the agent to trusted domains for better reliability and security.

**Short answer:**
"I would use LangChain or LangGraph with a web search API and browser tool. The agent searches the web, retrieves relevant pages, summarizes the content with an LLM, cites sources, and uses guardrails, caching, and error handling for reliable responses."

35. A product manager wants you to add a feature where the AI auto-generates and sends weekly summary emails. What questions do you ask before building? 

**Answer (Interview - Brief):**

"Before building, I'd clarify the requirements:

1. **Who** should receive the weekly emails?
2. **What data** should be summarized?
3. **What is the email format** (template, length, tone)?
4. **When** should emails be sent (day, time, time zone)?
5. **How** will users receive them (email provider like SMTP or SendGrid)?
6. **Can users review or edit** the summary before it's sent?
7. **What happens if the AI is unsure** or no data is available?
8. **What security and privacy requirements** apply to the data?
9. **How will success be measured** (accuracy, open rate, user feedback)?

**Short answer:**
"I would clarify the recipients, data source, summary format, schedule, email service, approval workflow, failure handling, security/privacy requirements, and success metrics before starting the implementation."


