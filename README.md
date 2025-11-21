# StatGenerative Model — Synthetic Data Generation Research

**Author:** Abdul Quadir Owais (Muhammed)
**Advisor:** Dr. Michael Soltys
**Program:** M.S. Computer Science, CSU Channel Islands



## 📄 Abstract

This thesis investigates two fundamentally different approaches for generating synthetic tabular data:

* **CTGAN (Conditional Tabular GAN):** a deep generative neural model capable of modeling complex, mixed-type tabular data distributions.
* **Adaptive Kernel Density Estimation (AKDE):** a transparent, non-parametric statistical method that adapts bandwidth locally to better capture multimodal and irregular distributions.

Using the **Dry Beans Dataset** from the UCI Machine Learning Repository, both models are evaluated through:

* **Statistical fidelity metrics:** Kolmogorov–Smirnov statistic, Wasserstein distance, coverage percentage, variance ratio, and correlation preservation.
* **Visual diagnostics:** KDE / histogram overlays, PCA projections, pairwise scatterplots, boxplots, violin plots, and correlation heatmaps.

Results consistently show that **AKDE preserves distributional shapes, outlier behavior, and inter-feature correlations more faithfully than CTGAN**, especially on small–medium tabular datasets. CTGAN offers higher generative flexibility but demonstrates variance drift and instability in low-data regimes.

This repository contains the full thesis, announcement documents, code, models, datasets, and experimental notebooks required to fully reproduce the study.

---

## 📂 Repository Structure

```
SynExploration/
├── AIEN/                          # Future/experimental models (AIEN, VAE)
│   ├── aien.py.ipynb
│   ├── aien1.py.ipynb
│   ├── aien_keras.ipynb
│   ├── best_model.pth
│   ├── best_aien_model.weights.h5
│   ├── vae_model.pth
│   ├── bean-clean.csv
│   ├── bean.csv
│   ├── synthetic_data.csv
│   └── synthetic_data_kde.csv
│
├── akde/                          # AKDE code & synthetic data results
│   ├── test_akde-bean.ipynb
│   ├── test_result.ipynb
│   ├── k-mean_kde-bean_on_*.ipynb
│   ├── bean.csv
│   ├── bean-clean.csv
│   ├── bean1.csv ... bean5.csv
│   ├── syn_bean1.csv ... syn_bean5.csv
│   ├── syn_bean_merged.csv
│   └── syn_with50.csv
│
├── ctgan/                         # CTGAN implementation & outputs
│   ├── ctgan_synGenerator.ipynb
│   ├── k-mean_kde-bean_on_enitre.ipynb
│   ├── k-mean_kde-bean_on_syn_ctgan.ipynb
│   ├── bean-clean.csv
│   ├── synthetic_data_1.csv ... synthetic_data_5.csv
│   └── merged_syn_data.csv
│
├── bean_kde/                      # Classical KDE (baseline) experiments
│   ├── test_kde-bean.ipynb
│   ├── k-mean_kde-bean_on_*.ipynb
│   ├── bean.csv / bean-clean.csv
│   └── syn_bean*.csv
│
├── iris_dataset/                  # Auxiliary validation experiments
│   ├── iris_data*.csv
│   ├── synthetic_iris_data*.csv
│   ├── kde_gen.csv
│   └── test_kde.ipynb
│
└── thesis/                        # Required documentation
    ├── Thesis_Synthetic_Data.pdf        # Full thesis (PDF)
    └── thesis_announcement.pdf


```

---

## 📘 Documentation Included

This repository contains all documentation required by the thesis committee:

### **1. Full Thesis**

* **`thesis/Thesis_Synthetic_Data.pdf`**
  Complete thesis document, including abstract, theory, experiments, results, and references.

### **2. Thesis Announcement**

* **`thesis/announcement/thesis_announcement.pdf`**

Contains defense time, location, advisor, title, and committee info.

### **3. Project Description**

Should be added if your department requires a separate 1–2 page synopsis.
Place it inside:

```
thesis/project_description.pdf
```

---

## 📊 Datasets Used

### **1. Dry Beans Dataset (Primary Thesis Dataset)**

* **Source:** UCI Machine Learning Repository
* **Link:** [https://archive.ics.uci.edu/dataset/602/dry+bean+dataset](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset)
* **Description:**

  * 13,611 samples
  * 16 continuous features + 1 categorical class label
  * Multi-class classification task
* **Files in this repo:**
  `akde/bean.csv`, `bean-clean.csv`, `bean1.csv`…`bean5.csv`
  `ctgan/bean-clean.csv`
  `bean_kde/bean*.csv`

### **2. Iris Dataset (Auxiliary validation only)**

Used to validate KDE / clustering workflows prior to the Beans dataset.

* **Typical Source:** UCI or scikit-learn
* **Files:** `iris_dataset/iris_data*.csv`, `kde_gen.csv`

---

## 🧠 What Is Code vs What Is Documentation?

### ✔ **Documentation** (for thesis readers)

Located in `thesis/`:

* Thesis PDF
* Thesis LaTeX source
* Announcement PDF & LaTeX
* Project description (if included)
* Any exported figures used in the thesis

### ✔ **Code**

Located in:

* `akde/` → Adaptive KDE implementation
* `ctgan/` → CTGAN training and generation
* `bean_kde/` → Classical KDE baselines
* `iris_dataset/` → Auxiliary experiments
* `AIEN/` → Future work on AIEN / VAE models

Code artifacts include:

* Jupyter notebooks (`*.ipynb`)
* Python scripts (if present)
* Model weight files (`*.pth`, `*.h5`)

### ✔ **Data**

Raw and synthetic datasets:

* Real beans data:
  `bean.csv`, `bean-clean.csv`, `bean1.csv`…`bean5.csv`

* Synthetic AKDE data:
  `syn_bean*.csv`, `syn_bean_merged.csv`

* Synthetic CTGAN data:
  `synthetic_data_1.csv`…`synthetic_data_5.csv`

* Iris data:
  `iris_data*.csv`, `synthetic_iris*.csv`

---

## 🧪 How to Run the Experiments

### 1. Install environment

```bash
conda create -n synexploration python=3.11
conda activate synexploration
pip install numpy pandas matplotlib seaborn scikit-learn scipy sdv jupyter
```

### 2. Start Jupyter Notebook

```bash
jupyter notebook
```

### 3. Run AKDE experiments

Open:

```
akde/test_akde-bean.ipynb
akde/test_result.ipynb
```

### 4. Run CTGAN experiments

Open:

```
ctgan/ctgan_synGenerator.ipynb
ctgan/k-mean_kde-bean_on_syn_ctgan.ipynb
```

### 5. View Baseline KDE and Iris experiments (optional)

Open notebooks in:

```
bean_kde/
iris_dataset/
```

---

## 📚 How to Read the Thesis Using This Repo

1. **Start with the thesis PDF:**
   `thesis/Thesis_Synthetic_Data.pdf`

2. **Refer to the data sources:**
   Dry Beans dataset link (UCI), included CSVs, and Iris dataset.

3. **Review code-backed methodology:**

   * AKDE implementation → `akde/test_akde-bean.ipynb`
   * CTGAN implementation → `ctgan/ctgan_synGenerator.ipynb`

4. **Analyze plots & outputs:**
   Many figures in the thesis are generated by these notebooks.

5. **Explore synthetic datasets:**
   Synthetic CSVs are generated and stored inside each model folder.
