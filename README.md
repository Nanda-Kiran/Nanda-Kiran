### Founder of [Requal](https://requal.ai)

**Automated eval infrastructure for critical AI systems, from building golden datasets to gating releases.**

I build the infrastructure that tests whether a change to an AI system is ready to ship. I first ran into this problem at Ford's AI Advancement Center in 2025. There I built and deployed an LLM agent for Ford's vehicle shopping experience, then built the evaluation and observability harness around it (automated test suites, trajectory tracing, Arize AI), which cut evaluation time by about 60%.

[requal.ai](https://requal.ai) · [Requal on GitHub](https://github.com/Requal-Inc) · [LinkedIn](https://www.linkedin.com/in/nandakiranvelaga) · [X](https://x.com/NandaVelaga)

### Now building: Requal

A prompt edit, a model upgrade or a new tool can change what an AI system does. Requal tests each candidate release by what it actually did, applies the team's qualification policy, and turns the team's sign-off into a signed release authorisation that the deployment pipeline enforces. Agents that take actions, such as refunds, credits, orders and account changes, are the first example. The target is every critical AI system.

**Where it stands.** A working pre-launch prototype; the source is private. It runs end to end on one machine against scripted models, and cloud deployment comes next. In the demo, a faulty support-agent release is caught, its fix is qualified and authorised, and the deployment gate admits the fix and blocks the faulty release.

- **Evaluation engine (`rq`)**: statistics, verdicts, sealed runs and `rq verify`
- **Agent test environments**: resettable state, sandboxed tools behind a tool gateway, fault injection and assertions
- **Versioned contracts, a qualification-policy evaluator and a published verifier** that recomputes each verdict from the evidence
- **Runner (`rqr`)** that signs results as Ed25519 statements, and a **deployment gate** with GitHub, GitLab and generic CI examples
- **Control plane and web app**, plus a chaos suite and recovery drills

**Next.** Hosted execution on Requal's cloud by default, with the runner (`rqr`), already built to run in a team's own cloud, as the enterprise option. An agentic harness that turns a team's production data into a private benchmark. A library of test environments.

### How I build

I run AI coding agents as my engineering team: I direct the work, and they write and test the code. The Requal prototype is 244 commits over four days (Oct 1–4, 2026). Kin, below, was built the same way, and its commits credit the agent as co-author.

### Recently shipped

**[Kin](https://github.com/Nanda-Kiran/Kin)** · June 2026 · TypeScript, VS Code extension APIs, Ollama\
A local-first AI code editor. It is a fork of Code-OSS with one built-in extension that adds Ollama chat models, Tab autocomplete (fill-in-the-middle), `@kin` codebase Q&A over a local embedding index, and Agent-mode tool calling. It needs no API keys and leaves the editor core under `src/` untouched. Agent mode maps the editor's tools onto Ollama function calling and sets `num_ctx` explicitly, because Ollama's small default context would otherwise silently truncate agent prompts.

**[vellum](https://github.com/Nanda-Kiran/vellum)** · May 2026 · Python, FastAPI, LangGraph, Groq, Slack · 5-hour hackathon, two-person team\
A finance-controller agent for startups. It pulls Plaid (sandbox), Stripe, Gmail and Google Sheets, runs deterministic checks for duplicate charges, recurring SaaS, meal-policy breaches and vendor payment-change emails from the wrong domain, and posts findings to Slack, with approve and reject buttons where sign-off is needed. Rules decide. The LLM explains, can only raise a finding's severity, and falls back to the rule result if it fails. It shipped with its own scenario evals, including near-miss negative cases.

**[yunaki-memory-mcp](https://github.com/Nanda-Kiran/yunaki-memory-mcp)** · June 2026 · TypeScript, MCP\
An MCP server that gives coding agents memory for each repo. Each memory is a Markdown file in a separate git store keyed to the repo's root-commit SHA, so memory stays with the repo when it is renamed or moved, and every write is a commit you can diff or revert. Agents can write and search memories, and seed them from a repo's file tree, package.json and docs.

### Earlier

- **[IVADAS](https://github.com/Nanda-Kiran/IVADAS)** (Dec 2025, UMD cloud computing course, team project): PatchCore and SoftPatch anomaly detection, deployed for the course on SageMaker real-time endpoints behind a Lambda `/predict` API, with an S3 result cache keyed by model and image hash. The models are upstream research code; our work was the serving layer.
- **[CodeCompanion](https://github.com/Nanda-Kiran/CodeCompanion)** (Nov 2024, HackUMass, team project): an AI coding-practice companion. My part was the Flask service that calls Gemini for hints, code Q&A and solution checks, containerised and deployed to Cloud Run with Terraform.

### Background

- **Yunaki**, co-founder (2026): agentic automation for law firms, with human approval and traceability
- **Ford AI Advancement Center**, AI intern (2025): the vehicle shopping agent (LangGraph, AG-UI, React/Next.js), shipped on GCP Cloud Run behind Apigee with Tekton CI/CD, and its eval harness
- **Ford, Chennai**, SDE intern (2024): a production serverless platform on GCP; monitoring that cut MTTD/MTTR by about 40%
- **Critical River**, AI/ML intern (2023): document-understanding ML pipelines on SageMaker
- **MS Applied Machine Learning**, University of Maryland, College Park (2026) · **BTech CSE**, NIT Raipur (2024)

Shipping a critical AI system? I'd like to hear how you test changes before they go out. Book a demo at [requal.ai](https://requal.ai).
