# Honest AI for Food Security: Prototypical Network Approach

**Author:** Muttaqin Muzakkir – Universitas Indonesia

---

## Overview

This project addresses **interpretable plant disease classification** in the context of food security. Unlike standard black-box AI models, our Prototypical Network produces **transparent predictions** by learning a “prototype” embedding for each class, enabling domain experts to understand why a prediction was made.

---

## Key Results

* **Interpretability:** Visual prototypes per class reveal the ideal representative learned by the model, allowing inspection of class-defining features.
* **Performance:** Achieves competitive macro F1-score and accuracy on the PlantVillage dataset while remaining fully interpretable.
* **Robustness:** Aggressive augmentation ensures the model focuses on invariant, disease-relevant features rather than spurious correlations.
* **Efficiency:** Lightweight CNN encoder with a 64-dimensional embedding space balances performance and computational cost.

---

## Caveats & Considerations

* **Data Limitations:** The model relies on labeled plant disease images; rare or unseen disease variants may not be well-represented.
* **Prototype Sensitivity:** Learned prototypes reflect training data distributions; out-of-distribution samples may reduce interpretability.
* **Scaling:** While effective for moderate-sized datasets, large-scale deployment may require optimized training and data handling pipelines.

---

## Why This Approach is Superior

1. **Intrinsic Interpretability:** Directly maps each class to a visual prototype.
2. **Metric Learning:** Embeddings cluster similar diseases, enabling transparent comparison and confidence estimation.
3. **Targeted Augmentation:** Reduces reliance on background artifacts, emphasizing disease-specific patterns.
4. **Reproducibility:** Fully deterministic pipeline from preprocessing to evaluation.

---

## Reproduction Steps

1. **Clone the repository**

```bash
git clone https://github.com/muttyqt15/interpretable-plant-classification.git
cd interpretable-plant-classification
```

2. **Set up environment**

```bash
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. **Configure dataset path** in `CONFIG['data_path']` to point to PlantVillage images.

4. **Run the pipeline**

```python
from main import main
main()
```

* `RUN_TRAINING = True` → train model from scratch
* `RUN_TRAINING = False` → load saved model and generate final evaluation and prototype visualizations

5. **Inspect outputs**

* Training metrics: loss, accuracy, F1-score per epoch
* Prototype images per class
* Classification report and evaluation on test set
