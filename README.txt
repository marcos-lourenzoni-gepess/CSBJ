# Data and Analyses – JCIM Project

This repository contains the **data and analyses** associated with the manuscript submitted to the *Journal of Chemical Information and Modeling (JCIM)*.  
The information is organized hierarchically to ensure **reproducibility, traceability, and transparency** of the results.

---

## 📂 General Structure

The main directory is divided into two sections:

- **DM/** – Contains the files and results from Molecular Dynamics (MD) simulations.  
- **Analyses/** – Contains computational and experimental analysis results, including flow cytometry data.

JCIM/
├── DM/
│ ├── OFA_Wild/
│ │ ├── Minimization/
│ │ ├── Thermalization/
│ │ ├── Production/
│ │ 
│ ├── Variants/
│ │ ├── [Variant_Name_1]/
│ │ │ ├── Minimization/
│ │ │ ├── Thermalization/
│ │ │ ├── Production/
├── Analyses/
│ ├── Supplementary Data and Manuscript/
│ ├── Other

---

##  **Molecular Dynamics (MD)**

The **DM/** folder contains the simulation data for the **OFA wild-type antibody** and its **variants**.  
Each system follows the same simulation protocol, divided into three main stages:

- **Minimization/** – Energy minimization.  
- **Thermalization/** – Heating and equilibration stages.  
- **Production/** – Production run (main trajectory).

Each subfolder includes GROMACS input and output files (`.pdb`, `.gro`, `.mdp`, `.top`, `.xvg`, `.log`, `.edr`).  
Local `README.md` files describe the simulation parameters and software versions.  
> The same protocol was applied to both the OFA wild-type and all variants.

---

## 📊 **Computational and Experimental Analyses**

The **Analyses/** folder compiles all *in silico* and experimental results.  
Subfolder and file names follow the convention:

> `[AnalysisType]_[System]_Fig[XX]`

where `Fig[XX]` corresponds to the figure number in the **main manuscript** or **Supplementary Data**.

### **Molecular_Dynamics/**
Contains post-processing results derived from MD trajectories:
- RMSD and RMSF per residue;  
- Curves of **Intermolecular Interaction Potential (IIP)**;  
- DGbinding.DG_res DDG_res


### **Flow_Cytometry/**
Contains experimental flow cytometry data:
- **Raw_data/** – original `.dat`   
- **Processed/** – cleaned data corresponding to figures in the manuscript and supplementary files.

---

## ⚙️ **Reproducibility**

All datasets are in **machine-readable** formats (`.dat`, ) and can be processed in open environments.  
The analyses can be reproduced with:

- **GROMACS **  
- **Python 3.10**  
- **PyMOL + APBS Plugin**  
- ** flow cytometry

The complete workflow for simulation, processing, and analysis is described in `Data_and_Software_Availability.txt`, following JCIM data-sharing guidelines.

---

## 🧾 **Citation**

> *[Manuscript Title]*  
> *Journal of Chemical Information and Modeling (JCIM)*, [Year], [Volume], [Pages].

---

## 📞 **Contact**

**Marcos Roberto Lourenzoni**  
Grupo de Engenharia de Proteínas e Soluções para Saúde (**GEPeSS**) – Fiocruz Ceará  
📧 marcos.lourenzoni@fiocruz.br  
📍 Fortaleza – Ceará, Brazil
