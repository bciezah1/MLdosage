# MLdosage

# SNP-Based Machine Learning Pipeline for ADRD Classification

## 📖 Overview
This project implements a **machine learning pipeline** to classify ADRD cases based on SNP data. It includes:
- **Step 1:** Data Preprocessing
- **Step 2:** Feature Selection
- **Step 3:** Machine Learning Models (Logistic Regression, Gradient Boosted Trees, Neural Networks)
- **Step 4:** Model Evaluation (10-fold CV, ROC-AUC, Permutation Feature Importance)

---


## 📂 Project Structure

```plaintext
📦 Project Root
├── 📁 codes          # All scripts and code files
│   ├── step1_preprocessing.py
│   ├── step2_feature_selection.py
│   ├── step3_machine_learning.py
│   ├── step4_model_evaluation.py
│   ├── utils.py      # Helper functions
│   ├── run_pipeline.sh  # SLURM batch script (optional)
│   └── README.md
├── 📁 input          # Input files (SNP data, GWAS summary stats)
│   ├── SNP_preselected_chr*.csv
│   ├── pradi_sum_stats_sorted_model1_sorted.txt
│   └── other_files/
├── 📁 output         # Outputs from analysis
│   ├── 📁 tables     # CSV outputs (AUC scores, feature importance)
│   │   ├── PFI_Logistic_Lasso.csv
│   │   ├── PFI_XGBoost.csv
│   │   └── summary_results.csv
│   ├── 📁 plots      # Visualizations (ROC curves, feature importance)
│   │   ├── ROC_Logistic_Lasso.png
│   │   ├── ROC_XGBoost.png
│   │   ├── PFI_LightGBM.png
│   │   └── summary_plots/
│   └── logs/        # SLURM logs (if running on HPC)
└── .gitignore       # Files to ignore in version control


---

## Running the Pipeline

### **Step 1: Data Preprocessing**
- Reads raw SNP data and GWAS summary statistics.
- Filters SNPs based on **MAF ≥ 0.01** and **P-value < 0.001**.

### **Step 2: Feature Selection**
- Applies **Lasso feature selection** to reduce dimensionality.

### **Step 3: Train Machine Learning Models**
- Trains:
  - **Logistic Regression** (Lasso, Ridge, ElasticNet)
  - **Gradient Boosting** (XGBoost, LightGBM, CatBoost)
  - **Neural Networks** (MLPClassifier)
- Saves **ROC curves** in `output/plots/`.

### **Step 4: Model Evaluation**
- **10-fold cross-validation** using **ROC-AUC**.
- Computes **Permutation Feature Importance (PFI)**.
- Saves feature importance tables in `output/tables/`.

---

## Results
- **ROC curves** are stored in `output/plots/`.
- **AUC scores** and **PFI tables** are in `output/tables/`.

---

## To Do
- [ ] Add hyperparameter tuning for all models.
- [ ] Implement feature selection comparisons.
- [ ] Scale pipeline to all chromosomes.

---

## Citation
If you use this pipeline in your research, please cite:

