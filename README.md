<h1 align="center">Hi, I'm Oluwajuwon</h1>
<p align="center">
  <b>AI Engineer</b> building grounded, tested and production-ready AI systems
</p>

<p align="center">
  <a href="mailto:juwonfadairo13@gmail.com">
    <img src="https://img.shields.io/badge/Email-juwonfadairo13%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white" />
  </a>
  <a href="https://linkedin.com/in/[https://www.linkedin.com/in/oluwajuwon-f-27b132248/]">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white" />
  </a>
  <img src="https://img.shields.io/badge/Based%20in-Lagos%2C%20Nigeria-008751?style=flat-square" />
</p>

## What I do

I design and ship end-to-end AI systems, from LLM assistants and RAG pipelines to forecasting models, and take them all the way to production. My work sits between ML engineering and AI product building, with attention to what decides whether a system holds up: data quality, honest evaluation, cost and reliability under real usage.

Currently, I'm the engineer in charge of building and scaling the backend and AI infrastructure for [bukkafood.com](https://bukkafood.com), alongside independent projects in LLM applications, applied ML and MLOps.

## Featured projects

### Adugbo AI: Lagos rent assistant
**AI assistant that tells you what rent really costs in Lagos, from real listings, in English or Pidgin.**

Rent in Lagos is hard to judge: listings are scattered, prices are quoted monthly or yearly, and agents inflate them. Adugbo AI gives a plain answer with a typical price, a range and the number of listings behind it, and links every figure to those listings. Built solo, end to end.

- **Grounded by design:** the LLM only turns a question into a structured search. Every price is calculated with SQL from stored listings, so the AI never invents prices, and prices found in web text are stripped out.
- **Fresh data:** a resumable weekly scraper for two Nigerian property sites keeps only the last 7 days of listings, removes duplicates, converts monthly prices to yearly and flags prices that look mistyped.
- **Guardrails and cost control:** prompt injection is blocked before any AI call, off-topic questions are refused, and three layers of rate limiting protect the app and its AI budget.
- **Wale, the assistant:** replies in Nigerian Pidgin when the user writes in Pidgin.
- **Observable and tested:** a trace id per question, every AI call logged with latency and token use, a private admin console with Argon2-hashed logins and CSRF protection, 131 backend and 22 frontend tests.

`Groq (gpt-oss-120b)` · `Tavily` · `FastAPI` · `PostgreSQL (Supabase)` · `React` · `TypeScript` · `PWA` · `Vercel` · `Render`

[Live app](https://adugbo-ai.vercel.app/) · [Repo and screenshots](https://github.com/Jaywestty/Lagos-Rent-Predictor)

### Crude Oil Scenario Forecaster
**Honest evaluation over impressive numbers: proved no model beats a no-change forecast, then built a scenario tool on top of what can be defended.**

**What I built:** a system that turns plain-English "what if" questions about the oil market into probability-weighted Brent crude price scenarios. A SARIMAX model forecasts each scenario, an LLM assigns the scenario probabilities, and a FastAPI backend (Render) serves a Streamlit app. The first version reported a 15.22% MAPE.

**What I did to improve it:**
- Rebuilt the evaluation as a walk-forward backtest with naive baselines and significance tests, and found the 15.22% was inflated by data leakage. A simple no-change forecast scored better (12.39%), so I reframed the product as a scenario tool rather than a price predictor.
- Found and fixed a data-timing leak in monthly macro series. Fixed, the deployed model was significantly worse than "no change" at 12 weeks (Holm p = 0.038).
- Rebuilt the LLM layer with JSON Schema output and validation, tested on a 40-case harness with targets set in advance: valid output rose from 85% to 100% and injection attempts handled from 2/4 to 12/12.
- Added a gated, automated retraining pipeline in GitHub Actions, and cut the model file from 488 MB to 2.8 MB with identical forecasts to fix out-of-memory crashes. 183 automated tests.

`Time Series` · `LLM Evaluation` · `MLOps` · `FastAPI`

[Live demo](https://crudeoilforecaster.streamlit.app/) · [API docs](https://crudeoil-forecaster.onrender.com/docs) · [Research write-up](https://github.com/Jaywestty/CrudeOil-Forecaster/blob/main/docs/RESEARCH.md) · [Repo](https://github.com/Jaywestty/CrudeOil-Forecaster)

### Fraud Detection ML
**What I built:** a personal end-to-end project that scores money-transfer transactions for fraud risk, trained on a deliberately messy dataset of 10,200 records. An XGBoost model is served by a FastAPI service on Hugging Face Spaces (Docker) and a Streamlit app, with experiments tracked in MLflow and deploys through GitHub Actions.

**What I did to improve it:**
- Audited my own first version and found 8 issues, including evaluation leakage, train/serve skew and 7 of 9 engineered features being silently dropped before the model. I fixed all 8.
- Moved cleaning and feature engineering into one scikit-learn pipeline shared by training and serving, enforced by a parity test, and replaced a leaky random split with chronological validation and calibrated probabilities.
- Made CI deploy only when all 22 tests pass.
- **Result:** on a held-out future period, reviewing the riskiest 5% of transactions catches 23% of fraud, about 4.5x more than random review (PR-AUC 0.073 against a 0.0155 base rate). The dataset is small, with 195 fraud cases in total.

`XGBoost` · `scikit-learn` · `MLflow` · `FastAPI` · `Docker` · `GitHub Actions`

[Live app](https://fraud-detect-mll.streamlit.app) · [API docs](https://jayywestty-frauddetection-ml.hf.space/docs) · [Model dashboard](https://jayywestty-frauddetection-ml.hf.space/dashboard) · [Repo](https://github.com/Jaywestty/Fraud-detection-ML)

## Experience and impact

Beyond these public projects, I've worked inside production AI systems with real users:

- Built and debugged conversational analytics systems combining RAG retrieval, Text-to-SQL generation and hybrid LLM routing with automatic fallback, including forecasting components using quantile regression for uncertainty-aware predictions
- Designed and shipped a production medical AI assistant with retrieval-augmented generation, voice input and output, and request-level observability tracing
- Diagnosed failure modes in multi-agent LLM systems (duplicate-record bugs causing silent booking failures, tool-routing mismatches, state issues in long conversations) and implemented reliability patterns such as single-writer field ownership and idempotency for actions with real side effects

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
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

**Backend and databases**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat-square)

**Frontend**
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat-square&logo=streamlit&logoColor=white)

**Cloud and MLOps**
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![MLflow](https://img.shields.io/badge/MLflow-0194E2?style=flat-square&logo=mlflow&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat-square&logo=huggingface&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=flat-square&logo=render&logoColor=black)
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
