# Shared Concept Index

> [!info] Purpose
> This index connects concepts to both sources of learning:
> - topic notes, which explain the technique
> - lab/project notes, which show where the technique was practiced or demonstrated

Use this note when you ask: "Where did I learn this concept, and where did I see it applied?"

---

## APIs and LLM Calls

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| OpenAI API basics | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/W1D4 Product Listing Vision Lab]], [[Labs/Project 2 Report Generator]] | Client setup, model calls, response handling |
| Responses API | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/W1D4 Product Listing Vision Lab]], [[Labs/W2D1 Podcast Project]] | `client.responses.create`, `response.output_text` |
| Chat completions | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/W2D4 News Summarizer Lab]], [[Labs/Project 2 Report Generator]] | Message arrays, system/user roles |
| Vision input | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/W1D4 Product Listing Vision Lab]] | Images as input, base64 encoding, product listings |
| Structured outputs | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/W1D4 Product Listing Vision Lab]], [[Labs/W2D4 Python Low Code JSON Validation Lab]] | Pydantic models, strict fields, parsed outputs |
| JSON validation | [[Engineering/Code Quality and Automation]] | `m1_04_python.ipynb`, `m1_08_generative-ai.ipynb` | [[Labs/W1D2 Titanic JSON Lab]], [[Labs/W2D4 Python Low Code JSON Validation Lab]] | JSON export, malformed JSON, validation errors |
| Token tracking | [[APIs/Multi-Provider]] | `m2_02_integration-patterns.ipynb` | [[Labs/W1D4 Product Listing Vision Lab]], [[Labs/W2D4 News Summarizer Lab]], [[Labs/Project 2 Report Generator]] | Usage, cost estimates, budgets |
| Model selection | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/Project 2 Report Generator]] | Model discovery, defaults, generation settings |
| Speech and embedding APIs | [[APIs/OpenAI API]] | `m1_08_generative-ai.ipynb` | [[Labs/W1D5 Whisper STT Evaluation Lab]], [[Labs/W2D5 Native OpenAI RAG Lab]] | Whisper transcription, embeddings, native OpenAI RAG calls |
| API-driven research summarization | [[APIs/OpenAI API]] | applied Week 4 lab material | [[Labs/W4D3 arXiv n8n Notion Research Summarizer Lab]] | Search API, model summarization, structured downstream writes |

---

## Prompting

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| Zero-shot prompting | [[Prompting/Prompting Basics]] | `m2_02_advanced-prompt-techniques.ipynb` | [[Labs/W2D3 Prompt Engineering Lab]] | Direct instruction without examples |
| One-shot prompting | [[Prompting/Prompting Basics]] | `m2_02_advanced-prompt-techniques.ipynb` | [[Labs/W2D3 Prompt Engineering Lab]] | One example to establish output format |
| Few-shot prompting | [[Prompting/Prompting Basics]] | `m2_02_advanced-prompt-techniques.ipynb` | [[Labs/W2D3 Prompt Engineering Lab]] | Multiple examples to teach a pattern |
| Role prompting | [[Prompting/Prompting Basics]] | `m2_02_advanced-prompt-techniques.ipynb` | [[Labs/W2D3 Prompt Engineering Lab]], [[Labs/W3D3 LangChain Complaint Handler Lab]] | Persona, expertise, system behavior |
| Chain-of-thought prompting | [[Prompting/Prompting Basics]] | `m2_02_advanced-prompt-techniques.ipynb` | [[Labs/W2D3 Prompt Engineering Lab]] | Step-by-step reasoning instructions |
| Prompt testing | [[Prompting/Prompting Basics]] | `m2_02_advanced-prompt-techniques.ipynb` | [[Labs/W2D3 Prompt Engineering Lab]] | Repeated runs, inconsistency detection |
| Dynamic prompting | [[Prompting/Dynamic Prompting]] | `00_dynamic_prompting.ipynb` | [[Labs/Project 2 Report Generator]], [[Labs/W2D1 Podcast Project]] | Build prompts from runtime variables |
| Context injection | [[Prompting/Dynamic Prompting]] | `00_dynamic_prompting.ipynb` | [[Labs/W2D1 Podcast Project]], [[Labs/Project 2 Report Generator]], [[Labs/W2D5 RAG Chunking Lab]] | Insert source material or retrieved context into prompt |
| Prompt templates | [[Prompting/Dynamic Prompting]] | `00_dynamic_prompting.ipynb` | [[Labs/Project 2 Report Generator]] | Template files, placeholders, style/depth controls |
| Feedback prompting | [[Prompting/Dynamic Prompting]] | partial in Week 3 concepts | [[Labs/Project 2 Report Generator]] | Revise generated output using general and section feedback |

