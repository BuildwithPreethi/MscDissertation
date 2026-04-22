# MscDissertation
Exploring Weakly Supervised Multitask Learning for Cross Domain Spam Detection in News Media

## Overview
This project explores spam detection in online news using weak supervision and multitask learning. 
Since labelled datasets are limited, heuristic labelling functions are used to generate weak labels, 
and deep learning models are trained to improve performance across multiple domains.

## Objectives
- Generate spam labels using weak supervision
- Build baseline and transformer-based models
- Apply multitask learning (MTL) to improve classification
- Evaluate performance across domains

## Dataset
The dataset used in this project is publicly available on Zenodo:
https://zenodo.org/api/records/7394851/files-archive

The dataset consists of a large collection of news articles with the following attributes:
- Article title
- Article content (text)
- Category labels (e.g., politics, health, business, etc.)
- Source of publication
- Publication date and metadata

Note: Spam labels were generated using heuristic rules.

### Important Notes
- The dataset does **not contain spam labels**
- Spam labels were generated using **weak supervision techniques**
- Multiple heuristic rules were used to approximate spam classification

### Usage Instructions
Due to size and licensing considerations, the dataset is **not included** in this repository.

1. Download the dataset from the link above  
2. Extract it locally  
3. Place it inside a `data/` folder:

## Methodology

### Weak Supervision
Spam labels were generated using heuristic labelling functions:
- Clickbait detection
- Excessive punctuation and capitalisation
- Title-content mismatch
- Rare source detection
- Duplicate titles across sources
- Source burst activity

### Models Implemented

#### Baseline
- TF-IDF + Logistic Regression

#### Deep Learning
- RoBERTa Transformer (single-task)

#### Multitask Learning Model
- Shared encoder (RoBERTa)
- Spam classification (primary task)
- Category prediction (auxiliary task)
- Source prediction (auxiliary task)

## Evaluation Metrics
- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

## Results

### Model Comparison (Ablation Study)
Results/06 Result_Summary.png

The ablation study shows the impact of different model configurations:

- **Baseline (TF-IDF + Logistic Regression)**: F1 ≈ 0.41  
- **RoBERTa (Single-task)**: F1 ≈ 0.42  
- **RoBERTa + Category (MTL)**: **Best performance with F1 ≈ 0.57**  
- **RoBERTa + Category + Source**: Slight improvement (F1 ≈ 0.54)  
- **RoBERTa + Metadata tokens**: No consistent gain due to noise  

Multitask learning with category prediction significantly improves spam detection performance.

### Baseline Model (TF-IDF + Logistic Regression)
Results/01 Baseline (TF-IDF + LR).png

The baseline model performs well on legitimate news but struggles with spam detection due to limited feature representation.

### RoBERTa (Single-task Spam Detection)
Results/02 RoBERTa single task spam detection.png

Transformer-based models improve representation learning, but performance is still limited when trained on a single task.

### Multitask Learning (Spam + Category)
Results/03 RoBERTa MTL (Spam+Category).png

Adding category prediction as an auxiliary task improves:
- Recall for spam detection  
- Overall model robustness  

### Multitask Learning (Spam + Category + Metadata Tokens)
Results/04 RoBERTa MTL (Spam+Category) with metadata token.png

The model incorporates metadata tokens to enrich contextual understanding.  
However, improvements are marginal, suggesting that metadata introduces noise in some cases.

### Extended Multitask Learning Model (Spam + Category + Source)
Results/05 RoBERTa MTL model (spam + category + source).png

Including source prediction adds complexity but provides limited gains due to class imbalance in source labels.

## 📌 Key Insights

- Multitask learning significantly improves spam detection performance  
- Category prediction is the most beneficial auxiliary task  
- Source prediction provides minimal improvement  
- Metadata tokens do not consistently enhance performance  
- Class imbalance remains a key challenge for spam detection  

## Project Structure
MscDissertation/
├── Results/ # Images of the results obtained
├── notebooks/ # Jupyter notebooks for analysis and modelling
├── Dissertation_Report.pdf
├── requirements.txt
└── README.md
- Dataset is not included. Download from Zenodo link provided above.

## How to Run

1. Clone the repository:
https://github.com/BuildwithPreethi/MscDissertation.git
2. Install dependencies:
pip install -r requirements.txt
3. Run the notebook:

## Key Contributions
- Applied weak supervision for scalable spam detection
- Demonstrated effectiveness of multitask learning in NLP
- Evaluated cross-domain robustness

## Future Work
- Improve weak labelling functions
- Explore advanced weak supervision frameworks
- Incorporate richer metadata features

## Author
Preethi Sivaradjou  
MSc Data Science – University of Surrey