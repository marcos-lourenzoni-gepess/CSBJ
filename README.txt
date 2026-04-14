# Data and Analyses – CSBJ Project

This repository contains the **data and analyses** associated with the manuscript submitted to the *Computational and Structural Biotechnology Journal (CSBJ)*.  
The information is organized hierarchically to ensure **reproducibility, traceability, and transparency** of the results.

---

## 📂 General Structure

The main directory is divided into two sections:

- **DM/** – Contains the files and results from Molecular Dynamics (MD) simulations.  
- **Analyses/** – Contains computational and experimental analysis results, including flow cytometry data.

CSBJ/
├── DM/
│ ├── OFA_Wild/
│ │ ├── Minimization/
│ │ ├── Thermalization/
│ │ ├── Production/
│ │
│ ├── scFv_Water/
│ │ ├── Minimization/
│ │ ├── Thermalization/
│ │ ├── Production/
│ │
│ ├── Variants/
│ │ ├── [Variant_Name_1]/
│ │ │ ├── Minimization/
│ │ │ ├── Thermalization/
│ │ │ ├── Production/
│
├── Analyses/
│ ├── Supplementary Data and Manuscript/
│ ├── Other/

---

## 🧬 **Molecular Dynamics (MD)**

The **DM/** folder contains the simulation data for:

- The **OFA wild-type antibody bound to CD20**  
- The **isolated scFv simulated in aqueous solution**  
- The **mutant variants**

Each system follows the same simulation protocol, divided into three main stages:

- **Minimization/** – Energy minimization  
- **Thermalization/** – Heating and equilibration stages  
- **Production/** – Production run (main trajectory)

Each subfolder includes GROMACS input and output files (`.pdb`, `.gro`, `.mdp`, `.top`, `.xvg`, `.log`, `.edr`).  

Local `README.md` files describe simulation parameters and software versions.

> The same simulation protocol was applied to the OFA wild-type, isolated scFv in water, and all mutant variants.

---

## 📊 **Computational and Experimental Analyses**

The **Analyses/** folder compiles all *in silico* and experimental results.  

Subfolder and file names follow the convention:


where `Fig[XX]` corresponds to the figure number in the **main manuscript** or **Supplementary Data**.

### **Molecular_Dynamics/**

Contains post-processing results derived from MD trajectories:

- RMSD and RMSF per residue  
- Intermolecular Interaction Potential (**IIP**) curves  
- Binding free energy (**ΔGbinding**)  
- Per-residue energy decomposition (**ΔG_res**, **ΔΔG_res**)

---

### **Flow_Cytometry/**

Contains experimental flow cytometry data:

- **Raw_data/** – original `.dat` files  
- **Processed/** – cleaned datasets corresponding to figures in the manuscript and supplementary files

---

## ⚙️ **Reproducibility**

All datasets are provided in **machine-readable formats** and can be processed in open computational environments.

The analyses can be reproduced using:

- **GROMACS 2024**  
- **Python 3.10**  
- **PyMOL**  
- Flow cytometry processing tools  

The complete workflow for simulation, processing, and analysis is described in:



following **CSBJ data-sharing recommendations**.

---

## 🧾 **Citation**

> Lourenzoni MR et al.  
> *Revisiting the Ofatumumab Epitope on CD20 through Integrative Molecular Dynamics and Flow Cytometry Analyses.*  
> Computational and Structural Biotechnology Journal (CSBJ).  

(To be updated after acceptance.)

---

## 📞 **Contact**

**Marcos Roberto Lourenzoni**  
Grupo de Engenharia de Proteínas e Soluções para Saúde (**GEPeSS**) – Fiocruz Ceará  
📧 marcos.lourenzoni@fiocruz.br  
📍 Fortaleza – Ceará, Brazil
