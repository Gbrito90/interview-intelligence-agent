# 🤖 Interview Intelligence Agent

> AI-powered agent that analyzes job descriptions, generates tailored interview scripts, and produces structured candidate assessments — built by a Senior Tech Recruiter who automated his own workflow.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o-412991?style=flat&logo=openai)](https://openai.com)
[![Colab](https://img.shields.io/badge/Google_Colab-Ready-F9AB00?style=flat&logo=googlecolab&logoColor=white)](https://colab.research.google.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat)](LICENSE)

---

## 🎯 The Problem

Tech recruiters conducting interviews for complex technical roles face three recurring bottlenecks:

1. **Preparing the interview** — Reading JDs and crafting relevant technical questions per stack takes 30–60 minutes per role
2. **Consistency** — Questions vary depending on the recruiter's familiarity with the stack
3. **Writing the assessment** — Structuring a professional candidate report after each interview is time-consuming and often inconsistent

This agent solves all three.

---

## ✨ What It Does

```
📄 PDF Job Description
        ↓
🔍 Stage 1 — Structured JD Analysis
        ↓  extracts stack, seniority, responsibilities, behavioral profile
❓ Stage 2 — Interview Script Generation
        ↓  technical questions (per stack) + STAR behavioral questions
        ↓  [you conduct the interview]
📝 Stage 3 — Candidate Assessment
        ↓  paste your interview transcript/notes
⭐ Scorecard + Executive Summary + Recommendation
        ↓
💾 Export full report as .md
```

---

## 🚀 Quick Start

### Run on Google Colab (recommended — no setup required)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Gbrito90/interview-intelligence-agent/blob/main/interview_intelligence_agent.ipynb)

1. Click the button above
2. Add your OpenAI API Key to Colab Secrets (`🔒` icon → name it `OPENAI_API_KEY`)
3. Run cells sequentially
4. Upload your JD PDF when prompted
5. Paste your interview transcript in Stage 4
6. Export the full report

### Run locally

```bash
git clone https://github.com/Gbrito90/interview-intelligence-agent
cd interview-intelligence-agent
pip install -r requirements.txt
jupyter notebook interview_intelligence_agent.ipynb
```

---

## 📋 Output Example

### Stage 1 — JD Analysis
```markdown
## 📋 Análise da Vaga

**Cargo:** Senior Backend Engineer
**Senioridade:** Sênior
**Modelo de trabalho:** Remoto

### 🛠️ Stack Técnica
- **Obrigatório:** Python, FastAPI, PostgreSQL, AWS, Docker
- **Desejável:** Kubernetes, Redis, Terraform

### ⚠️ Pontos de Atenção
- Experiência com sistemas de alta disponibilidade (menciona >99.9% uptime)
- Background com equipes distribuídas — investigar autonomia e comunicação assíncrona
```

### Stage 2 — Interview Script
```markdown
### 🔧 Perguntas Técnicas

1. Como você estruturaria uma API FastAPI para suportar 10k req/s?
   💡 O que avaliar: conhecimento de async, connection pooling, caching strategy

2. Descreva como faria o deploy de um serviço Python na AWS com zero downtime.
   💡 O que avaliar: conhecimento de Blue/Green, ECS/EKS, health checks
```

### Stage 3 — Candidate Assessment
```markdown
### 📊 Scorecard

| Dimensão                    | Nota  | Observação                          |
|-----------------------------|-------|-------------------------------------|
| Aderência técnica à stack   | ⭐⭐⭐⭐⭐ | Domínio sólido de Python e AWS      |
| Profundidade técnica        | ⭐⭐⭐⭐  | Conhece Kubernetes mas pouca prática|
| Competências comportamentais| ⭐⭐⭐⭐  | Boa comunicação, evidências de ownership |

**Score geral: 4.2/5**

### 🏁 Recomendação
**[x] AVANÇAR**
```

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| `openai` | GPT-4o API calls |
| `pymupdf` | PDF text extraction |
| `IPython` | Markdown rendering in Colab |

---

## 📁 Repository Structure

```
interview-intelligence-agent/
├── interview_intelligence_agent.ipynb   # Main notebook
├── requirements.txt                      # Dependencies
├── examples/
│   ├── sample_jd.pdf                    # Sample job description
│   └── sample_report.md                 # Example output report
└── README.md
```

---

## 💡 Design Decisions

**Why separate stages instead of one prompt?**
Chaining prompts with focused instructions produces significantly better output than a single mega-prompt. Each stage has a specific temperature tuned for its task:
- Analysis: `0.3` (factual, precise)
- Question generation: `0.4` (slightly more creative)
- Assessment: `0.3` (consistent, structured)

**Why PDF input?**
Recruiters live in PDF-land. JDs come from ATSs, clients, and email attachments — almost always as PDFs. No reformatting required.

---

## 🗺️ Roadmap

- [ ] Support for URL input (scrape JD from job boards)
- [ ] ATS integration (Gupy, InHire webhooks)
- [ ] Multi-candidate comparison mode
- [ ] Streamlit UI for non-technical recruiters
- [ ] Portuguese / English language toggle

---

## 👤 Author

**Guilherme Rodrigues** — Senior Tech Recruiter transitioning to AI Engineering

6+ years recruiting for technology roles. Built this agent to automate the parts of my job that AI does better than manual work — so I can focus on what humans do better.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-guilhermebrito--rodrigues-0077B5?style=flat&logo=linkedin)](https://www.linkedin.com/in/guilhermebrito-rodrigues)
[![GitHub](https://img.shields.io/badge/GitHub-Gbrito90-181717?style=flat&logo=github)](https://github.com/Gbrito90)

---

*If this project is useful to you, leave a ⭐ — it helps with visibility.*
