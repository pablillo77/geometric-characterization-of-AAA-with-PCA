[README_AAA.md](https://github.com/user-attachments/files/29818873/README_AAA.md)
# Geometric Characterization of Abdominal Aortic Aneurysms with PCA

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/pablillo77/geometric-characterization-of-AAA-with-PCA/blob/main/PCA_Shape_Modes_public.ipynb)

A **statistical shape model** of abdominal aortic aneurysms (AAA) built from 3D CT-derived geometry. Instead of analyzing each anatomical measurement in isolation, the model finds the **principal directions of shape variation** across a patient cohort, reducing a high-dimensional geometry problem to a handful of interpretable *shape modes*.

MSc thesis project, *Three-dimensional geometric characterization of AAA in a local population*, defended at Universidad Favaloro (Nov 2024).

---

## What this does

Each aneurysm is summarized by a set of geometric measurements (diameters, lengths, angles). The pipeline turns those raw measurements into a compact, interpretable model of how aneurysm shape varies across patients, and whether that variation clusters into distinct morphological groups.

## Method

1. **Data preparation.** Geometric measurements per patient, keeping only shape-relevant variables and discarding identifiers and auxiliary fields.
2. **Standardization + PCA.** Variables live in different units (mm vs. degrees), so each is standardized before PCA runs on the correlation matrix, preventing any single variable from dominating by scale.
3. **Dimensionality selection.** A scree plot (per-component and cumulative variance) identifies how many modes to retain. **Five principal components explain ~80% of total shape variance.**
4. **Projection to shape space.** Each patient becomes a point whose coordinates are their shape scores along each mode.
5. **Clustering.** K-Means and Ward hierarchical clustering (with dendrogram) group patients by shape; an interactive 3D scatter (PC1, PC2, PC3) shows the separation.
6. **Morphological profiling.** Per-cluster boxplots reveal which diameters and angles distinguish each group, giving the clusters an anatomical reading.
7. **Shape-mode reconstruction.** Synthetic shapes are reconstructed by moving plus/minus k times sigma along each principal direction from the mean shape, making each abstract component visually interpretable.

## Key result

Five principal components capture roughly 80% of the geometric variance in the cohort, establishing a compact reference framework relevant to **adaptive endograft design** and **clinical simulation**.

## Data & privacy

The repository contains **no raw patient data and no CT images**. The notebook works only from **derived, aggregated geometric measurements**, so no patient-identifiable information is exposed.

## Tech stack

Python, NumPy, pandas, scikit-learn (PCA, KMeans, AgglomerativeClustering), SciPy, Matplotlib, Seaborn.

## Run it

Click the **Open in Colab** badge above. No local setup required.

---

*Author: Pablo Giménez. MSc Biomedical Engineering, MSc Electronics Engineering.*
