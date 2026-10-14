# AI Automation for Developers

![GitHub](https://img.shields.io/github/license/DataForScience/AIAutomation)
[![Twitter @data4sci](https://img.shields.io/twitter/follow/data4sci)](https://twitter.com/intent/follow?screen_name=data4sci)
![GitHub top language](https://img.shields.io/github/languages/top/DataForScience/AIAutomation)
![GitHub repo size](https://img.shields.io/github/repo-size/DataForScience/AIAutomation)
![GitHub last commit](https://img.shields.io/github/last-commit/DataForScience/AIAutomation)

[![Substack](https://img.shields.io/badge/Data_For_Science-Subscribe-blue)](https://data4sci.substack.com/)
[![Data Science Briefing](https://img.shields.io/badge/Data_Science_Briefing-Subscribe-blue)](https://data4sci.com/newsletter)

### Code and slides to accompany the online webinar by Data For Science.

LLMs are good at a surprising amount of the tedious work that fills a normal week — pulling structured fields out of free text, summarizing long documents, running multi-step reviews, and answering questions over a knowledge base. This webinar walks through four end-to-end Jupyter notebooks that show how to build each of those workflows with [LangChain](https://www.langchain.com/), [CrewAI](https://www.crewai.com/), and Anthropic's [Claude](https://platform.claude.com/docs/en/home), with practical guardrails, schemas, and evaluation patterns you can lift straight into your own projects.

## Contents

This tutorial is divided into four parts:

### 1. **Structured Extraction**
- LLM Review
- LangChain Deep dive
- Pydantic schema planning
- JSON validation loop
- Prompt guardrail patterns
  
**Notebook:** [`1. Structured Extraction.ipynb`](1.%20Structured%20Extraction.ipynb)

Turns free-form job descriptions (from the Hugging Face `jacob-hugging-face/job-descriptions` dataset) into validated, typed records. A Pydantic `JobPosting` schema is the single source of truth: it uses explicit nullability, `Literal` enums, and validators whose error messages flow back to the model. A LangChain chain pairs a guardrailed system prompt (extract only what's in the source, flag non-job content) with `PydanticOutputParser`. When output fails to parse or validate, a self-healing loop re-prompts with the exact error. The notebook runs a sample with progress tracking and failure logging, sanity-checks the results by plotting the top skills and the seniority distribution, and ends with adversarial inputs (a news article, a prompt injection, and a recipe) to test the guardrails.

### 2. **Summarization**
- Action-item templates
- Router prompts
- Misclassification auditing
  
**Notebook:** [`2. Summarization.ipynb`](2.%20Summarization.ipynb)

Triages long arXiv papers streamed from the `ccdv/arxiv-summarization` dataset. First, an action-item template turns a paper summary into a structured `PaperBrief`: a summary, up to five typed action items (e.g. `try-method`, `replicate-experiment`) with priorities, and open questions, ready for downstream automation. Next, a router prompt with a shared rubric and few-shot examples classifies each paper as `theory`, `experimental`, or `survey` and sends it to a specialist summarizer, because a theory paper summarized with an applied template tends to come back with invented datasets and metrics. An auditor re-asks the classification question using the same rubric to catch misroutes.

### 3. **Agents**
- Agent review
- CrewAI DeepDive
- Researcher/Writer pipeline
- Synchronous and Asynchronous crews
- Compliance checklist creation
  
**Notebook:** [`3. Agents.ipynb`](3.%20Agents.ipynb)

A CrewAI multi-agent pipeline that audits real privacy policies (GitHub, DuckDuckGo, and Wikipedia, with an offline fallback) against an 8-item GDPR/CCPA compliance checklist. Three single-responsibility agents run as a sequential crew: a **Privacy Researcher** extracts quoted factual statements, a **Compliance Officer** maps them to checklist items as covered, partial, or missing, and an **Audit Writer** produces a one-page executive report with a verdict, the top gaps, and remediation steps. The notebook runs the crew synchronously, one policy at a time, then asynchronously with all policies in parallel, plots the speed difference, and writes the per-policy results to [`data/compliance_audits.json`](data/compliance_audits.json) for downstream tools.

### 4. **ChatBot**
- Embeddings
- Vector Databases
- Retrieval Augmented Generation
- Tool integration
- Interactive agent
  
**Notebook:** [`4. ChatBot.ipynb`](4.%20ChatBot.ipynb)

A laptop-friendly RAG chatbot over the `rag-datasets/rag-mini-wikipedia` corpus (~3,200 passages). Passages are embedded locally with `all-MiniLM-L6-v2` (no extra API key) and stored in an in-memory Chroma collection. A plain RAG chain answers only from the retrieved passages, cites them by number, and says when it doesn't know; it is evaluated on the bundled Q&A split with exact-match and substring-match scores. The notebook then adds tools (`wiki_search`, `calculator`, and `now`) and builds an interactive tool-calling agent that decides on each turn whether to search, compute, or check the time.

Slides for the webinar live in [`slides/AIAutomation.pdf`](slides/AIAutomation.pdf).

## References

- [Hands-On Large Language Models](https://amzn.to/4d81BhV)
- [AI Engineering: Building Applications with Foundation Models](https://amzn.to/4tRImAk)
- [LLM Engineer's Handbook]( https://amzn.to/42M3VGs)
- [Building LLM Powered Applications](https://amzn.to/48IhGJQ)
- [Prompt Engineering for LLMs](https://amzn.to/3OW4RF6)
- [LLMs in Production](https://amzn.to/3P3FfpN)
- [Agentic Design Patterns](https://amzn.to/4w7wLi7)
- [Generative AI with LangChain](https://amzn.to/3P3FHV1)
- [AI Agents in Action](https://amzn.to/3P0Lpa0)
- [Building AI Agents with LLMs, RAG, and Knowledge Graphs](https://amzn.to/4n4tU5i)

## Setup

Install [uv](https://docs.astral.sh/uv/) if you don't have it yet:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Install dependencies and launch Jupyter:

```bash
uv sync
uv run jupyter notebook
```

Set your Anthropic API key before running the notebooks:

```bash
export ANTHROPIC_API_KEY=sk-ant-...
```

## Author

<table border="0">
 <tr>
	<td>
	  <img src="data/bgoncalves.png" alt="Bruno Gonçalves" width="150" height="150" style="border-radius: 50%; object-fit: cover;">
	</td>
	<td>
	  <h2>Bruno Gonçalves</h2>
	  <h3>Data For Science, Inc.</h3>
	  <p>
			Web: <a href="http://www.data4sci.com/">www.data4sci.com</a><br>
			Twitter/X: <a href="https://twitter.com/bgoncalves">@bgoncalves</a><br>
			LinkedIn: <a href="https://www.linkedin.com/in/bmtgoncalves/">@bmtgoncalves</a><br>
			Email: <a href="info@data4sci.com">info@data4sci.com</a><br>
			Schedule a Call: <a href="https://data4sci.com/call">https://data4sci.com/call</a>
	  </p>
	</td>
 </tr>
</table>
