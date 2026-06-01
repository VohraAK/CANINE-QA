# CANINE-QA

<<<<<<< HEAD
Evaluation of CANINE's tokenization-free architecture on multilingual question answering with parameter-efficient LoRA fine-tuning.
=======
### GitHub Project Repo: https://github.com/VohraAK/CANINE-QA/
>>>>>>> fbc485c3171f87272d126b65054fa4e6a299229d

## Results

TyDiQA (CANINE-C)
• 64.20% EM/F1 using only 0.26% trainable parameters
• Matches original paper benchmarks with 2K training examples
• 11 languages: Arabic, Bengali, English, Finnish, Indonesian, Japanese, Kiswahili, Korean, Russian, Telugu, Thai

UQA (CANINE-S)
• 0.04% EM, complete training collapse
• Model predicts only empty spans
• Failure caused by translation artifacts, dataset imbalance, reduced model capacity

## Repository Contents

```
Reproducing_CANINE_results_tydiqa.ipynb    TyDiQA success case
Train_CANINE_S_LoRA_UQA_*.ipynb           UQA failure experiments
fixed_preprocess_uqa.py                    Character-level preprocessing
analyze_training_metrics.ipynb             Performance analysis
checkpoints/                               Model checkpoints
```

## Setup

```bash
pip install peft evaluate transformers python-Levenshtein ipywidgets
```

Training performed on Kaggle.

There might be some cells commented out which load the dataset, split and preprocess them, and cache them in local / Kaggle storage, make sure to tweak them based on the environment and requirements.

A personal HuggingFace token was used to push model checkpoints to HF repositories under `VohraAK`. However, I have included downloaded model checkpoints for the three main training sessions under the `checkpoints` directory.

Evaluation assets are available under `assets` directory.

## Key Finding

Character-level models excel on native multilingual data but fail catastrophically on translated low-resource datasets due to distribution mismatch and preprocessing challenges.

Authors: Abdullah Khurram Vohra, Muhammad Mahad Bhatti, Mir Huzaifa Gujjar
Course: CS5316 NLP Theory and Applications, LUMS
