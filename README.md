# 🧠 LLM_Media_Vaccine_Agent

This repository contains experimental notebooks and scripts for simulating COVID-19 vaccine decision-making using **Large Language Models (LLMs)** — including **GPT-4o-mini**, **GPT-4.1**, **Gemini-2.5-Flash**, and **LLaMA-4-17B**.  
Each notebook corresponds to a distinct model configuration (M0–M2) or analysis stage in the study.

---

## 📚 Project Overview

This project investigates how **demographics**, **prior beliefs**, and **media exposure** jointly influence simulated vaccine decisions.  
By comparing multiple LLM families (OpenAI, Google, and open-source), we examine how model reasoning and information inputs shape behavioral predictions.

| Model | Description | Key Input Features |
|--------|--------------|--------------------|
| **M0 – Demographics Only** | Baseline model that predicts vaccine decisions purely from demographic attributes. | Age, gender, income, education, region |
| **M1 – Survey Model** | Adds prior-belief variables on top of demographics (survey-based). | Demographics + attitudes toward vaccine, trust in science, perceived severity, etc. |
| **M2 – Media Diet Model** | Incorporates personalized media exposure on top of demographics (replacing belief inputs). | Demographics + Media Diet (Left Echochamber / Center-ish / Right Echochamber / Misinformation-Only / Public-Health-Only) |

---

## 🧩 Repository Structure
```
LLM_Media_Vaccine_Agent/
├── data/ # Example input data or small samples
├── Chatgpt.ipynb # Main pipeline for GPT-4o-mini / GPT-4.1 / Gemini-2.5-Flash
├── Llama_4_17b.ipynb # LLaMA-4-17B-based experiments
├── Counterfactual_Analysis.ipynb # M2 counterfactual variants (random diet, random articles, etc.)
├── TextGrad.ipynb # Prompt optimization via TextGrad (trainable segments between % Task Prompt and Output format)
└── README.md
```

---

## 🔍 Notebook Descriptions

### 🤖 **Chatgpt.ipynb**
Implements all M0–M2 models using **GPT-4o-mini**, **GPT-4.1**, and **Gemini-2.5-Flash**.  
- **M0:** Demographics-only baseline  
- **M1:** Demographics + Prior Beliefs  
- **M2:** Demographics + Media Diet  
  - Media-diet assignment derived from participants’ demographic and belief profiles  
  - Predicts vaccine decisions under each media exposure type  
  - Enables cross-model comparison among GPT and Gemini families  

---

### 🦙 **Llama_4_17b.ipynb**
Runs the same modeling pipeline on **LLaMA-4-17B** (open-weight model) to test generalizability across **closed-source (GPT, Gemini)** and **open-source** LLMs.

---

### ⚙️ **TextGrad.ipynb**
Implements **prompt-engineering optimization** using **TextGrad**:  
- Improves reasoning quality within the `% Task Prompt` block  
- Optimizes trainable text segments between `% Task Prompt` and `Output format`  
- Evaluated by accuracy, balanced accuracy, and recall across M2 settings  

---

### 🔁 **Counterfactual_Analysis.ipynb**
Implements multiple **M2 counterfactual variants** to assess model robustness:  
- **Random Diet Assignment** – each participant randomly assigned a media diet  
- **Random 5 Articles Sampling** – five random articles per diet  
- **Random 10 Articles Sampling** – ten random articles per diet  
- **Demographics-Only Assignment** – removes belief layer  
- **Misinformation-Only** – isolates misinformation exposure  
- **Public-Health-Only** – isolates official health-source exposure  

These counterfactuals evaluate how media randomness or selective exposure alters simulated vaccine decisions across GPT, Gemini, and LLaMA models.

---

## 💾 Data
Small-scale example data (e.g., demographic and belief samples) are stored under:
```
/data/
```
Larger or full-scale datasets are **available upon request** due to privacy and storage limitations.

---

## 🧠 Models Used
- **GPT-4o-mini / GPT-4.1** — OpenAI API  
- **Gemini-2.5-Flash** — Google API  
- **LLaMA-4-17B** — via Hugging Face Router  
- **TextGrad** — for prompt optimization and reasoning-segment fine-tuning  

---

## ⚙️ Environment Setup
Install dependencies:
```bash
pip install -r requirements.txt