---

## Engineering and Code Quality

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| Helper functions | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | Many labs | Small reusable units with focused responsibilities |
| Refactoring | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | [[Labs/W2D4 Python Low Code JSON Validation Lab]], [[Labs/W3D3 LangChain Complaint Handler Lab]], [[Labs/Project 2 Report Generator]] | Split messy code into modules/functions |
| API wrappers | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | [[Labs/W2D4 News Summarizer Lab]], [[Labs/Project 2 Report Generator]] | Centralize provider calls and error behavior |
| Standard response objects | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | [[Labs/Project 2 Report Generator]] | Normalized payloads with success/error/usage |
| Unit tests | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | [[Labs/W2D4 News Summarizer Lab]], [[Labs/Project 2 Report Generator]] | `pytest`, fake clients, validation tests |
| Config handling | [[APIs/Multi-Provider]] | `m2_02_integration-patterns.ipynb` | [[Labs/W2D4 News Summarizer Lab]], [[Labs/W3D3 LangChain Complaint Handler Lab]], [[Labs/Project 2 Report Generator]] | API keys, model names, environment settings |
| Modular project structure | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | [[Labs/W2D1 Podcast Project]], [[Labs/W3D3 LangChain Complaint Handler Lab]], [[Labs/Project 2 Report Generator]] | Separate UI, processing, prompts, tools, data, LLM integration |

---

## API Reliability and Multi-Provider Systems

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| Exponential backoff | [[APIs/Reliability Patterns]] | `m2_01_api-fundamentals.ipynb` | partial in applied API work | Increasing retry delay |
| Jitter | [[APIs/Reliability Patterns]] | `m2_01_api-fundamentals.ipynb` | partial in applied API work | Randomized retry delays |
| Circuit breaker | [[APIs/Reliability Patterns]] | `m2_01_api-fundamentals.ipynb` | mostly official notebook | Stop repeated calls to failing service |
| Provider fallback | [[APIs/Multi-Provider]] | `m2_02_integration-patterns.ipynb` | [[Labs/W2D4 News Summarizer Lab]] | Try OpenAI, fall back to Anthropic |
| Provider chaining | [[APIs/Multi-Provider]] | `m2_02_integration-patterns.ipynb` | [[Labs/W2D4 News Summarizer Lab]] | Summarize with one provider, analyze with another |
| Rate limiting | [[APIs/Multi-Provider]] | `m2_02_integration-patterns.ipynb` | [[Labs/W2D4 News Summarizer Lab]] | RPM intervals, waiting between calls |
| Cost tracking | [[APIs/Multi-Provider]] | `m2_02_integration-patterns.ipynb` | [[Labs/W2D4 News Summarizer Lab]], [[Labs/Project 2 Report Generator]] | Pricing tables, usage aggregation, budgets |
| Async processing | [[Engineering/Code Quality and Automation]] | partial in integration ideas | [[Labs/W2D4 News Summarizer Lab]] | Concurrent article processing with a semaphore |
| Guardrail middleware | [[Ironhack/Frameworks/LangChain]], [[APIs/Reliability Patterns]] | applied Week 4 lab material | [[Labs/W4D1 LangChain Guardrails Lab]] | Input/output checks, PII redaction, policy gates |
| Workflow error handling | [[APIs/Reliability Patterns]], [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D4 n8n Error Handling and Scheduled Workflows Lab]] | Retry paths, error branches, scheduled recovery |

---

