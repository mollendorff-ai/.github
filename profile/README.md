## Mollendorff AI

Open-source AI architecture, cognitive systems, and developer tooling research.

### Agentic AI Platform

Three projects designed to work together via [MCP](https://modelcontextprotocol.io/) (Model Context Protocol). Sentinel orchestrates. Forge calculates. Ref fetches. The LLM reasons -- and is swappable with one env var.

```mermaid
C4Container
    title Sentinel — C4 Container Diagram

    Person(analyst, "Analyst", "Requests earnings analysis via CLI")

    Container_Boundary(sentinel, "Sentinel") {
        Container(pipeline, "LangGraph Pipeline", "StateGraph", "Conditional routing, self-correction loops, checkpointing")
        Container(research, "Research Agent", "LangChain", "Fetches earnings data, extracts financials")
        Container(modeler, "Modeler Agent", "LangChain", "Generates Forge YAML, validates, calculates DCF")
        Container(risk, "Risk Analyst", "LangChain", "Monte Carlo simulation, tornado sensitivity")
        Container(scenario, "Scenario Planner", "LangChain", "Bull / base / bear scenario analysis")
        Container(synth, "Synthesizer", "LangChain", "Executive brief with traceable numbers")
        ContainerDb(db, "SQLite", "Checkpointer", "Persists state for resumable runs")
    }

    System(forge, "Forge", "Our MCP server: DCF, Monte Carlo, 173 Excel functions, 7 analytical engines")
    System(ref, "Ref", "Our MCP server: headless Chrome, SPA support, structured JSON extraction")
    System_Ext(llm, "LLM Provider", "Claude / GPT / Gemini — swappable via env var")
    System_Ext(langsmith, "LangSmith", "Observability: traces, run names, tags, metadata")

    Rel(analyst, pipeline, "Runs", "CLI / Makefile")
    Rel(pipeline, research, "Dispatches")
    Rel(pipeline, modeler, "Dispatches")
    Rel(pipeline, risk, "Full mode only")
    Rel(pipeline, scenario, "Full mode only")
    Rel(pipeline, synth, "Dispatches")
    Rel(research, ref, "Fetches earnings", "MCP / stdio")
    Rel(modeler, forge, "Validate + calculate", "MCP / stdio")
    Rel(risk, forge, "Simulate + tornado", "MCP / stdio")
    Rel(scenario, forge, "Scenarios + compare", "MCP / stdio")
    Rel(research, llm, "Extracts financials", "API")
    Rel(modeler, llm, "Generates YAML", "API")
    Rel(risk, llm, "Augments model", "API")
    Rel(scenario, llm, "Generates scenarios", "API")
    Rel(synth, llm, "Produces brief", "API")
    Rel(pipeline, db, "Checkpoints state")
    Rel(pipeline, langsmith, "Traces runs", "HTTPS")

    UpdateLayoutConfig($c4ShapeInRow="3", $c4BoundaryInRow="1")
```

| Project | What It Does | Stack |
| ------- | ----------- | ----- |
| **[Sentinel](https://github.com/mollendorff-ai/sentinel)** | Multi-agent earnings analysis -- 5 LangGraph agents, self-correction, Monte Carlo, conditional routing | Python, LangGraph, LangSmith |
| **[Forge](https://github.com/mollendorff-ai/forge)** | Financial modeling MCP server -- YAML that LLMs read, write, and validate deterministically | Rust, MCP |
| **[Ref](https://github.com/mollendorff-ai/ref)** | Web data ingestion MCP server -- headless Chrome, SPA support, structured JSON for LLM agents | Rust, MCP |

### More Projects

| Project | What It Does | Stack |
| ------- | ----------- | ----- |
| **[DANEEL](https://github.com/mollendorff-ai/daneel)** | Cognitive architecture research (TMI implementation) | Rust, Redis, Qdrant |
| **[daneel-web](https://github.com/mollendorff-ai/daneel-web)** | Live WASM observatory into a running cognitive architecture -- [timmy.mollendorff.ai](https://timmy.mollendorff.ai) | Rust, Leptos, Axum |
| **[Asimov](https://github.com/mollendorff-ai/asimov)** | AI session orchestration for coding CLIs | Shell/Bash |
| **[Kinship Protocol](https://github.com/mollendorff-ai/kinship-protocol)** | Game-theory framework: cooperation as a mathematical attractor | Research |

[![Timmy — DANEEL cognitive observatory](timmy-observatory.png)](https://timmy.mollendorff.ai)

Personal R&D by [Louis C. Tavares](https://www.linkedin.com/in/louistavares/) -- 20+ year enterprise architecture background, AI engineering.
