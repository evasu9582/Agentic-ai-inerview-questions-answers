36. Tell me about a time you had to learn a new AI framework or tool quickly to deliver a project?

**Answer (Interview - Brief):**

"One example was when I needed to build a RAG-based chatbot and had to learn **LangChain** quickly. I started with the official documentation, built a small proof of concept, and then integrated document loading, chunking, embeddings, vector search, and prompt templates into the project. After validating the prototype, I optimized retrieval, prompts, and performance. By learning incrementally and testing each component, I was able to deliver the project on time."

**Short answer:**
"I had to learn LangChain quickly for a RAG chatbot project. I studied the documentation, built a prototype, integrated document retrieval and vector search, tested each component, and successfully delivered the solution within the project timeline."

37. Describe a time you pushed back on a technical decision made by someone more senior. What happened?

**Answer (Interview - Brief):**

"On one project, a senior engineer suggested sending the entire document to the LLM for every query. I was concerned about high token costs, slower response times, and context limits. I proposed using a **RAG architecture** instead, where only the most relevant document chunks are retrieved and sent to the model. I built a small prototype comparing both approaches, and it showed lower costs, faster responses, and better scalability. Based on the results, the team adopted the RAG approach."

**Short answer:**
"A senior engineer wanted to send the full document to the LLM. I suggested using RAG with vector search instead, built a prototype to compare both approaches, and demonstrated lower cost and better performance. The team agreed and adopted the RAG solution."

38. Tell me about a project where something went wrong. What was your role and what did you do?

**Answer (Interview - Brief):**

"In one RAG chatbot project, users reported that the chatbot was giving inaccurate answers even though the information existed in the documents. My role was to investigate and fix the issue. I analyzed the pipeline and found that the chunk size was too large, retrieval quality was poor, and the prompt didn't clearly instruct the model to use only the retrieved context.

I reduced the chunk size, added chunk overlap, improved retrieval by tuning the search parameters, and updated the prompt to answer only from the retrieved context. After these changes, the chatbot's accuracy improved significantly, and users received more reliable answers."

**Short answer:**
"In a RAG chatbot project, retrieval quality caused incorrect answers. I identified the issue, optimized chunking and retrieval, improved the prompt, and increased the chatbot's accuracy and reliability."

39. How do you handle disagreements with a teammate about the best technical approach?

**Answer (Interview - Brief):**

"I handle technical disagreements by focusing on data rather than opinions. First, I listen to my teammate's perspective to understand their reasoning. Then, we discuss the trade-offs, such as performance, scalability, cost, and maintainability. If we're still unsure, I suggest building a small prototype or proof of concept and compare the results. Once we have evidence, we choose the approach that best meets the project's requirements."

**Short answer:**
"I listen to my teammate's perspective, discuss the trade-offs, and, if needed, build a small prototype to compare approaches. I base the final decision on data and project requirements rather than personal preference."

40. Describe a situation where you had to explain a complex AI concept to a non-technical stakeholder.

**Answer (Interview - Brief):**

"In one project, I needed to explain how a **RAG chatbot** worked to a product manager who didn't have an AI background. Instead of discussing embeddings and vector databases, I used a simple analogy: I explained that the chatbot first **looks up the most relevant pages in a company manual**, like a person using an index, and then uses those pages to answer the question. I also explained that this approach makes the answers more accurate because it relies on the company's documents rather than only the model's built-in knowledge. This helped the stakeholder understand the design and approve the solution."

**Short answer:**
"I explained RAG using the analogy of looking up information in a manual before answering a question. By avoiding technical jargon and using simple examples, I helped the stakeholder understand how the chatbot worked and why it was more accurate."

41. Tell me about a time you improved a process or workflow in your team related to AI development.

**Answer (Interview - Brief):**

"In one AI project, I noticed that prompt changes were being made without any structured testing, which sometimes caused regressions. I proposed creating a standard evaluation workflow with a benchmark dataset, regression tests, and prompt versioning. We also tracked metrics such as answer correctness, faithfulness, and latency before every release. This made deployments more reliable, reduced production issues, and gave the team confidence when updating prompts or models."

**Short answer:**
"I improved our AI development process by introducing prompt versioning, benchmark test datasets, and regression testing. This reduced regressions, improved response quality, and made releases more reliable."

42. How do you stay updated with the latest developments in the Agentic AI space?

**Answer (Interview - Brief):**

"I stay updated by following official documentation and release notes for AI frameworks, reading research papers and technical blogs, experimenting with new tools through small prototype projects, and following AI communities and GitHub repositories. I also watch conference talks and webinars to learn about the latest best practices and emerging trends."

**Short answer:**
"I stay current by following official documentation, AI research papers, technical blogs, GitHub repositories, and AI communities. I also build small prototypes to gain hands-on experience with new frameworks and tools."

43.  Tell me about a time you had to deliver a project under a tight deadline. How did you manage it? 

**Answer (Interview - Brief):**

"In one project, I had to deliver a **RAG-based chatbot** within a very tight deadline. I first identified the core features needed for the MVP, such as document ingestion, vector search, and question answering, and postponed non-essential features. I broke the work into small tasks, built a working prototype early, and tested each component as I integrated it. I also communicated progress regularly with the team so we could resolve issues quickly. We delivered the project on time, and then improved performance and added enhancements in later iterations."

**Short answer:**
"I prioritized the MVP, broke the work into small tasks, built and tested incrementally, communicated regularly with the team, and delivered the RAG chatbot on time. After release, we optimized and added additional features."

44. What motivates you to work in the Agentic AI space specifically? 

**Answer (Interview - Brief):**

"What motivates me about Agentic AI is the opportunity to build systems that can do more than just answer questions—they can reason, use tools, retrieve information, and automate real business workflows. I enjoy solving practical problems such as building RAG systems, AI agents, and workflow automation that improve productivity and user experience. Since the field is evolving rapidly, I also enjoy continuously learning and applying new frameworks and techniques."

**Short answer:**
"I'm motivated by building intelligent systems that can reason, use tools, and automate real-world tasks. I enjoy solving practical business problems with RAG and AI agents, and I like continuously learning as the Agentic AI ecosystem evolves."

45. Have you ever found a security vulnerability in an AI system you worked on? What did you do?

**Answer (Interview - Brief):**

"Yes. During testing of a RAG-based chatbot, I noticed it could be influenced by instructions embedded in retrieved documents, which is a form of **prompt injection**. I reported the issue, analyzed the impact, and implemented mitigations by strengthening the system prompt, treating retrieved content as untrusted, adding input and output guardrails, and restricting tool access. I also added test cases for prompt injection to ensure the issue did not reoccur."

> If you haven't actually experienced this, present it as a testing scenario rather than claiming it happened.

**Short answer:**
"During testing, I identified a prompt injection risk in the AI system. I strengthened the system prompt, treated retrieved content as untrusted, added guardrails and validation, restricted tool access, and added security tests to prevent similar issues in the future."



