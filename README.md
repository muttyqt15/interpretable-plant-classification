# Honest AI: An Inherently Interpretable Vision System

A from-scratch implementation of a **Prototypical Network** that moves beyond "black box" models to deliver high-performance, truly explainable image classification.

[*Kaggle Notebook Implementation*](https://www.kaggle.com/code/hayaye/inherently-interpretable-classification)


---

## The Core Innovation: Visual, Auditable Reasoning

This system doesn't just predict; it **explains**. By learning a single, representative **"prototype"** for each plant disease, its reasoning is transparent and auditable. A prediction is made by finding the closest prototype, allowing an expert to instantly verify the *why* behind any decision.

This is what the model learns, the **archetypal example** for each disease.

---

## The Problem & Solution

**The Problem:** Standard AI models are "black boxes." In high-stakes domains like agriculture, a farmer will not trust a diagnosis they cannot understand. This "trust gap" is the biggest barrier to real-world adoption.

**My Solution:** I built a Prototypical Network from first principles. Instead of just classifying, the model learns a **semantically meaningful embedding space** where distances represent visual similarity. This makes the model's reasoning process itself the explanation.

---

## Key Results & Features

- **High Performance:** Achieved a **90% weighted F1-score** on the PlantVillage dataset, proving interpretability does not require sacrificing accuracy.  
- **Built from Scratch:** Engineered a computationally efficient CNN (~500k parameters) and a **custom prototypical loss function** in PyTorch.
- **Robust & Trustworthy:** The system's reasoning aligns with plant pathology, mitigating risks of spurious correlations (e.g., background artifacts).

---

## Architecture Overview

- **CNN Encoder:** A lightweight CNN processes an input image and maps it into a **64-dimensional embedding vector**.  
- **Prototype Calculation:** The mean embedding vector ("prototype") is calculated for all images in a class.  
- **Metric Learning (Custom Loss):** Minimizes distance to the correct prototype while maximizing distance to others.  
- **Inference:** Classifies a new image by finding the **closest class prototype** in Euclidean space.

---

## Reproduction Steps

1. **Clone the repository:**
```bash
git clone https://github.com/muttyqt15/interpretable-plant-classification.git
cd interpretable-plant-classification
````

2. **Set up environment:**

```bash
pip install -r requirements.txt
```

3. **Configure dataset path in `config.py`.**

4. **Run the pipeline:**

```bash
python main.py
```

---

## Tech Stack

* **Core:** Python, PyTorch
* **Data Handling:** Pandas, NumPy, Scikit-learn
* **Visualization:** Matplotlib, Seaborn
