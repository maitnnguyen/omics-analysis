# omics-cancer-analysis

**Computational analyses of cancer genomics data — ML benchmarks, deep learning, and single-cell approaches**

Author: [Mai Nguyen](https://linkedin.com/in/mai-n-347a1331) | [dataready.onrender.com](https://dataready.onrender.com)

---

## Repository Structure

```
omics-cancer-analysis/
├── 01_somatic_mutations_ML/          # ML benchmark on somatic mutation profiles
│   ├── ovarian_mutations_ml.ipynb    # Main notebook
│   └── README.md
├── 02_histopathology_DL/             # Deep learning on whole slide images
│   ├── ubc_ocean_classification.ipynb
│   └── README.md
└── 03_clonal_evolution/              # Clonal evolution via scRNA + InferCNV (coming soon)
```

---

## Notebooks

### 01 — Somatic Mutations ML Benchmark
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/maitnnguyen/omics-cancer-analysis/blob/main/01_somatic_mutations_ML/ovarian_mutations_ml.ipynb)

**Dataset:** [electricsheepafrica/ovarian-somatic-mutations](https://huggingface.co/datasets/electricsheepareira/ovarian-somatic-mutations) — 30,000 pan-African ovarian cancer samples  
**Goal:** Predict platinum chemotherapy response from somatic mutation profiles  
**Models:** Logistic Regression · Random Forest · XGBoost · LightGBM · MLP  
**Key tools:** `datasets` (HuggingFace API) · `scikit-learn` · `xgboost` · `lightgbm` · `shap`

**Highlights:**
- Data loaded directly via HuggingFace API — no manual download
- SHAP feature importance for biological interpretation
- HRD score and BRCA1/2 status emerge as top predictors of platinum sensitivity
- Publication-quality figures throughout

---

### 02 — Histopathology Deep Learning (UBC-OCEAN)
[![Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://www.kaggle.com/competitions/UBC-OCEAN)

**Dataset:** UBC Ovarian Cancer Subtype Classification (Kaggle UBC-OCEAN)  
**Goal:** Classify ovarian cancer subtypes from whole slide imaging (WSI)  
**Models:** EfficientNet · Vision Transformer (ViT)  
**Key tools:** `PyTorch` · `timm` · `albumentations` · `openslide`

*Notebook in progress — runs entirely on Kaggle GPU*

---

### 03 — Clonal Evolution via scRNA + InferCNV *(coming soon)*

**Goal:** Infer tumour clonal structure from single-cell RNA-seq data using copy number variation  
**Approach:** Public cancer scRNA dataset → InferCNV → clonal phylogeny reconstruction  
**Key tools:** `InferCNV` · `Seurat` · `Scanpy` · `fishplot`

---

## How to Connect to HuggingFace Datasets

```python
# Install
pip install datasets huggingface_hub

# Load public dataset — no token needed
from datasets import load_dataset
df = load_dataset('electricsheepafrica/ovarian-somatic-mutations')['train'].to_pandas()

# For private/gated datasets
from huggingface_hub import login
login(token='hf_your_token')   # token from huggingface.co/settings/tokens
df = load_dataset('owner/private-dataset')['train'].to_pandas()
```

---

## Environment

```bash
pip install datasets huggingface_hub scikit-learn xgboost lightgbm shap \
            matplotlib seaborn pandas numpy torch timm albumentations
```

Or use the provided `environment.yml`:
```bash
conda env create -f environment.yml
conda activate omics-analysis
```

---

## Related Work

- [ctDNA Targeted Sequencing Pipeline](https://github.com/maitnnguyen/ctdna-targeted-pipeline)
- [ctDNA Shallow WGS Pipeline](https://github.com/maitnnguyen/ctdna-shallow-wgs-pipeline)
- [scRNA / Multiome Analysis](https://github.com/maitnnguyen/scrna-multiome-analysis)
- [DataReady — AI Data Readiness Tool](https://dataready.onrender.com)

---

## License

MIT License — see [LICENSE](LICENSE)
