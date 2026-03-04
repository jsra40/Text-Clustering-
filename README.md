# Text-Clustering-(PubMed Abstracts)

This repository contains an end-to-end text clustering pipeline that:

collects biomedical abstracts from PubMed,
preprocesses and standardizes text length,
builds multiple feature representations,
runs multiple clustering algorithms,
evaluates clusters against human labels, and
performs error analysis + visualizations.
Project Summary

Dataset: 1,000 PubMed records (Title + Abstract), years 2010–2026
Classes (balanced): 200 per label
a: Type 2 Diabetes (T2D)
b: Thyroid Disorders
c: Bone Density / Osteoporosis
d: PCOS
e: Pituitary Adenomas
Text length rule: keep docs with ≥130 words, truncate to 150 words
Preprocessing: lowercase → remove punctuation/numbers → stopwords → lemmatization
Features compared: BoW, TF‑IDF, LDA, Doc2Vec
Algorithms compared: KMeans, EM/GMM, Hierarchical (Ward)
Evaluation: Silhouette + Cohen’s Kappa (after Hungarian alignment)
Best model (final): TF‑IDF + KMeans (Kappa 0.7363, Silhouette 0.0318)
Repository Contents

Clustering.ipynb                    # Main notebook (data collection → results)
Project Report-Assignment 2-2.docx  # Final report
README.md                           # This file
Group 1 - [Clustering].pptx.        # Project presentation
Requirements

Python: 3.9+ recommended
OS: Windows/macOS/Linux
Internet access: required to collect data from PubMed inside the notebook
Install Dependencies

From the project folder, run:

pip install -U pandas numpy matplotlib seaborn scikit-learn scipy nltk gensim biopython requests
NLTK Data Downloads (first run only)

Run once (in Python or a notebook cell):

import nltk
nltk.download("stopwords")
nltk.download("wordnet")
Environment Variables / Configuration

No environment variables are required.
The notebook collects data from PubMed using public NCBI E‑utilities endpoints.

Do not submit any .env file.
How to Run (Step‑by‑Step)

Option A — Run Everything (recommended)

Open Clustering.ipynb in Jupyter Notebook or JupyterLab.
Run cells top to bottom.
The notebook will:
collect data from PubMed (balanced labels a–e),
clean text and enforce the 130–150 word constraint,
build features (BoW/TF‑IDF/LDA/Doc2Vec),
cluster with KMeans / EM(GMM) / Hierarchical,
compute Silhouette + Kappa (with Hungarian alignment),
generate evaluation tables and plots,
run error analysis (confusions and text characteristics).
Option B — Skip Data Collection (if you already have the CSV)

If you already generated Research_Papers_MainFile.csv, you can:

Place the CSV in the same folder as the notebook.
Skip the “Data Collection” section in the notebook.
Run the remaining cells to reproduce clustering, evaluation, and plots.
Notes on Reproducibility

Random seed is set in the notebook (e.g., SEED = 42) for sampling and model repeatability.
Since PubMed is live, re-collecting data may lead to small variations (new/updated abstracts).
Cohen’s Kappa uses Hungarian alignment to map cluster IDs to label IDs before scoring.
Outputs

The notebook produces:

Evaluation summary table (Feature × Algorithm → Silhouette, Kappa)
Cluster visualizations (PCA / t‑SNE)
Confusion matrix (aligned labels)
Error analysis: dominant confusion pairs + top terms/collocations
Exported dataset CSV (e.g., Research_Papers_MainFile.csv)
Authors

Ignancya Michelle George
Mamoona Zafar
Juan Sebastian Ramirez Acua
