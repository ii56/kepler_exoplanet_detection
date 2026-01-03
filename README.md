# Kepler Exoplanet Classification Using Machine Learning

## Project Overview

This project builds a **scientifically grounded machine learning system** to classify Kepler Objects of Interest (KOIs) into:

- **CONFIRMED**
- **CANDIDATE**
- **FALSE POSITIVE**

using real astrophysical data from the **NASA Exoplanet Archive**.

Unlike simple ML demos, this project emphasizes:

- Scientific feature engineering  
- Proper training / validation separation  
- Model comparison at scale  
- Real-world deployment readiness (usage demo, retraining, saved models)

---

## Objectives

- Build a **robust exoplanet classification pipeline**
- Compare **multiple ML algorithms objectively**
- Validate performance using **confusion matrices & metrics**
- Test models on **unseen NASA data**
- Produce **reusable trained models** and a **demo interface**


---

## Dataset

### Primary Dataset (Training & Evaluation)
- **Kepler Objects of Interest (KOI) Dataset**
- Source: **NASA Exoplanet Archive** (via Kaggle)
- ~9,500 labeled KOIs
- Detection method: **Transit photometry**
- Multi-class target variable: `koi_disposition`
  - CONFIRMED
  - CANDIDATE
  - FALSE POSITIVE
- Used for:
  - Feature engineering
  - Model training
  - Validation and benchmarking

### External / Unseen Dataset (Usage Demonstration)
- **NASA Exoplanet Archive – Cumulative KOI Table (2026 release)**
- Source: **NASA Exoplanet Archive**
- Represents a newer and more complete version of the KOI catalog
- Used **exclusively for model usage and inference demonstration**
- **Not used during training**, ensuring no data leakage

---

## Feature Engineering (Critical Step)

Raw astrophysical parameters were transformed into **model-ready scientific features**, including:

- Log-scaled quantities (period, duration, depth, insolation)
- Error aggregation features
- Physically meaningful ratios:
  - `depth_to_snr_ratio`
  - `planet_to_star_radius_ratio`

This step is what made **tree-based models perform exceptionally well**.

---

## Models Trained

A wide range of algorithms were trained and evaluated:

| Category       | Models                                           |
|----------------|--------------------------------------------------|
| Linear         | Logistic Regression, Ridge                       |
| Tree-based     | Random Forest, Extra Trees, Gradient Boosting    |
| Distance       | KNN                                              |
| Probabilistic  | Naive Bayes, Gaussian Process                    |
| Kernel         | SVM (RBF)                                        |
| Neural         | MLP Neural Network                               |

---

## Evaluation Metrics

Each model was evaluated using:

- Accuracy
- Precision (Macro)
- Recall (Macro)
- F1-score (Macro)
- ROC-AUC (One-vs-Rest)

Results were aggregated into a **single unified comparison table**.

---

## Top Performing Models

After objective evaluation, the **top 3 models** were selected:

1. **Extra Trees**
2. **Random Forest**
3. **Gradient Boosting**

These models showed:
- Very high CONFIRMED / FALSE POSITIVE separation
- Minimal class confusion
- Strong generalization

They were **retrained cleanly** and saved for reuse.

---

## Confusion Matrix Insights

Key observations:
- CONFIRMED planets are classified with **>99% accuracy**
- Most errors occur between **CANDIDATE ↔ FALSE POSITIVE**, which reflects real astrophysical ambiguity
- Extra Trees showed the **cleanest diagonal dominance**

---

## Model Usage & Demo

The project includes a **usage & demo folder** that have notebooks that:

- Applies trained models to unseen NASA data
- Displays per-model predictions + confidence
- Compares predictions against true NASA labels
- Highlights **correct vs incorrect** classifications
- Exports results as a **visual table image**

---

## Key Learning Outcomes

- High offline accuracy does **not guarantee** correct predictions on new data
- Feature consistency between training and usage is **critical**
- Tree-based models excel on structured astrophysical data
- Retraining + scaler alignment is mandatory for production systems

---

## Saved Artifacts

The project saves:
- Final trained models
- NASA-aligned standard scaler
- Training feature list
- Prediction result tables
- Visualization outputs

This allows **reuse without retraining**.

---

## Scientific Integrity Note

This project intentionally avoids:
- Data leakage
- Training on external datasets
- Inflated performance reporting

All results reflect **honest generalization performance**.

---

## Conclusion

This project is a full ML pipeline with:

- Real astrophysical data
- Proper preprocessing
- Multiple algorithms
- Rigorous evaluation
- Deployment-aware usage demo

It mirrors how **ML is used in real astronomical research pipelines** based on my knowledge.

---

## Citation

## Citation

This project makes use of publicly available datasets provided by NASA and Kaggle. Proper attribution is given below.

### NASA Exoplanet Archive

NASA Exoplanet Science Institute (NExScI).  
**NASA Exoplanet Archive – Cumulative Kepler Objects of Interest (KOI) Table.**  
Accessed: January 2026.  
Available at:  
https://exoplanetarchive.ipac.caltech.edu/cgi-bin/TblView/nph-tblView?app=ExoTbls&config=cumulative  

> The NASA Exoplanet Archive is operated by the California Institute of Technology under contract with the National Aeronautics and Space Administration (NASA).

---

### Kaggle – Kepler Exoplanet Search Results

NASA Exoplanet Archive (via Kaggle).  
**Kepler Exoplanet Search Results Dataset.**  
Kaggle Dataset.  
Available at:  
https://www.kaggle.com/datasets/nasa/kepler-exoplanet-search-results  

> This dataset is a curated distribution of Kepler mission results hosted on Kaggle for data science and machine learning research.

---

### Usage Disclaimer

This project is intended **solely for educational and research purposes**.  
All data usage complies with the respective dataset licenses and attribution requirements.
