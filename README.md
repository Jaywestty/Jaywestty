<h1 align="center">Hi, I'm Oluwajuwon</h1>
<p align="center">
  <b>AI Engineer</b> building grounded, tested and production-ready AI systems
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

I design and ship end-to-end AI systems, from LLM assistants and RAG pipelines to forecasting models, and take them all the way to production. My work sits between ML engineering and AI product building, with attention to the constraints that decide whether a system holds up: data quality, evaluation, latency, cost and reliability under real usage.

Currently, I work as an AI/ML Engineer refining prompt architecture and agent behavior within a live multi-agent Planner-Executor-Validator system, alongside independent projects spanning LLM applications, applied ML and MLOps.

## Featured projects

### Adugbo AI: Lagos rent assistant
**AI assistant that tells you what rent really costs in Lagos, from real listings, in English or Pidgin.**

Rent in Lagos is hard to judge: listings are scattered, prices are quoted monthly or yearly, and agents inflate them. Adugbo AI gives a short, plain answer with a typical price, a range and the number of listings behind it, and links every figure to those listings. Built solo, end to end: data pipeline, backend, AI layer, frontend, deployment and operations.

- **Grounded LLM design:** the model only turns a question into a structured search. Every price is calculated with SQL from stored listings, so the AI never invents prices, and price figures found in web text are stripped out automatically.
- **Data pipeline:** a resumable weekly scraper for two Nigerian property sites that keeps only listings from the last 7 days, removes duplicates, converts monthly prices to yearly and flags prices that look mistyped.
- **Guardrails:** prompt-injection attempts are blocked before any AI call, off-topic questions are refused politely, web content is treated as data and links can only point to cited sources.
- **Cost and abuse protection:** three layers of rate limiting (per device, per network address and a daily app-wide ceiling) with admin alerts.
- **Wale, the assistant:** a persona that answers in Nigerian Pidgin when the user writes in Pidgin.
- **Observability and quality:** a trace id per question, logging of every AI call with latency and token use, a private admin console with Argon2-hashed logins and CSRF protection, 131 backend tests and 22 frontend tests.

`Groq (gpt-oss-120b)` · `Tavily` · `FastAPI` · `PostgreSQL (Supabase)` · `React` · `TypeScript` · `PWA` · `Vercel` · `Render`

[Live app](https://adugbo-ai.vercel.app/) · [Repo](https://github.com/Jaywestty/Lagos-Rent-Predictor)

### Crude Oil Scenario Forecaster
**Honest evaluation over impressive numbers: proved no model beats a no-change forecast, then built a scenario tool on top of what can be defended.**

An end-to-end ML system that turns plain-English "what if" questions about the oil market into probability-weighted Brent crude price scenarios, with calibrated uncertainty ranges and historical event context. When I rebuilt the evaluation, I found the original 15.22% MAPE was inflated by data leakage and that a simple no-change forecast scored better (12.39%), so I reframed the product as a scenario tool rather than a price predictor.

- **Evaluation:** walk-forward backtest over 198 weekly forecast dates and 1 to 12 week horizons, with naive, seasonal and drift baselines, Diebold-Mariano tests and Holm correction.
- **Leakage fix:** found a data-timing leak in monthly macro series. Fixing it showed the deployed model was significantly worse than "no change" at 12 weeks (Holm p = 0.038).
- **LLM layer:** gpt-oss-120b with JSON Schema structured output and Pydantic validation, checked by a 40-case evaluation harness with targets set before running. Valid output rose from 85% to 100% and injection attempts handled from 2/4 to 12/12.
- **MLOps:** versioned data pipeline with a 4-gate promotion check and a model registry, plus GitHub Actions that open a pull request only when a refreshed model passes the gates. A human merges and Render auto-deploys.
- **Production fix:** cut the model file from 488 MB to 2.8 MB with identical forecasts, fixing out-of-memory crashes on a 512 MB server. 183 automated tests.

`Time Series` · `LLM Evaluation` · `MLOps` · `FastAPI`

[Live demo](https://crudeoilforecaster.streamlit.app/) · [API docs](https://crudeoil-forecaster.onrender.com/docs) · [Research write-up](https://github.com/Jaywestty/CrudeOil-Forecaster/blob/main/docs/RESEARCH.md) · [Repo](https://github.com/Jaywestty/CrudeOil-Forecaster)

### Fraud Detection ML
A personal end-to-end project that scores money-transfer transactions for fraud risk through a REST API and a web app. Data cleaning, leakage-free features, time-based evaluation, MLflow tracking, a FastAPI service on Hugging Face Spaces (Docker) and a Streamlit app, with 22 tests gating every deploy.

- **Result:** on a held-out future period, reviewing the riskiest 5% of transactions catches 23% of fraud, about 4.5x more than random review (PR-AUC 0.073 against a 0.0155 base rate). The dataset is small, with 195 fraud cases in total.
- **Self-audit:** found and fixed 8 issues in my own first version, including evaluation leakage, train/serve skew and 7 of 9 engineered features being silently dropped before the model.
- **Shared pipeline:** cleaning and feature engineering live in one scikit-learn transformer used by both training and serving, with a parity test enforcing it. It repaired 1,482 corrupted values and removed 200 duplicate rows.
- **Delivery:** typed FastAPI service with Pydantic validation, experiments tracked in MLflow, and GitHub Actions that deploy only when all tests pass.

`XGBoost` · `scikit-learn` · `MLflow` · `FastAPI` · `Docker` · `GitHub Actions`

[Live app](https://fraud-detect-mll.streamlit.app) · [API docs](https://jayywestty-frauddetection-ml.hf.space/docs) · [Model dashboard](https://jayywestty-frauddetection-ml.hf.space/dashboard) · [Repo](https://github.com/Jaywestty/Fraud-detection-ML)

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
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

**AI and LLM systems**
![Groq](https://img.shields.io/badge/Groq-F55036?style=flat-square)
![Tavily](https://img.shields.io/badge/Tavily-6B4EFF?style=flat-square)
![RAG](https://img.shields.io/badge/RAG-4B8BBE?style=flat-square)
![LangChain](https://img.shields.io/badge/LangChain-1C3C3C?style=flat-square&logo=langchain&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)

**ML and data**
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-EC4E2C?style=flat-square&logo=xgboost&logoColor=white)
![Statsmodels](https://img.shields.io/badge/Statsmodels-4B8BBE?style=flat-square)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

**Backend and databases**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat-square)

**Frontend**
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

**Cloud and MLOps**
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonaws&logoColor=white)
![pytest](https://img.shields.io/badge/pytest-0A9EDC?style=flat-square&logo=pytest&logoColor=white)

## GitHub stats

<p align="center">
  <img src="https://raw.githubusercontent.com/Jaywestty/github-stats/generated/overview.svg" height="165" />
</p>

## Let's talk

Open to AI Engineer and applied AI roles where I can take systems from prototype to production.

<p align="center">
  <a href="mailto:juwonfadairo13@gmail.com">juwonfadairo13@gmail.com</a>
</p>