## Speech

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| STT | [[Speech/STT]] | `stt.ipynb` | [[Labs/W1D5 Whisper STT Lab]] | Whisper transcription |
| Prompted transcription | [[Speech/STT]] | `stt.ipynb` | [[Labs/W1D5 Whisper STT Lab]] | Vocabulary/context prompts for better transcription |
| Audio chunking | [[Speech/STT]] | `stt.ipynb` | [[Labs/W1D5 Whisper STT Lab]] | Split longer audio into smaller segments |
| Timestamps | [[Speech/STT]] | `stt.ipynb` | [[Labs/W1D5 Whisper STT Lab]] | Time-aligned transcript output |
| STT evaluation | [[Speech/STT]] | `speech_recognition_breaking_points.ipynb` | [[Labs/W1D5 Whisper STT Evaluation Lab]] | Compare providers with repeated samples and quality metrics |
| Word error rate | [[Speech/STT]] | `speech_recognition_breaking_points.ipynb` | [[Labs/W1D5 Whisper STT Evaluation Lab]] | Measure transcription accuracy against a reference |
| TTS | [[Speech/TTS]] | `tts.ipynb` | [[Labs/W2D1 Podcast Project]] | Generate speech from text |
| Voice selection | [[Speech/TTS]] | `tts.ipynb` | [[Labs/W2D1 Podcast Project]] | Map speakers to voices |
| Audio merging | [[Speech/TTS]] | `tts.ipynb` | [[Labs/W2D1 Podcast Project]] | Combine generated segments into one MP3 |

---

## RAG, Chunking, and Knowledge Context

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| Document loading | [[RAG/RAG Basics]] | `rag_intro.ipynb`, `rag_openai.ipynb` | [[Labs/W2D5 RAG Chunking Lab]], [[Labs/Project 2 Report Generator]] | PDFs, markdown files, source ingestion |
| Fixed-size chunking | [[RAG/RAG Basics]] | `rag_intro.ipynb` | [[Labs/W2D5 RAG Chunking Lab]] | Split text by fixed character length |
| Recursive chunking | [[RAG/RAG Basics]] | `rag_intro.ipynb` | [[Labs/W2D5 RAG Chunking Lab]] | Structure-aware text splitting |
| Token chunking | [[RAG/RAG Basics]] | partial in chunking concepts | [[Labs/W2D5 RAG Chunking Lab]] | Chunk by token count |
| Semantic chunking | [[RAG/RAG Optimization]] | partial advanced concept | [[Labs/W2D5 RAG Chunking Lab]] | Meaning-based chunk boundaries |
| Embeddings | [[RAG/RAG Basics]] | `rag_intro.ipynb`, `rag_openai.ipynb` | [[Labs/W2D5 RAG Chunking Lab]] | Convert text to vectors |
| Vector search | [[RAG/RAG Basics]] | `rag_intro.ipynb`, `rag_openai.ipynb` | [[Labs/W2D5 Native OpenAI RAG Lab]] | Similarity search over embeddings |
| Context assembly | [[RAG/RAG Basics]] | `rag_intro.ipynb` | [[Labs/Project 2 Report Generator]] | Build selected context from structured knowledge base |
| Native OpenAI RAG | [[RAG/RAG Basics]] | `rag_openai.ipynb` | [[Labs/W2D5 Native OpenAI RAG Lab]] | Embeddings, vector store lookup, grounded answer generation without LangChain |
| LLM relevance scoring | [[RAG/RAG Optimization]] | `rag_pipeline.ipynb` | [[Labs/W3D4 Relevance Scoring and Rerankers Lab]] | Score retrieved chunks with an LLM and explain why they match the query |
| Source metadata filtering | [[RAG/RAG Optimization]] | `rag_pipeline.ipynb` | [[Labs/W3D4 Relevance Scoring and Rerankers Lab]] | Compare PDF and podcast transcript retrieval separately |
| Grounded answer generation | [[RAG/RAG Basics]] | `rag_openai.ipynb`, `rag_pipeline.ipynb` | [[Labs/W3D4 Relevance Scoring and Rerankers Lab]] | Generate answers from selected retrieved context |

---

