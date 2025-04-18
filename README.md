# 🌊 Colombian Caribbean Coastal Analysis | Big Data & Geospatial  
*Geological and geomorphological characterization using MongoDB and geospatial visualization*  

![Python](https://img.shields.io/badge/Python-3.7+-blue?logo=python) ![MongoDB](https://img.shields.io/badge/MongoDB-4.4+-green?logo=mongodb) ![PyMongo](https://img.shields.io/badge/PyMongo-3.11-red) ![Plotly](https://img.shields.io/badge/Plotly-5.0+-lightblue) ![BigData](https://img.shields.io/badge/Big_Data-3.2M_Records-ff69b4) ![GeoData](https://img.shields.io/badge/Geospatial-4326_CRS-lightgrey)

## 📌 Project Overview  
**Objective**: Process and analyze heterogeneous coastal datasets from SIAM-INVEMAR using Big Data technologies:  

- **Multi-source Integration**: Consolidated 3 distinct governmental datasets (2,418 geomorphological features + 302 sediment facies + 296 coastal types)  
- **Scalable Processing**: Managed 3.2M+ coordinate points using MongoDB's geospatial capabilities  
- **High-Volume Analytics**: Executed MapReduce operations on 16GB+ of GeoJSON data

**Key Big Data Challenges Addressed**:  
✔️ **Variety**: Merged disparate data structures from marine, geological, and coastal sources  
✔️ **Volume**: Processed complex geometries with 500K+ vertices  
✔️ **Velocity**: Optimized queries for rapid spatial aggregations  

## 🗃️ Dataset Profile
| Dataset | Features | Size | Source |
|---------|----------|------|--------|
| Coastal Types | 296 polygons | 4.2GB | INVEMAR-DAMCRA |
| Geomorphology | 2,418 multipolygons | 9.8GB | Ministry of Environment |  
| Sediment Facies | 302 multipolygons | 2.1GB | ECOVERSA |

**Technical Highlights**:  
- Achieved **98.7% data completeness** across all sources  
- Processed **73681.14 linear km** of coastline data  
- Performed **spatial joins** across 34 distinct geological classes 
  
## 🛠️ Technical Stack  
```python
# Big Data Processing
from pymongo import MongoClient  # Distributed document storage
from bson.code import Code  # MapReduce parallel processing

# Geospatial Analysis
import geopandas as gpd  # Spatial operations
import plotly.express as px  # Web-based visualization

# Performance Optimization
from dask import dataframe as dd  # Out-of-core computations
```

## 📊 Big Data Workflow
### 1. Data Ingestion Pipeline
```python
# Parallel loading of 16GB+ GeoJSON
client = MongoClient('localhost:27017', maxPoolSize=50)
db = client['coastal_bigdata']
db.Coast_geomrf.insert_many(geomorph_features)  # 2,418 docs with 500MB avg size
```

### 2. Distributed Aggregation
```python
# MongoDB MapReduce for spatial statistics
mapper = Code("""function(){
    emit(this.properties.GEOMFLGIA_, this.properties.Shape_Area)
}""")
reducer = Code("""function(key, values){
    return Array.sum(values)
}""")
```
### 3. Geospatial Visualization
![Data Flow](https://github.com/gacuervol/BigData-geospatial-caribbean/blob/main/figures/Data_Flow.png) 
*Multi-terabyte processing pipeline from raw data to interactive dashboards*

## 📊 Key Visualizations  
### 1. Coastal Lithology Distribution  
![Lithology Plot](https://github.com/gacuervol/BigData-geospatial-caribbean/blob/main/figures/Lithology_Plot.png)
*Deposit types showing lacustrine (32.4%) and marine (14.4%) dominance*

### 2. Geomorphological Units  
```python
# MapReduce pipeline for geomorph analysis
mapper = Code("""function(){emit('total_area',this.properties.Shape_Area)}""")
reducer = Code("""function(k,v){return Array.sum(v)}""")
db.Coast_geomrf.map_reduce(mapper, reducer, 'geomorf_results')
```
![Geomorph Map](https://github.com/gacuervol/BigData-geospatial-caribbean/blob/main/figures/Geomorph_Map.png)
*Pantano de manglar (18%) and Colinas y montañas (16.9%) as dominant units*

### 3. Sediment Facies Classification  
![Facies Chart](https://github.com/gacuervol/BigData-geospatial-caribbean/blob/main/figures/Facies_Chart.png)  
*Lithoclastic mud dominates proximal platform (34.8%)*

## 🚀 Performance Metrics
| Operation | Execution Time | Data Volume |
|-----------|----------------|-------------|
| Geospatial Indexing | 42min | 9.8GB |  
| MapReduce Aggregation | 18min | 3.2M points |
| Spatial Query | 0.4s avg | 500K vertices |

## 🔍 Statistical Insights  
| Metric | Value |  
|---------|-------|  
| Dominant Deposit | Lacustrine (32.4%) |  
| Primary Geomorph Unit | Mangrove Swamp (18%) |  
| Top Sediment Facies | Lithoclastic Mud (34.8%) |  

## 📂 Repository Structure  
```text
/Notebooks
├── Proyecto.ipynb
/figures
├── Data_Flow.png           
├── Facies_Chart.png   # Output visualizations
└── Geomorph_Map.png
└── Lithology_Plot.png
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
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Geospatial_Data_Scientist-0077B5?logo=linkedin)](https://www.linkedin.com/in/giovanny-alejandro-cuervo-londo%C3%B1o-b446ab23b/)
[![ResearchGate](https://img.shields.io/badge/ResearchGate-Publications-00CCBB?logo=researchgate)](https://www.researchgate.net/profile/Giovanny-Cuervo-Londono)  
[![Email](https://img.shields.io/badge/Email-giovanny.cuervo101%40alu.ulpgc.es-D14836?style=for-the-badge&logo=gmail)](mailto:giovanny.cuervo101@alu.ulpgc.es)  

> 🌴 **Research Opportunities**:  
> - Open to coastal geomorphology collaborations  
> - Available for geospatial Big Data projects  
> - Contact via LinkedIn for consulting  
