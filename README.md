# MD-simulation-of-post-translated-protein
# Project: Molecular Dynamics Simulation of Mucin-7 Glycosylation for Xerostomia Study

## Overview

This project investigates the conformational and stability changes induced by Post-Translational Modifications (PTMs), specifically O-linked glycosylation, on the human salivary protein Mucin-7 (MUC7). The primary goal is to determine which structural form (fully glycosylated or partially glycosylated) exhibits the most favorable properties (stability, compactness, hydration) for salivary film formation under conditions relevant to Xerostomia (dry mouth).


## Data and Source Structures


| **Target Protein** | Human Mucin-7 (MUC7) | AlphaFold prediction retrieved from **UniProt**. |
| **UniProt ID** | **Q8TAX7** | UniProt accession ID for the MUC7 protein. |
| **Initial Structure** | `Q8TAX7_alphafold.pdb` | The initial **unglycosylated** structure used as the starting point. |


## Computational Methodology

#### 1. Post-Translational Modification (PTM)

The initial AlphaFold structure was modified using **CHARMM-GUI** to generate two simulation systems:

1.  **System 1: Fully Glycosylated**: Addition of **O-linked glycans** to all potential Serine/Threonine residues and N-linked glycans to arginines at respective positions.
2.  **System 2: Partially Glycosylated**: Addition of **O-linked glycans** to a defined, critical subset of Serine/Threonine residues and all the N-linked glycans to arginines.

#### 2. System Setup and Force Field

* **Tool:** **CHARMM-GUI**
* **Force Field:** **CHARMM36m**
* **Solvent:** **TIP3P** water model.
* **Ions:** Neutralized system with counter-ions (Na+ and Cl-) at physiological concentration.
* **Box:** Rectangular periodic boundary conditions.

#### 3. Molecular Dynamics (MD) Simulation Protocol

All simulations were performed using the **GROMACS** MD package.

* **Energy Minimization (EM):** Steepest Descent until a maximum force 1000 kJ/mol/nm was achieved.
* **Equilibration:**
    * **NVT:** 1000 ps using the V-rescale thermostat.
* **Production Run:** A final 50 ns simulation was conducted for each system with a 2 fs time step.


### Key Analysis and Anticipated Findings

The analysis focuses on comparing the two MUC7 systems to identify structural differences relevant to salivary function.

#### Metrics
* **Stability:** **Root-Mean-Square Deviation (RMSD)** and **Root-Mean-Square Fluctuations (RMSF)**.
* **Conformation/Size:** **Radius of Gyration (Rg)**.
* **Interaction:** Intra-molecular and protein-solvent **Hydrogen Bond Analysis**.
* **Water Dynamics:** Analysis of water molecules surrounding the protein.

#### Result Hypothesis
The results will indicate which degree of glycosylation (full, partial) provides the **optimal balance of rigidity and hydration** required for MUC7 to effectively form a protective, lubricating layer on the oral mucosa, thereby informing therapeutic strategies for Xerostomia.


### File Structure

* `input_files/`: Contains the files prepared by the CHARMM-GUI server.
* `mdp_files/`: Need to modify the files given by the CHARMM-GUI server (step1_minimization.mdp, step2_equilibration.mdp, step3_production.mdp).
* `trajectories/`: Output trajectories (`.xtc`) and log files (`.log`) from the production runs.
* `analysis_data/`: Result files from GROMACS analysis tools (e.g., RMSD plots, Rg data).
  
### Script file
* `MD_codes.txt/`: Contains the codes of the simulation.
