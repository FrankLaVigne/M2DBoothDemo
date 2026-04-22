# FedAura Booth Demo: Speaker Notes

Use these talking points when walking someone through the demo. You don't need to hit every stage; find out what the visitor cares about and focus there. The three big rocks (AutoML, AutoRAG, Eval Hub) are the priority.

---

## Opening

> "This is FedAura, a reference application that shows how Red Hat AI connects models to data. It walks through an AI-powered mortgage processing pipeline, end to end."

- The pipeline auto-cycles. Click any stage to pause and drill in.
- The three larger stages are the big rocks; that's where the new capabilities live.
- Everything here runs on Red Hat OpenShift AI.

---

## Stage 1: Ingest (Docling)

**Story beat:** "Start with the data."

**Talking points:**
- Every AI system starts with documents. Docling turns raw, messy data into something models can actually use.
- PDFs, spreadsheets, scanned documents, and policy manuals: Docling handles all of it.
- It preserves the structure and metadata so downstream systems (RAG, training) get clean input.
- Connects to enterprise sources: databases, SharePoint, Confluence.

**If they ask:** "How is this different from just parsing PDFs?"
> Docling understands document structure (tables, headers, sections), not just raw text. That structure matters when you need a RAG system to retrieve the right policy clause, not just a paragraph that mentions the keyword.

---

## Stage 2: Train (OpenShift AI)

**Story beat:** "Teach the models your world."

**Talking points:**
- Foundation models know the internet. They don't know your business.
- Training Hub fine-tunes models on your data: loan histories, regulatory language, and internal policies.
- Runs distributed training across GPU clusters on OpenShift AI.
- Supports LoRA/QLoRA for efficient fine-tuning without needing massive compute.

**If they ask:** "Do I need to train my own model?"
> Not always. If your use case is retrieval-heavy (answering questions from documents), AutoRAG might be enough. Training makes sense when you need the model to deeply understand your domain language or make predictions specific to your data.

---

## Stage 3: Decide (AutoML): BIG ROCK

**Story beat:** "A $340,000 mortgage application arrives."

**Talking points:**
- AutoML automates the entire ML workflow: feature engineering, model selection, hyperparameter tuning, and validation.
- You give it your historical data (e.g., past loan decisions). It builds and selects the best predictive model.
- In the FedAura story, AutoML analyzes 47 financial signals and returns a decision in under 200ms.
- Every decision comes with ranked risk factors, fully auditable.
- Available as Tech Preview in Red Hat AI 3.4.

**Click the stage to open the panel.** Play the video if they want to see it in action.

**If they ask:** "How is this different from just training a model?"
> AutoML is specifically for predictive/classification tasks on structured data (think tabular data, CSV files, time series). It automates the tedious part: trying dozens of algorithms and configurations to find the best performer. Training Hub is for customizing language models with unstructured text.

**If they ask:** "What's on the roadmap?"
> Exposing trained predictive models as MCP tools so AI agents can call them directly. Also LLM-powered time series forecasting.

---

## Stage 4: Explain (AutoRAG): BIG ROCK

**Story beat:** "Why was my application rejected?"

**Talking points:**
- Building a good RAG pipeline is hard. Chunk sizes, embedding models, retrieval strategies, rerankers: hundreds of decisions.
- AutoRAG automates the search. It tests thousands of configurations and finds the optimal setup for your data.
- In the FedAura story, a customer asks why they were rejected. AutoRAG retrieves the exact policy clause: no hallucination, fully traceable.
- Evaluation metrics built in: answer correctness, faithfulness, groundedness.
- Available as Tech Preview in Red Hat AI 3.4.

**Click the stage to open the panel.** Play the video.

**If they ask:** "What does it actually optimize?"
> Everything in the RAG pipeline: how documents are chunked, which embedding model is used, the vector store configuration, retrieval strategy (keyword vs. dense vs. hybrid), reranker settings, and top-K retrieval count. It benchmarks each combination and picks the best.

**If they ask:** "What's on the roadmap?"
> Agentic RAG and Graph RAG: more advanced retrieval patterns where the system reasons about which documents to retrieve rather than doing a single lookup.

