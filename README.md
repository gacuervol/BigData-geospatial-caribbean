# 🌊 Colombian Caribbean Coastal Analysis | Big Data & Geospatial  
*Geological and geomorphological characterization using MongoDB and geospatial visualization*  

![Python](https://img.shields.io/badge/Python-3.7+-blue?logo=python) ![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-green?logo=mongodb) ![PyMongo](https://img.shields.io/badge/PyMongo-3.11-red) ![Plotly](https://img.shields.io/badge/Plotly-5.0+-lightblue)

## 📌 Project Overview  
**Objective**: Characterize the Colombian Caribbean coast through:  
- **Big Data Processing**: MongoDB document-based storage  
- **Geospatial Analysis**: Coastal typology and sediment facies mapping  
- **Statistical Insights**: MapReduce aggregation pipelines  

**Key Findings**:  
- Identified **32.4% lacustrine deposits** as dominant coastal sediment type  
- Discovered **18% mangrove swamps** as primary geomorphological unit  
- Revealed **34.8% lithoclastic mud** as predominant sediment facies  

## 🛠️ Technical Stack  
```python
import pymongo  # MongoDB interaction
from bson import Code  # MapReduce operations
import plotly.express as px  # Interactive geospatial visualizations
import pandas as pd  # Data analysis
```

## 📊 Key Visualizations  
### 1. Coastal Lithology Distribution  
![Lithology Plot](figures/coastal_lithology.png)  
*Deposit types showing lacustrine (32.4%) and marine (14.4%) dominance*

### 2. Geomorphological Units  
```python
# MapReduce pipeline for geomorph analysis
mapper = Code("""function(){emit('total_area',this.properties.Shape_Area)}""")
reducer = Code("""function(k,v){return Array.sum(v)}""")
db.Coast_geomrf.map_reduce(mapper, reducer, 'geomorf_results')
```
![Geomorph Map](figures/geomorph_units.png)  
*Pantano de manglar (18%) and Colinas y montañas (16.9%) as dominant units*

### 3. Sediment Facies Classification  
![Facies Chart](figures/sediment_facies.png)  
*Lithoclastic mud dominates proximal platform (34.8%)*

## 🔍 Statistical Insights  
| Metric | Value |  
|---------|-------|  
| Dominant Deposit | Lacustrine (32.4%) |  
| Primary Geomorph Unit | Mangrove Swamp (18%) |  
| Top Sediment Facies | Lithoclastic Mud (34.8%) |  

## 📂 Repository Structure  
```text
/Data
├── raw/                  # Original JSON datasets
│   ├── coastal_types.json
│   ├── geomorphology.json
│   └── sediment_facies.json
/Notebooks
├── 1_Data_Acquisition.ipynb
├── 2_MongoDB_Integration.ipynb  # Main workflow
/scripts
├── geospatial_utils.py   # Visualization functions
/figures
├── coastal_lithology.png             
├── geomorph_units.png    # Output visualizations
└── sediment_facies.png
```

## 🚀 How to Use  
### 1. Clone repository:  
```bash
git clone https://github.com/gacuervol/caribbean-coastal-analysis.git
```  

### 2. Start MongoDB service:  
```bash
sudo service mongod start
```  

### 3. Run analysis:  
```bash
jupyter notebook Notebooks/2_MongoDB_Integration.ipynb
```  

## 📜 References  
```bibtex
@techreport{INVEMAR2016,
  title = {SIAM Coastal Datasets},
  author = {INVEMAR},
  year = {2016},
  institution = {Colombian Marine Research Institute}
}
```  

## 🔗 Connect  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Giovanny_Cuervo-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/giovanny-alejandro-cuervo-londo%C3%B1o-b446ab23b/)  
[![ResearchGate](https://img.shields.io/badge/ResearchGate-00CCBB?style=for-the-badge&logo=researchgate)](https://www.researchgate.net/profile/Giovanny-Cuervo-Londono)  
[![Email](https://img.shields.io/badge/Email-giovanny.cuervo101%40alu.ulpgc.es-D14836?style=for-the-badge&logo=gmail)](mailto:giovanny.cuervo101@alu.ulpgc.es)  

> 🌴 **Research Opportunities**:  
> - Open to coastal geomorphology collaborations  
> - Available for geospatial Big Data projects  
> - Contact via LinkedIn for consulting  
