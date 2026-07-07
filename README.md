<h1 align="center">Hi, I'm Oluwajuwon</h1>
<p align="center">
  <b>AI/ML Engineer</b> building production-grade AI systems for real-world use cases
</p>

<p align="center">
  <a href="mailto:juwonfadairo13@gmail.com">
    <img src="https://img.shields.io/badge/Email-juwonfadairo13%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white" />
  </a>
  <a href="https://linkedin.com/in/[your-linkedin-handle]">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white" />
  </a>
  <img src="https://img.shields.io/badge/Based%20in-Lagos%2C%20Nigeria-008751?style=flat-square" />
</p>

## What I do

I design and ship end-to-end AI systems, from RAG pipelines and conversational agents to ML forecasting models, and take them all the way to production. My work sits at the intersection of practical ML engineering and AI product building, with attention to real business constraints: data quality, latency, cost, and reliability under real usage.

Currently, I work as an AI/ML Engineer refining prompt architecture and agent behavior within a live multi-agent Planner-Executor-Validator system, alongside independent projects spanning RAG, conversational AI, and applied ML.

## Featured projects

**Crude Oil Price Scenario Forecaster** — Probabilistic macroeconomic simulation engine
SARIMAX econometric forecasting combined with an LLM probability layer (LLaMA 3.3 via Groq) that reads plain-English market scenarios, assigns probability weights across competing outcomes, adjusts those weights using live macro signals (VIX, dollar index, inventories, Fed funds), and returns a weighted price distribution instead of a single point estimate.
[Live demo](https://crude-forecaster.streamlit.app/) · [API docs](https://crudeoil-forecaster.onrender.com/docs) · [Repo](https://github.com/Jaywestty/CrudeOil-Forecaster)

**Fraud Detection ML System** — Full MLOps reference implementation
A fraud scoring system built as three connected services rather than a single script: MLflow-tracked training across multiple candidate models with automatic best-model selection, a FastAPI backend serving predictions and a live metrics dashboard, and an independently deployed Streamlit frontend. CI/CD via GitHub Actions auto-deploys to Hugging Face Spaces on every push.
[Live app](https://fraud-detect-mll.streamlit.app) · [API and dashboard](https://jayywestty-frauddetection-ml.hf.space)

## Experience and impact

Beyond these public projects, I've spent recent months embedded in production AI systems handling real user traffic and real operational stakes:

- Built and debugged conversational analytics systems combining RAG retrieval, Text-to-SQL generation, and hybrid LLM routing with automatic fallback, including forecasting components using quantile regression for uncertainty-aware predictions
- Designed and shipped a production medical AI assistant with retrieval-augmented generation, voice input and output, and full request-level observability tracing
- Diagnosed and resolved subtle failure modes in multi-agent LLM systems, including duplicate-record bugs causing silent booking failures, tool-routing mismatches, and state management issues in long-running conversations
- Proposed and implemented architectural patterns for reliability in agentic systems, including single-writer field ownership and idempotency handling for actions with real side effects like external messaging and database mutations
- Worked across the full lifecycle of applied ML: feature engineering under real-world data constraints, model selection and evaluation, deployment, and post-deployment debugging

## Tech stack

**Languages**
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

**ML and data**
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-EC4E2C?style=flat-square&logo=xgboost&logoColor=white)

**AI and LLM systems**
![RAG](https://img.shields.io/badge/RAG-4B8BBE?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square)

**Backend and APIs**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

**Cloud and MLOps**
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)

## GitHub stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Jaywestty&show_icons=true&theme=default&hide_border=true" height="165" />
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Jaywestty&hide_border=true" height="165" />
</p>

## Let's talk

Open to AI/ML Engineer and applied AI roles where I can take systems from prototype to production.

<p align="center">
  <a href="mailto:juwonfadairo13@gmail.com">juwonfadairo13@gmail.com</a>
</p>
