# 🧬 scGenePT Inference Notebook

## 🧠 Overview
This notebook demonstrates how to use trained **scGenePT** models in **inference mode** for **perturbation prediction**.  
- Models are fine-tuned on the **Norman dataset [1]**  
- Examples include **single-gene** perturbations (e.g., *POU3F2*, *CDKN1B*)  
- Examples include **gene-pair** perturbations (e.g., *SAMD1+ZBTB1*)  
- Multi-gene perturbation predictions **have not been evaluated**, so performance is unknown  

---

## 🧬 Model: scGenePT
**scGenePT** is a collection of single-cell models for perturbation prediction, built on the **scGPT [2]** framework.  
It integrates **gene-level language embeddings** derived from LLMs trained on biological knowledge sources:  
- **NCBI Gene Descriptions**  
- **UniProt Protein Summaries** (protein-coding genes)  
- **GO (Gene Ontology) annotations**:  
  - Molecular Function (GO-F)  
  - Biological Process (GO-P)  
  - Cellular Component (GO-C)  

### Available Model Variants
| Model | Description |
|-------|-------------|
| `scGenePT_NCBI` | scGPT + NCBI Gene Card Summaries |
| `scGenePT_NCBI+UniProt` | scGPT + NCBI + UniProt Summaries |
| `scGenePT_GO-F` | scGPT + GO Molecular Function |
| `scGenePT_GO-C` | scGPT + GO Cellular Component |
| `scGenePT_GO-P` | scGPT + GO Biological Process |
| `scGenePT+GO-all` | scGPT + All GO Categories |

> This tutorial focuses on **scGenePT_GO-C** and **scGenePT_NCBI+UniProt** models.  

---

## 📊 Dataset: Norman et al. [1]
The **Norman dataset** is a CRISPR Perturb-seq dataset with **single- and dual-gene perturbations**.  

**Preprocessed version used in this notebook:**
- 105 single-gene and 131 two-gene perturbations  
- ~91,000 total observations  
- Log-normalized data filtered to the **top 5000 highly variable genes**  

**Notebook examples include:**
- Inference on the **test split**  
- Inference on a **random control sample**  
- Inference on a **new AnnData file**  

---

## ⚙️ Hardware Requirements
- **GPU recommended** for faster inference  
- CPU execution is possible but slower  

---

## 📘 Notebook Structure
The notebook provides examples of:
1. **Loading the Norman dataset**  
2. **Loading a trained scGenePT model**  
3. **Predicting perturbation responses**  
   - *POU3F2* with `scGenePT_GO-C`  
   - *CDKN1B* with `scGenePT_GO-C`  
   - *SAMD1+ZBTB1* with `scGenePT_NCBI+UniProt`  
4. **Plotting the Top 20 Differentially Expressed Genes**  
5. Running inference on:  
   - NumPy arrays (control samples)  
   - AnnData files (custom inputs)  

---

## 📚 References
1. Norman, Thomas M., et al. "Exploring genetic interaction manifolds constructed from rich single-cell phenotypes." *Science* 365.6455 (2019): 786-793.  
2. Cui, Haotian, et al. "scGPT: toward building a foundation model for single-cell multi-omics using generative AI." *Nature Methods* (2024): 1-11.
