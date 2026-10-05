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
Turn free-form job descriptions into validated, typed records using a Pydantic schema and LangChain's `PydanticOutputParser`. 

### 2. **Summarization**
- Map-reduce chain demo
- Action-item templates
- Router prompts
- Misclassification
  
**Notebook:** [`2. Summarization.ipynb`](2.%20Summarization.ipynb)
Map-reduce summarization of long arXiv papers, plus a structured action-item template for downstream automation.

### 3. **Agents**
- Agent review
- CrewAI DeepDive
- Researcher/Writer pipeline
- Synchronous and Asynchronous crews
- Compliance checklist creation
  
**Notebook:** [`3. Agents.ipynb`](3.%20Agents.ipynb)
A CrewAI multi-agent pipeline that audits real privacy policies against a GDPR/CCPA compliance checklist.

### 4. **ChatBot**
- Embeddings
- Vector Databases
- Retrieval Augmented Generation
- Tool integration
- Interactive agent
  
**Notebook:** [`4. ChatBot.ipynb`](4.%20ChatBot.ipynb)
A laptop-friendly RAG chatbot over a Wikipedia subset, using local sentence-transformer embeddings, Chroma, and tool use.

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