## LangChain and Agents

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| LangChain models | [[Ironhack/Frameworks/LangChain]] | `langchain_integration.ipynb` | [[Labs/W3D3 LangChain Complaint Handler Lab]] | `ChatOpenAI`, model setup |
| Messages | [[Ironhack/Frameworks/LangChain]] | `langchain_integration.ipynb` | [[Labs/W3D3 LangChain Complaint Handler Lab]] | User/system/AI message flow |
| Tools | [[Ironhack/Frameworks/LangChain]] | `langchain_integration.ipynb` | [[Labs/W3D3 LangChain Complaint Handler Lab]] | Callable functions exposed to the agent |
| Tool registry | [[Ironhack/Frameworks/LangChain]] | `langchain_integration.ipynb` | [[Labs/W3D3 LangChain Complaint Handler Lab]] | `TOOLS` list imported into the agent |
| Agents | [[Ironhack/Frameworks/LangChain]] | `langchain_integration.ipynb` | [[Labs/W3D3 LangChain Complaint Handler Lab]] | Model + tools + loop |
| Prompt separation | [[Ironhack/Frameworks/LangChain]] | partial in framework practice | [[Labs/W3D3 LangChain Complaint Handler Lab]] | Store system prompt outside agent runtime |
| Final answer extraction | [[Ironhack/Frameworks/LangChain]] | partial in agent examples | [[Labs/W3D3 LangChain Complaint Handler Lab]] | Read final `AIMessage` from agent result |
| MCP | [[Frameworks/MCP]] | `mcp_introduction.ipynb` | [[Labs/W3D5 MCP in LangChain Lab]] | External tool/resource server integration |
| MCP filesystem tools | [[Frameworks/MCP]] | `mcp_introduction.ipynb` | [[Labs/W3D5 MCP in LangChain Lab]] | Let an agent inspect files through a constrained MCP server |
| MCP Git tools | [[Frameworks/MCP]] | `mcp_introduction.ipynb` | [[Labs/W3D5 MCP in LangChain Lab]] | Let an agent inspect repository state through MCP |
| Direct API vs MCP | [[Frameworks/MCP]] | `mcp_introduction.ipynb` | [[Labs/W3D5 MCP in LangChain Lab]] | Compare explicit REST integration with standardized MCP tool access |
| MCP-enabled coding agents | [[Frameworks/MCP]], [[Agentic/Effective Context Engineering for AI Agents]] | applied Week 3 lab material | [[Labs/W3D5 MCP Setup in Codex and Claude Code Lab]] | Connect coding assistants to external servers and validate tool availability |
| Agent skills | [[Agentic/Agent Skills]] | `lessons/W4D2_AI_agent_skills` | [[Labs/W4D2 Reflection Skills Lab]] | Package repeatable agent behavior into `SKILL.md`, scripts, references, and assets |
| Progressive disclosure | [[Agentic/Agent Skills]], [[Agentic/Effective Context Engineering for AI Agents]] | `lessons/W4D2_AI_agent_skills` | [[Labs/W4D2 Reflection Skills Lab]] | Load skill metadata first, then detailed instructions only when needed |
| Skill description routing | [[Agentic/Agent Skills]] | `lessons/W4D2_AI_agent_skills` | [[Labs/W4D2 Reflection Skills Lab]] | Use the description field to trigger skills from user intent |
| Skills vs MCP | [[Agentic/Agent Skills]], [[Frameworks/MCP]] | `lessons/W4D2_AI_agent_skills`, `mcp_introduction.ipynb` | [[Labs/W3D5 MCP Setup in Codex and Claude Code Lab]] | Skills encode procedure; MCP exposes tools and services |
| Agent reflection skills | [[Agentic/Effective Context Engineering for AI Agents]], [[Agentic/Agent Skills]] | applied Week 4 lab material | [[Labs/W4D2 Reflection Skills Lab]] | Reflection prompts, skill instructions, iterative self-review |

---

## LangGraph and Workflow Orchestration

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| LangGraph state graphs | [[Ironhack/Frameworks/LangGraph]] | `langgraph.ipynb`, `langgraph_integration.ipynb` | [[Labs/W4D1 LangGraph Complaint Workflow Lab]] | Define a workflow as nodes, edges, and shared state |
| Typed workflow state | [[Ironhack/Frameworks/LangGraph]] | `langgraph.ipynb` | [[Labs/W4D1 LangGraph Complaint Workflow Lab]] | Pass structured state through each graph node |
| Deterministic AI workflows | [[Ironhack/Frameworks/LangGraph]] | `langgraph_integration.ipynb` | [[Labs/W4D1 LangGraph Complaint Workflow Lab]] | Use fixed stages when an AI process must be traceable |
| Structured investigation and resolution | [[Ironhack/Frameworks/LangGraph]] | `langgraph_integration.ipynb` | [[Labs/W4D1 LangGraph Complaint Workflow Lab]] | Move from intake to validation, investigation, resolution, and closure |
| Workflow path tracking | [[Ironhack/Frameworks/LangGraph]] | partial in Week 4 workflow practice | [[Labs/W4D1 LangGraph Complaint Workflow Lab]] | Record which nodes executed for debugging and review |

