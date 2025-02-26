# Vaccine_LLM_Prompt_Engineering
## Overview
This project explores the application of **Large Language Models (LLMs)** in predicting vaccine hesitancy.
We aim to:
- Optimize **prompt engineering** to improve LLM predictions on vaccine-related attitudes.
- Assess how different factors (e.g., **demographics, professions, prior beliefs**) influence vaccine hesitancy.
- Compare the performance of various LLMs (e.g., **LLaMA-2, GPT-4**) on this task.
## Methodology
We follow a structured approach:

1. **Data Collection**:
   - We use a dataset of vaccine-related survey responses.
   - Responses are categorized into four groups: **Strongly Accept, Accept, Hesitant, Reject**.

2. **Prompt Engineering**:
   - We design multiple prompts, including:
     - **Baseline Prompt** (Direct Questioning)
     - **Chain-of-Thought (CoT) Prompting**
     - **Few-Shot Prompting with Examples**
   - Examples of prompts can be found in the [`prompts/`](./prompts/) directory.

3. **LLM Experiments**:
   - **Model:** Meta’s LLaMA-2-7B & OpenAI’s GPT-4
   - **Frameworks:** Hugging Face Transformers, PyTorch, CUDA
   - **Inference Code:** [`models/inference.py`](./models/inference.py)

4. **Evaluation Metrics**:
   - Accuracy of LLM-generated responses vs. ground truth
   - Perplexity scores of different prompt designs

## Current Progress
✔ **Data preparation completed**  
✔ **Initial prompt engineering tested**  
✔ **Baseline model inference implemented**  
🟡 **Fine-tuning experiments in progress**  
🟡 **Evaluating prompt performance using real-world survey data**

## Challenges & Solutions
🔹 **Challenge 1: LLM prompt sensitivity**
- Different wording significantly affects model responses.
- **Solution:** Iterative testing of prompt formats to ensure consistency.

🔹 **Challenge 2: CUDA memory limitations on large models**
- Running LLaMA-2-7B on limited GPU resources caused **Out-of-Memory (OOM) errors**.
- **Solution:** Experimenting with **LoRA fine-tuning** and memory-efficient inference strategies.

🔹 **Challenge 3: Lack of labeled training data for supervised fine-tuning**
- **Solution:** Exploring **self-supervised learning** and data augmentation techniques.

## How to Run

### 1️⃣ Install Dependencies
```bash
pip install -r requirements.txt
python models/inference.py --model llama-2 --prompt prompts/optimized_prompt_v2.txt

### 2️⃣ Run Model Inference

## Future Work
- 📌 Experimenting with **fine-tuning methods** to improve model consistency.
- 📌 Extending the study to other public health topics.
- 📌 Comparing LLM responses with real-world survey results.

