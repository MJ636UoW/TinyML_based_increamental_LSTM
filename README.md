# TinyML-based Incremental LSTM for Logic-Layer Anomaly Detection  
### SWaT Training + WADI Validation (PLC-Oriented Deployment)

This repository contains the notebook-based implementation used in my Master’s dissertation.  
The work focuses on detecting **logic-layer anomalies** in industrial water systems using a **lightweight, incremental LSTM model**, designed with **PLC-class feasibility** in mind.

Instead of only detecting abnormal sensor values, this work focuses on **process and logic inconsistencies**, such as:
- sensor–actuator mismatch  
- abnormal control behaviour over time  
- sequence-level deviations that appear normal at individual time steps  

---

## Repository Contents

This repository contains **three Jupyter notebooks**, which should be run in the following order.

### 1️⃣ 01_SWaT_Training_FeatureSelection.ipynb
This notebook prepares the model input using the SWaT dataset.

It performs:
- loading and cleaning SWaT process data  
- preparing the dataset for learning  
- selecting a compact set of meaningful features  
- reducing redundancy to support lightweight execution  

---

### 2️⃣ 02_SWaT_IncrementalLSTM_Experiments.ipynb
This notebook contains the **core model and all SWaT-based experiments**.

It includes:
- construction of the incremental LSTM model  
- training of the baseline configuration  
- execution of multiple controlled experiments (approximately 8–9 variations)  

The experiments analyse the effect of:
- window size  
- chunk size (important for memory behaviour)  
- batch size  
- number of LSTM units  
- decision threshold  

---

### 3️⃣ 03_WADI_Validation_PLC_Deploy.ipynb
This notebook performs **validation using the WADI dataset** and is the one used for **PLC-oriented deployment evaluation**.

Important clarification:
- this notebook is **not used for heavy retraining**
- it is used to **validate the trained model** on a different industrial system  

This notebook reflects a **deployment-style setup**, with attention to:
- lightweight configuration  
- practical window and chunk settings  
- stability and feasibility for PLC-class devices  

---

## Datasets Used

### SWaT Dataset (Training and Experiments)
The SWaT dataset is used for:
- feature selection  
- model training  
- all controlled experiments  

✅ In this repository, SWaT dataset files are included (as you provided).

---

### WADI Dataset (Validation and PLC-Oriented Testing)

✅ **In this repository, the WADI dataset is included in a zipped form** (because the raw dataset is large).  
So, you do **not** need to request it separately if you are using this repo version.

However, I am still maintaining the official WADI reference below, because the dataset originates from that work and should be cited properly.

#### Official WADI Reference Paper
Ahmed, C. M., Palleti, V. R., & Mathur, A. P.  
**WADI: A Water Distribution Testbed for Research in the Design of Secure Cyber Physical Systems**  
Proceedings of the 3rd International Workshop on Cyber-Physical Systems for Smart Water Networks (CySWater), 2017  

ACM Digital Library link:  
https://dl.acm.org/doi/abs/10.1145/3055366.3055375

---

## Extracting the WADI Dataset (IMPORTANT)

Because the dataset is stored in zipped form, please extract it first.

Example:
- Download / clone the repository
- Extract the zip file (Right click → Extract All)

After extraction, you should be able to access the WADI files normally from your local system.

---

## Updating Dataset Paths (IMPORTANT)

Since datasets are stored locally on each system, you must update the dataset path inside each notebook.

Inside the notebooks, you will see variables similar to:

```python
SWAT_PATH = "C:/Users/....../SWaT_dataset.xlsx"
WADI_PATH = "C:/Users/....../WADI_dataset.csv"
