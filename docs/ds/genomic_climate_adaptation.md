# 🧬 Genomic & Geographic Adaptation to Climate Change  
*A Case Study of Wild Yak and Takin*

---

## 🧭 Project Overview

This interdisciplinary project investigates how **high-altitude mammals like Wild Yak and Takin adapt to climate change**, using a combination of:

- **Species Distribution Modeling (SDM)** with Random Forest  
- **Comparative Genomics** using tools like Mash, InterProScan, and ProteinOrtho

By integrating geographic and genomic data, we aimed to model future habitats under climate scenarios and uncover genes responsible for environmental resilience.

---

## 🎯 Objectives

- Predict habitat suitability shifts under 2050 climate projections (SSP245 & SSP585)
- Identify genomic traits that enable survival in low-oxygen, cold, UV-rich environments
- Recommend conservation strategies based on habitat and genetic insights

---

## 🗂️ Data Sources

| Data Type     | Source                                         |
|---------------|------------------------------------------------|
| Occurrence    | GBIF, iNaturalist, camera trap literature      |
| Climate       | TerraClimate (2009–2024), WorldClim 2050      |
| Elevation     | Google Earth Engine DEM                        |
| Genomes       | NCBI Genome: Wild Yak, Takin, Water Buffalo    |

---

## ⚙️ Methodology

### 🗺️ Species Distribution Modeling (SDM)
- **Algorithm**: Random Forest (AUC: 0.999 for Yak, ~0.95 for Takin)
- **Features**: Precipitation, max/min temperature, elevation
- **Tools**: `xarray`, `rasterio`, `scikit-learn`, `matplotlib`, `numpy`
- **Future Scenarios**: SSP245 (moderate), SSP585 (severe warming)

### 🧬 Genomic Analysis
- **Mash**: Whole-genome similarity (Yak-Buffalo ~97.1%)
- **InterProScan**: Protein domain annotation and GO term enrichment
- **ProteinOrtho**: Ortholog clusters to detect gene gains/losses

---

## 📊 Key Results

### 🌐 SDM Findings
- **Wild Yak**:
  - Habitat loss projected by 2050 (~19% drop under SSP585)
  - Elevational shift upward by ~60m
- **Takin**:
  - Predicted habitat expansion westward
  - Greater ecological tolerance observed

### 🧪 Genomic Insights
| Species      | Key Genetic Adaptations                             |
|--------------|-----------------------------------------------------|
| Wild Yak     | Cytoskeletal, membrane signaling, hypoxia-resilience |
| Takin        | Immune response, sensory expansion, ECM remodeling |
| Water Buffalo| Generalist traits, rich sensory and immune diversity |

> Notable: Yak shows **loss of olfactory domains**, likely due to extreme niche specialization.

---

## 📍 Conservation Impact

- **Refugia** for Wild Yak lie outside existing protected zones
- Genomic traits can inform **breeding programs** and **species-specific corridors**
- Shows need for **climate-genomic integration** in policy and wildlife planning

---

## 🛠️ Tools & Technologies

- Python (scikit-learn, rasterio, pandas, matplotlib)
- InterProScan, ProteinOrtho, Mash
- GBIF API, NCBI, TerraClimate, WorldClim
- WSL/Linux CLI tools, MAFFT, FASTA/GFF formats


---

## 📌 Next Steps

- Link with expression data under hypoxia stress  
- Improve annotation for Wild Yak genes  
- Integrate land-use change for finer SDM forecasting  
- Use ensemble models (MaxEnt, BRT) for robustness



---

## 📂 GitHub Repository 

> [Superstore Profit Analysis on GitHub](https://github.com/fenil264/Superstore_Profit_Analysis)

