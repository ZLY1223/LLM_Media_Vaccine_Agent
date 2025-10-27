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
| **M2 – Media Diet Model** | Incorporates personalized media exposure on top of demographics (replacing belief inputs). | Demographics + Media Diet (Left Echochamber / Center-ish / Right Echochamber / Misinformation-Only) |

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
Implements all **M0–M2** configurations using **GPT-4o-mini** and **GPT-4.1**.  
- **M0 – Demographics-Only:** baseline simulation using demographic attributes  
- **M1 – Survey Model:** adds prior belief variables to demographics  
- **M2 – Media Diet Model:** integrates demographics, beliefs, and media-exposure context  
  - Media diet assignment derived from participants’ demographics and beliefs  
  - Produces baseline results for comparison with Gemini-2.5-Flash and LLaMA-4-17B  

---

### 🌐 **Gemini_2_5_flash.ipynb**
Runs the same M0–M2 pipeline on **Gemini-2.5-Flash** (Google model).  
- Mirrors the ChatGPT notebook to ensure architecture-consistent prompts and evaluation  
- Provides a **cross-vendor comparison** between OpenAI (GPT) and Google (Gemini) systems  
- Evaluates robustness, reasoning diversity, and consistency across media-exposure conditions  

---

### 🦙 **Llama_4_17b.ipynb**
Runs the same experiments on **LLaMA-4-17B** (open-weight model via Hugging Face).  
Serves as the **open-source baseline** to benchmark against closed-source families (GPT / Gemini).  

---

### ⚙️ **TextGrad.ipynb**
Implements **prompt-engineering optimization** using **TextGrad**, applied to all LLM families (GPT, Gemini, LLaMA).  
- Optimizes reasoning within the `% Task Prompt` section  
- Adjusts trainable segments between `% Task Prompt` and `Output format`  
- Evaluated by accuracy, balanced accuracy, and recall across M2 settings  

---

### 🔁 **Counterfactual_Analysis.ipynb**
Implements multiple **M2 counterfactual variants** across all models (GPT-4o-mini / GPT-4.1 / Gemini-2.5-Flash / LLaMA-4-17B):  
- **Random Diet Assignment** – random media exposure per participant  
- **Random 5 Articles Sampling** – five random articles per diet  
- **Random 10 Articles Sampling** – ten random articles per diet  
- **Demographics-Only Assignment** – removes belief layer  
- **Misinformation-Only** – isolates misinformation exposure  
- **Public-Health-Only** – isolates official health-source exposure  

These experiments assess how media-exposure variability and model family jointly shape simulated vaccine decisions.

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
