🧠 Overview

This notebook demonstrates how to use trained scGenePT models in inference mode for perturbation prediction.
The models are fine-tuned on the Norman dataset [1] and include examples of predicting post-perturbation expression responses for both single-gene (e.g., POU3F2, CDKN1B) and gene-pair (SAMD1+ZBTB1) perturbations.
Multi-gene perturbation predictions have not been evaluated, so their performance is unknown.

🧬 Model: scGenePT

scGenePT is a collection of single-cell models for perturbation prediction, built upon the scGPT [2] framework.
It enhances scGPT by integrating language embeddings at the gene level, derived from large language models (LLMs) trained on biological knowledge sources, including:

NCBI Gene Descriptions

UniProt Protein Summaries (for protein-coding genes)

GO (Gene Ontology) annotations for:

Molecular Function (GO-F)

Biological Process (GO-P)

Cellular Component (GO-C)

Available Model Variants

scGenePT_NCBI → scGPT + NCBI Gene Card Summaries

scGenePT_NCBI+UniProt → scGPT + NCBI Gene Cards + UniProt Summaries

scGenePT_GO-F → scGPT + GO Molecular Function

scGenePT_GO-C → scGPT + GO Cellular Component

scGenePT_GO-P → scGPT + GO Biological Process

scGenePT+GO-all → scGPT + All GO Categories

This tutorial focuses on comparing scGenePT_GO-C and scGenePT_NCBI+UniProt models.

📊 Dataset: Norman et al. [1]

The Norman dataset is a CRISPR Perturb-seq dataset containing both single and dual-gene perturbations.
We use a preprocessed version containing:

105 single-gene and 131 two-gene perturbations

~91,000 total observations

Log-normalized data filtered to the top 5000 highly variable genes

The models are trained on the train split, and this notebook provides examples of:

Inference on the test split

Inference on a random control sample

Inference on a new AnnData file

⚙️ Hardware Requirements

GPU execution is highly recommended for faster inference.
The notebook can also run on CPU, though performance will be slower.

📘 Notebook Structure

The notebook includes examples of:

Loading the Norman dataset

Loading a trained scGenePT model

Predicting perturbation responses:

POU3F2 with scGenePT_GO-C

CDKN1B with scGenePT_GO-C

SAMD1+ZBTB1 with scGenePT_NCBI+UniProt

Plotting the Top 20 Differentially Expressed Genes

Running inference on:

NumPy arrays (control samples)

AnnData files (custom inputs)