---

## Stage 5: Test (SDG Hub)

**Story beat:** "Does the system actually work under pressure?"

**Talking points:**
- SDG Hub is a composable Python framework for synthetic data generation.
- Pre-built flows cover RAG evaluation, red teaming, tool calling, and knowledge tuning.
- Native to Red Hat OpenShift AI: the same pipelines run from a workbench prototype to Kubernetes at scale.
- In the FedAura story, SDG Hub generates thousands of evaluation scenarios (edge cases, ambiguous policies, adversarial questions), each with a ground-truth answer so Eval Hub can score automatically.

**If they ask:** "Why synthetic data instead of real data?"
> Real evaluation data is expensive and slow to create. You also can't easily generate adversarial edge cases from real data. SDG Hub lets you stress-test specifically the scenarios that matter: the weird edge cases that break systems in production.

---

## Stage 6: Validate (Eval Hub): BIG ROCK

**Story beat:** "Does it hold up under scrutiny?"

**Talking points:**
- Eval Hub is the validation control plane. It evaluates models, RAG pipelines, agents, and full applications.
- Runs accuracy benchmarks, groundedness checks, and adversarial probes.
- Supports multiple evaluation frameworks: lm-evaluation-harness, LightEval, GuideLLM, and custom frameworks via BYOF (Bring Your Own Framework).
- Industry-specific evaluation collections: validate against scenarios that matter to your domain.
- Kubernetes-native: evaluations run as Jobs, results tracked in MLflow.
- Available as part of TrustyAI in Red Hat AI.

**Click the stage to open the panel.** Play the video.

**If they ask:** "What makes this different from just running benchmarks?"
> Eval Hub is an orchestration platform, not a single benchmark tool. It manages the lifecycle: scheduling evaluations, tracking results over time, comparing model versions, enforcing resource quotas. And it supports multiple backends, so you're not locked into one evaluation framework.

**If they ask:** "Can I bring my own evaluation logic?"
> Yes. The BYOF (Bring Your Own Framework) SDK lets you implement a single method, package it as a container, and Eval Hub handles scheduling, status tracking, and result aggregation. It also has an MCP server so AI agents can trigger and read evaluations.

---

## Stage 7: Refine (ITS Hub)

**Story beat:** "10,000 loan officers. Simultaneously."

**Talking points:**
- Inference-Time Scaling samples multiple responses at inference and selects the best one.
- Instead of training bigger models, ITS gets larger-model accuracy from smaller ones at runtime.
- Algorithms: Best-of-N, Monte Carlo Tree Search, beam search.
- Available as an SDK and a gateway (zero code changes).
- In the FedAura story: larger-model accuracy from smaller models at a fraction of the GPU cost, without sacrificing the accuracy that compliance demands.

**If they ask:** "How does it improve quality without retraining?"
> It generates multiple candidate responses and selects the best one (Best-of-N), or it uses tree search to explore different reasoning paths. You're trading inference compute for output quality, which is often cheaper than training a larger model.

---

## Closing

> "That's the pipeline: from raw documents to production-ready AI, all on Red Hat OpenShift AI. The three big rocks are AutoML, AutoRAG, and Eval Hub, all available in Red Hat AI 3.4. Want to go deeper on any of these?"

- Offer to play the video demos for whichever component they're most interested in.
- If they want hands-on: ITS Hub has a live demo link.
- Point them to redhat.com/ai for more info.

---

## Quick Reference

| Stage | Component | One-liner |
|-------|-----------|-----------|
| Ingest | Docling | Turns any document into AI-ready data |
| Train | Training Hub | Fine-tunes models on your domain data |
| **Decide** | **AutoML** | **Automated ML from your historical data** |
| **Explain** | **AutoRAG** | **Optimized RAG pipelines in minutes** |
| Test | SDG Hub | Synthetic data for evaluation and training |
| **Validate** | **Eval Hub** | **Comprehensive AI validation before production** |
| Refine | ITS Hub | Better accuracy from existing models at runtime |
