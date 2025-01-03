# Code-for-Minocycline-Influence-On-Protein-Stability-Research-Project

This is the code for the research project that me and my friends did. The code uses OpenMM and PyRoseTTA as dependencies, so make sure that your operating system supports them (along with Python of course).

**Here is credit where credit is due** _(Not for dependencies, just who directly contributed to this project)_**:**
- Ali Zahid: Wrote 95% of the code, helped with Excel graphs, dealt with the statistics, wrote the methods section and anything else really technical
- Owen Zhang: Wrote the introduction for the paper, helped with conceptualization and background information
- Anthony Hur: Team leader, ran the 12 hour (each) simulations and made sure everything went smoothly
- Everyone Above: Helped with conceptualization and writing discussion

## Project Overview

Project Title: Novel Computational Framework: Investigating the Effect of Minocycline on Iba1 and CD163 Biomarkers in the Central Nervous System During Traumatic Brain Injury

Overview:
Traumatic brain injuries (TBI) is one of the leading causes of mortality and long-term disability globally, contributing to over 100,000 deaths and 500,000 permanent disabilities annually. Despite substantial efforts to treat TBI, neuroprotective agents to mitigate brain damage post-injury remain limited. This paper aims to explore the neuroprotective capabilities of Minocycline, a known antibiotic, and its ability to affect microglial activation markers within the brain, having the potential to improve the lives of patients suffering from TBI. During TBI, microglial activation is often chronic. To combat this, we used Molecular Dynamic (MD) simulations and PyRoseTTA to score protein stability, simulating the interactions between Minocycline and proteins involved in microglial activations over 200 nanoseconds in order to see if a controlled reduction of microglia was possible. We tracked changes in protein stability by scoring RoseTTA Energy Units (REU) every 100 picoseconds, and our results showed a significant correlation (p < 0.05) between the presence of Minocycline and protein stability. Our results provide insight into Minocycline's role in treating TBI, showing how Minocycline can lead to a controlled reduction in microglial activation marker activity. These results provide evidence for a correlation between biomarkers and their roles in the human body, providing insight to help patients with TBI. These findings show that Minocycline-controlled prevention of chronic microglial activation is possible, and may help prevent neurotoxic factor release, ultimately reducing inflammation and supporting recovery.

## How to Use

Please note that this code will produce several files such as 2500 pdb files (< 248 KB each), a trajectory.dcd file, .log file, and a .xlsx file.

Download the following files for simulations:

- [Minocycline Force Field]
- [Iba1 without Minocycline]
- [Iba1 with Minocycline]
- [CD163 without Minocycline]
- [CD163 with Minocycline]
- [Code for Negative Control (ONLY WORKS FOR THOSE PROTEINS WITHOUT MINOCYCLINE)]
- [Code for Experimental (FOR WITH MINOCYCLINE)]
- [Excel Template for Collecting Data]

The code is purely coded in Python, check the [Dependencies](#) section to download OpenMM and PyRoseTTA. 

### Running the Code**

Make sure that all the files are in a single folder/directory that you will run the code from. Simply open up the code and edit a handful of set values:

- 'output_file_excel_name': used to change the name of the output Excel File (.xlsx)
- 'protein': Change the name inside the brackets to one of the names of the protein that is stored in the 'Proteins' dictionary
- 'platform': Change the platform name to one of the ones mentioned [here](#), OpenMM has optimization for NVIDIA GPU's, but any GPU is ideal. Take a look at the OpenMM documentation for more information or look online.
- 'simulation_drug.reporters.append(
    DCDReporter('trajectory.dcd', reporting_steps)  # Save every 1000 steps
)': Change the 'trajectory.dcd' argument to another name with the .dcd extension to change the name of the trajectory output file

## Dependencies, Licensing, and Attribution

This repository is licensed under a **BSD 3-Clause License**. See [LICENSE](docs/LICENSE) for details.

### Dependencies

This program uses OpenMM and PyRoseTTA programs to run the molecular dynamics simulations and scoring the protein. 

Here is how to obtain the dependences:

- OpenMM: [Documentation](#http://docs.openmm.org/7.0.0/userguide/application.html)
- PyRoseTTA: [How to Download](#https://www.pyrosetta.org/downloads)

The rest of the packages should be included if you use Conda, if not here are the other modules necessary to run the code.

- time
- sys
- openpyxl

### **Disclaimer**

This project is intended for academic and educational purposes only. Users are responsible for ensuring compliance with all dependencies' licensing terms.

### Acknowledgments

The developers of OpenMM and PyRosetta for providing essential tools for this research.
