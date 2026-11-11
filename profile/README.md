## Möllendorff AI

Unpaid personal R&D in open-source AI tooling, by [Louis C. Tavares](https://www.linkedin.com/in/lctavares/). Built with AI coding assistants under my direction. These are research projects, not products or services.

### Main projects

| Project | What it is | Status |
| ------- | ---------- | ------ |
| **[Forge](https://github.com/mollendorff-ai/forge)** | Deterministic financial-modelling engine in Rust. Excel-style formulas in YAML, with Monte Carlo, decision trees and other analysis engines, a command line and an MCP server so AI agents can run models. Checked against Gnumeric (over 1,300 formula cases agree, none disagree) and against R; [VALIDATION.md](https://github.com/mollendorff-ai/forge/blob/main/VALIDATION.md) lists every check. | R&D prototype, release candidate |
| **[Forge Studio](https://mollendorff-ai.github.io/forge/)** | Forge on a phone: a web page that shows a model as cards and runs the same engine in the browser through WebAssembly. The page itself calculates nothing, and the files stay in the browser. | R&D prototype, live |
| **[Ref](https://github.com/mollendorff-ai/ref)** | Small Rust tool that renders JavaScript-heavy web pages and PDFs into compact JSON for AI agents, with an MCP server. Can reuse a browser session you signed in to yourself. | Released, no known users yet |

The checks on Forge live in their own repositories: [forge-e2e-gnumeric](https://github.com/mollendorff-ai/forge-e2e-gnumeric) and [forge-e2e-r](https://github.com/mollendorff-ai/forge-e2e-r).

### Experiments and personal tools

- **[Asimov](https://github.com/mollendorff-ai/asimov)**: Bash launcher and build mode for AI coding CLIs. A personal tool, for sandboxes only.
- **[Kinship Protocol](https://github.com/mollendorff-ai/kinship-protocol)**: game-theory research notes on cooperation, with Forge models. Paused; its claims are hypotheses.
- **[DANEEL](https://github.com/mollendorff-ai/daneel)** and **[daneel-web](https://github.com/mollendorff-ai/daneel-web)**: a hobby cognitive-architecture experiment and its dashboard. Unvalidated; not for serious use.
- **[Sentinel](https://github.com/mollendorff-ai/sentinel)**: an earnings-analysis pipeline built on Forge and Ref. Experimental; it does not run yet.