---

## Low-Code and App Automation

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| n8n trigger nodes | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D2 n8n Node Study Guide Lab]], [[Labs/W4D3 n8n Multi-App Integration Lab]] | Start workflows from chat, schedule, manual execution, or Telegram |
| n8n JSON item flow | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D2 n8n Node Study Guide Lab]], [[Labs/W4D3 n8n Multi-App Integration Lab]] | Track how each node receives and returns structured JSON |
| Code node transformations | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D2 n8n Node Study Guide Lab]] | Convert model output into app-ready Notion block JSON |
| Split Out | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D2 n8n Node Study Guide Lab]] | Convert an array field into one item per element |
| Multi-app workflow | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D3 n8n Multi-App Integration Lab]] | Move Telegram message data into Airtable records |
| Research-to-Notion workflow | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D3 arXiv n8n Notion Research Summarizer Lab]] | Search papers, summarize, transform fields, persist to Notion |
| n8n operational hardening | [[n8n/n8n Workflows]], [[APIs/Reliability Patterns]] | applied Week 4 lab material | [[Labs/W4D4 n8n Error Handling and Scheduled Workflows Lab]] | Error workflows, scheduled execution, duplicate/idempotency guards |

---

## ML and Data

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| Data manipulation | [[Foundations/Data and Pipeline Foundations]] | `m1_04_python.ipynb` | [[Labs/W1D2 Titanic JSON Lab]] | Load, inspect, transform, export data |
| Feature engineering | [[ML/Classical ML]] | `m1_06_sklearn.ipynb` | [[Labs/W1D2 Titanic JSON Lab]], [[Labs/W1D3 Sklearn Model Training Lab]] | Create model-ready columns |
| KNN classification | [[ML/Classical ML]] | `m1_06_sklearn.ipynb` | [[Labs/W1D3 Sklearn Model Training Lab]] | Breast cancer and churn prediction |
| Model evaluation | [[ML/Classical ML]] | `m1_06_sklearn.ipynb` | [[Labs/W1D3 Sklearn Model Training Lab]] | Accuracy, reports, confusion matrices, k comparison |
| Neural networks | [[ML/Deep Learning]] | `m1_04_deep-learning.ipynb` | [[Labs/W1D3 Neural Network Lab]] | Simple image classification |
| Rule-based monitoring | [[Foundations/Data and Pipeline Foundations]] | applied Week 1 project material | [[Labs/W1D1 HomeGuard System Lab]] | Threshold rules, alerts, simple sensor-driven decisions |

---

## End-to-End Pipelines

| Concept | Topic Note | Official Course Source | Lab / Project Source | What It Covers |
|---|---|---|---|---|
| Gradio app | no dedicated topic note yet | not central in official notes | [[Labs/W2D1 Podcast Project]], [[Labs/Project 2 Report Generator]] | User interface around AI pipeline |
| Multi-step AI workflow | [[Engineering/Code Quality and Automation]] | `m2_02_automation-with-python.ipynb` | [[Labs/W2D1 Podcast Project]], [[Labs/Project 2 Report Generator]] | Ingest, process, prompt, generate, export |
| Source ingestion | [[RAG/RAG Basics]] | `rag_intro.ipynb` | [[Labs/W2D1 Podcast Project]], [[Labs/Project 2 Report Generator]] | PDF, URL, text, markdown knowledge base |
| Report generation | [[Prompting/Dynamic Prompting]] | dynamic prompting concepts | [[Labs/Project 2 Report Generator]] | Context + templates + model output |
| Podcast generation | [[Speech/TTS]] | speech notebooks | [[Labs/W2D1 Podcast Project]] | Summary to script to speech |
| Structured workflow orchestration | [[Ironhack/Frameworks/LangGraph]] | `langgraph.ipynb`, `langgraph_integration.ipynb` | [[Labs/W4D1 LangGraph Complaint Workflow Lab]] | Multi-stage AI workflow with explicit state and predictable execution |
| Operational app automation | [[n8n/n8n Workflows]] | applied Week 4 lab material | [[Labs/W4D2 n8n Node Study Guide Lab]], [[Labs/W4D3 n8n Multi-App Integration Lab]] | Low-code workflows that connect triggers, AI/model steps, transformations, and external apps |
