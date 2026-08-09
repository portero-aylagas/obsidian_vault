# AI Integration Bootcamp

> [!info] Structure
> This note system is organized by topic.
> Use this page as the main entry point.

## Topic Index

### Cross-Reference
- [[01 Shared Concept Index]]
- [[02 Lab Index]]
- [[03 Weekly Progression Rubric]]
- [[Prompt Library/00 Prompt Library Map]]

### Mandatory Labs and Projects
- [[Labs/W1D1 HomeGuard System Lab]]
- [[Labs/W1D2 Titanic JSON Lab]]
- [[Labs/W1D3 Sklearn Model Training Lab]]
- [[Labs/W1D4 Product Listing Vision Lab]]
- [[Labs/W1D5 Whisper STT Lab]]
- [[Labs/W2D1 Podcast Project]]
- [[Labs/W2D3 Prompt Engineering Lab]]
- [[Labs/W2D4 News Summarizer Lab]]
- [[Labs/W2D4 Python Low Code JSON Validation Lab]]
- [[Labs/W2D5 RAG Chunking Lab]]
- [[Labs/W3D3 LangChain Complaint Handler Lab]]
- [[Labs/W3D4 Relevance Scoring and Rerankers Lab]]
- [[Labs/W3D5 MCP in LangChain Lab]]
- [[Labs/W4D1 LangGraph Complaint Workflow Lab]]
- [[Labs/W4D2 n8n Node Study Guide Lab]]
- [[Labs/W4D3 n8n Multi-App Integration Lab]]
- [[Labs/Project 2 Report Generator]]

### Extra Labs
- [[Labs/W1D3 Neural Network Lab]]
- [[Labs/W1D5 Whisper STT Evaluation Lab]]
- [[Labs/W2D5 Native OpenAI RAG Lab]]
- [[Labs/W3D5 MCP Setup in Codex and Claude Code Lab]]
- [[Labs/W4D1 LangChain Guardrails Lab]]
- [[Labs/W4D2 Reflection Skills Lab]]
- [[Labs/W4D3 arXiv n8n Notion Research Summarizer Lab]]
- [[Labs/W4D4 n8n Error Handling and Scheduled Workflows Lab]]

### Foundations
- [[Foundations/Data and Pipeline Foundations]]

Subtopics:
- `pandas`
- JSON parsing
- Nested API response extraction
- Structured data handling
- Pipeline building blocks

### APIs
- [[APIs/OpenAI API]]
- [[APIs/Reliability Patterns]]
- [[APIs/Multi-Provider]]

Subtopics:
- `client.responses.create`
- `client.chat.completions.create`
- Reasoning models
- Instructions and roles
- Temperature
- Multi-turn context
- Image input
- Structured outputs
- Moderation-style classification
- Exponential backoff
- Jitter
- Retry strategy
- Circuit breaker
- Provider comparison
- Provider fallback
- Provider chaining
- Token budget tracking
- Streaming budget monitoring
- External data enrichment
- Environment configuration

### Engineering
- [[Engineering/Code Quality and Automation]]

Subtopics:
- Helper functions
- Refactoring messy code
- Separation of concerns
- API wrapper classes
- Standardized response objects
- Error handling
- Fake-client testing
- Unit testing with `pytest`
- Edge-case testing
- Test-driven development

### Agentic
- [[Agentic/Agent Skills]]
- [[Agentic/Effective Context Engineering for AI Agents]]

Subtopics:
- Agent skills
- `SKILL.md`
- Progressive disclosure
- Skill description routing
- `scripts/`, `references/`, and `assets/`
- Skills vs MCP
- Context engineering
- Just-in-time context retrieval
- Compaction
- Structured note-taking
- Sub-agent architectures

### n8n
- [[n8n/n8n Workflows]]

Subtopics:
- n8n trigger nodes
- n8n JSON item flow
- Code nodes
- Split Out
- app nodes
- HTTP Request nodes
- multi-app automation

### Frameworks
- [[Ironhack/Frameworks/LangChain]]
- [[Frameworks/MCP]]
- [[Ironhack/Frameworks/LangGraph]]

Subtopics:
- LangChain model abstraction
- `invoke`
- `stream`
- `batch`
- Message objects
- Multi-turn conversation
- Tools
- Pydantic tool schemas
- Tool binding
- Manual tool execution
- Multiple tool calls
- Agents
- Agent streaming
- MCP clients
- MCP tools
- MCP resources
- MCP tool interceptors
- LangGraph state graphs
- typed workflow state
- workflow nodes and edges
- deterministic AI workflows
- workflow path tracking

### ML
- [[ML/Classical ML]]
- [[ML/Deep Learning]]

Subtopics:
- Train/test split
- Scaling
- Feature engineering
- Logistic regression
- Random forest
- KNN regression
- Linear regression
- PCA
- K-means clustering
- Model comparison
- Dense neural networks
- MNIST classification
- Model training and evaluation
- Transformer zero-shot classification
- Batch classification

### Prompting
- [[Prompting/Prompting Basics]]
- [[Prompting/Dynamic Prompting]]

Subtopics:
- Zero-shot prompting
- One-shot prompting
- Few-shot prompting
- Role prompting
- Emotional prompting
- Chain-of-thought prompting
- Prompt iteration
- Output length control
- Temperature
- `top_p`
- `max_tokens`
- Frequency penalty
- Presence penalty
- Seed reproducibility
- Runtime prompt construction
- Variable injection
- Style injection
- Input injection
- Context injection
- Prompt templates
- Conversation memory

### RAG
- [[RAG/RAG Basics]]
- [[RAG/RAG Optimization]]

Subtopics:
- Document loading
- Chunking
- Recursive chunking
- Manual chunking
- Embeddings
- Vector stores
- Pinecone
- Vector upsert
- Similarity search
- Similarity scores
- RAG prompt structure
- Formatting retrieved documents
- LangChain RAG
- Direct OpenAI + Pinecone RAG
- With RAG vs without RAG
- Query rewriting
- Sub-query decomposition
- Parent document retrieval
- Reranking
- LLM relevance scoring
- combined retrieval scores
- Metadata filtering

### Speech
- [[Speech/STT]]
- [[Speech/TTS]]

Subtopics:
- Audio recording
- Save audio to WAV
- Audio visualization
- Whisper transcription
- Prompt-assisted transcription
- Chunking long audio
- Timestamps
- Transformer audio inference
- Speech recognition breaking points
- Accuracy comparison across conditions
- Offline TTS
- OpenAI TTS
- Voice comparison
- ElevenLabs TTS
