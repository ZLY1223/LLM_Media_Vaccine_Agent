# 🧠 LLM_Media_Vaccine_Agent

This repository contains experimental notebooks and scripts for simulating COVID-19 vaccine decision-making using Large Language Models (LLMs).  
Each notebook corresponds to a distinct model configuration (M0–M2) or analysis stage in the study.

---

## 📚 Project Overview

The project explores how **demographics**, **prior beliefs**, and **media exposure** jointly influence simulated vaccine decisions.  
We use multiple LLMs (GPT-4o-mini, GPT-4.1, Gemini-2.5-Flash, and LLaMA-4-17B) to model different information conditions.

| Model | Description | Key Input Features |
|--------|--------------|--------------------|
| **M0 – Demographics Only** | Baseline model that predicts vaccine decisions purely based on demographic attributes. | Age, gender, income, education, region |
| **M1 – Survey Model** | Incorporates demographic + prior belief variables (survey-based). | Demographics + attitudes toward vaccine, trust in science, perceived severity, etc. |
| **M2 – Media Diet Model** | Adds media exposure information on top of demographics (Replace beliefs). | Demographics + personalized media diet (Left Echochamber / Center-ish / Right Echochamber / Misinformation Only) |

---

## 🧩 Repository Structure
```
LLM_Media_Vaccine_Agent/
├── data/ # Example input data or small samples
├── Chatgpt.ipynb # Main pipeline for GPT-4o-mini / GPT-4.1
├── Llama_4_17b.ipynb # LLaMA-4-17B-based experiments
├── Counterfactual_Analysis.ipynb # M2 counterfactual variants (random diet, random articles, etc.)
├── TextGrad.ipynb # Prompt optimization via TextGrad (trainable segments between % Task Prompt and Output format)
└── README.md
```

---

## 🔍 Notebook Descriptions

### 🧮 **Chatgpt.ipynb**
Implements all M0–M2 models using **GPT-4o-mini** or **GPT-4.1**.  
- **M0:** Demographics-only baseline  
- **M1:** Demographics + Prior Beliefs  
- **M2:** Demographics + Media Diet  
  - Media diet assignment derived from participants’ demographic and belief profiles  
  - Used to predict final vaccine decisions under each media exposure type  

---

### 🦙 **Llama_4_17b.ipynb**
Runs the same pipeline on **LLaMA-4-17B** (open-weight model) for cross-model comparison.  
Used to test generalizability across closed- and open-source LLM families.

---

### ⚙️ **TextGrad.ipynb**
Prompt engineering optimization pipeline using **TextGrad**:  
- Focuses on improving the reasoning quality within `% Task Prompt` block  
- Optimizes trainable text segments between `% Task Prompt` and `Output format`  
- Evaluated by accuracy, balanced accuracy, and recall across M2 configurations  

---

### 🔁 **Counterfactual_Analysis.ipynb**
Implements multiple **M2 counterfactual conditions** to test robustness:  
- **Random Diet Assignment** – each participant randomly assigned a media diet  
- **Random 5 Articles Sampling** – 5 random articles per media diet  
- **Random 10 Articles Sampling** – 10 random articles per media diet  
- **Demographics-Only Assignment** – removes belief layer  
- **Misinformation-Only** – isolates misinformation exposure  
- **Public Health-Only** – isolates official health source exposure  

These experiments test how media randomness or selective exposure alters predicted vaccine behavior.

---

## 💾 Data
Small-scale example data (e.g., demographic and belief samples) are stored under:
Larger or full-scale datasets are available upon request due to privacy and storage limitations.

---

## 🧠 Models Used
- **GPT-4o-mini / GPT-4.1** (OpenAI API)
- **Gemini-2.5-Flash** (Google API)
- **LLaMA-4-17B** (via Hugging Face Router)
- **TextGrad** (for prompt optimization)

---

## ⚙️ Environment Setup
Install dependencies:
```bash
pip install -r requirements.txt
