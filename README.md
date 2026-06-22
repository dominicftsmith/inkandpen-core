# inkandpen-core
Ink &amp; Pen Plus: Core Multi-Agent Orchestration Engine
1. Executive Summary & Problem StatementTraditional enterprise workflows are bottlenecked by manual administrative tasks, data entry, and fragmented customer service channels. Traditional software solutions rely on rigid, deterministic logic that breaks when faced with the ambiguous, unstructured nature of human communication.  InkAndPen-Core resolves this operational friction by shifting the human interface from syntax to intent. Built on Google's Agent Development Kit (ADK), this architecture deploys an interoperable, distributed virtual workforce designed to autonomously ingest, triage, and execute high-signal administrative workflows under strict enterprise guardrails.  2. Core Architecture: The Distributed WorkforceTo prevent context rot and attention dilution inherent in single-agent monoliths, this platform utilizes a Directed Acyclic Graph (DAG) orchestration pattern to divide labor among specialized domain experts:                    ┌──────────────────┐
                  │ User Intent/PR   │
                  └────────┬─────────┘
                           │
                           ▼
               ┌───────────────────────┐
               │   Coordinator Agent   │
               └───────────┬───────────┘
                           │ (Handoff via Schema Pointer)
                           ▼
         ┌─────────────────┴─────────────────┐
         ▼                                   ▼
┌─────────────────┐                 ┌─────────────────┐
│  Triage Agent   │                 │   Data Agent    │
└────────┬────────┘                 └────────┬────────┘
         │                                   │ (JSON-RPC 2.0)
         ▼                                   ▼
┌─────────────────┐                 ┌─────────────────┐
│ Responder Agent │                 │ Custom SQLite   │
│ (Email/Chat)    │                 │   MCP Server    │
└─────────────────┘                 └─────────────────┘
Coordinator Agent: Processes top-level natural language intent, decomposes goals into atomic tasks, and manages async execution loops.  Triage Agent: Continuously monitors incoming communication streams and categorizes semantic intent.  Data Agent: Intercepts administrative records and securely commits updates to localized storage.  Responder Agent: Drafts brand-consistent, context-aware responses adhering perfectly to corporate style guidelines.  3. Key Course Concept IntegrationsThis repository serves as a portfolio-ready demonstration of Google's 5-Day Intensive Vibe Coding concepts implemented for production environments:  Google ADK Multi-Agent System: State and execution history are decoupled from the prompt; nodes communicate asynchronously across network boundaries by passing structural schema references to prevent context overflow.  Model Context Protocol (MCP) Server: Data entry automation is standardized using an enterprise host-client-server topology over a local stdio transport layer, eliminating custom API wrapper debt.  Agent Skills Primitive: Scoped procedural memory (such as data formatting or email sanitization) is offloaded into trigger-based .agent/skills/ directories, leveraging progressive disclosure to minimize token spend.  Effective Trust Security Harness: Enforces a rigid "safety envelope" through kernel-level ephemeral sandboxing, Just-In-Time (JIT) hyper-restricted token downscoping, and a human-in-the-loop "Vibe Diff" summary for high-stakes tool invocations.  4. Rigorous Evaluation & Verification"Structure scales, vibes don't." To graduate code past the draft tier, this repository features an automated Evaluation-Driven Development (EDD) pipeline:  Unit Tests: Catch binary, deterministic regressions in our underlying code assets.  Trajectory Evaluations: Leverage an automated LLM-as-judge against a curated 20+ case Golden Dataset, utilizing IN_ORDER sequence scoring to guarantee that sub-agents execute only authorized workflows.
