# Code-for-Minocycline-Influence-On-Protein-Stability-Research-Project

This is the code for the research project that me (Ali Zahid), Owen Zhang, and Anthony Hur did. The code uses OpenMM and PyRoseTTA as dependencies, so make sure that your operating system supports them (along with Python of course).

**Acknowledgments** 

A thank you to the developers of OpenMM and PyRoseTTA for providing the essential tools for this research.

OpenMM Citation: Eastman, P., Galvelis, R., Peláez, R. P., Abreu, C. R. A., Farr, S. E., Gallicchio, E., Gorenko, A., Henry, M. M., Hu, F., Huang, J., Krämer, A., Michel, J., Mitchell, J. A., Pande, V. S., Rodrigues, J. PGLM., Rodriguez-Guerra, J., Simmonett, A. C., Singh, S., Swails, J., ... Markland, T. E. (2023). OpenMM 8: Molecular Dynamics Simulation with Machine Learning Potentials. Journal of Physical Chemistry B, 128(1), 109-116. Advance online publication. https://doi.org/10.1021/acs.jpcb.3c06662 

PyRoseTTA Citation: Chaudhury, S., Lyskov, S., & Gray, J. J. (2010). PyRosetta: A script-based interface for
implementing molecular modeling algorithms using Rosetta. Bioinformatics, 26(5), 689–691. https://doi.org/10.1093/bioinformatics/btq007

## Project Overview

Project Title: Novel Computational Framework: Investigating the Effect of Minocycline on Iba1 and CD163 Biomarkers in the Central Nervous System During Traumatic Brain Injury

Overview:
Traumatic brain injuries (TBI) is one of the leading causes of mortality and long-term disability globally, contributing to over 100,000 deaths and 500,000 permanent disabilities annually. Despite substantial efforts to treat TBI, neuroprotective agents to mitigate brain damage post-injury remain limited. This paper aims to explore the neuroprotective capabilities of Minocycline, a known antibiotic, and its ability to affect microglial activation markers within the brain, having the potential to improve the lives of patients suffering from TBI. During TBI, microglial activation is often chronic. To combat this, we used Molecular Dynamic (MD) simulations and PyRoseTTA to score protein stability, simulating the interactions between Minocycline and proteins involved in microglial activations over 200 nanoseconds in order to see if a controlled reduction of microglia was possible. We tracked changes in protein stability by scoring RoseTTA Energy Units (REU) every 100 picoseconds, and our results showed a significant correlation (p < 0.05) between the presence of Minocycline and protein stability. Our results provide insight into Minocycline's role in treating TBI, showing how Minocycline can lead to a controlled reduction in microglial activation marker activity. These results provide evidence for a correlation between biomarkers and their roles in the human body, providing insight to help patients with TBI. These findings show that Minocycline-controlled prevention of chronic microglial activation is possible, and may help prevent neurotoxic factor release, ultimately reducing inflammation and supporting recovery.

Simulation Details:

- Simulation Type: NVT (Constant # of Moles, Volume, and Temperature)
- Simulation Length: 200 Nanoseconds
- Equilibriation Length: 2 Nanoseconds
- Step Size: 0.002 Picoseconds
- Time Between "Snapshots": 0.1 Nanoseconds
- Integrator: Langevin Middle Integrator
- Temperature: 312K
- Friction: 1/Picosecond
- Force Fields: 'protein.ff14SB.xml', 'implicit/obc1.xml', ('Minocycline_FF.xml' for experimental)
- Solvent Type: Implicit
- Nonbonded Method: CutoffNonPeriodic 
- Nonbonded Cutoff: 1 Nanometer,
- Constraints: HBonds

If any of the simulation details look smaller than they should, it's because we didn't have the resources to run the simulation for any longer, as with an RTX 4060ti and Ryzen 5 7600x it still took 12 hours to run one simulation for one protein. We have 4 simulations to run for 1 complete set of data, and we don't have access to any fancy computers. So this was the best we could do with the resources we had.

## How to Use

Please note that this code will produce several files such as 2000 pdb files (< 248 KB each), a trajectory.dcd file, .log file, and a .xlsx file with all of the data.

Download the following files for simulations:

- [Minocycline Force Field](docs/Minocycline_FF.xml)
- [Iba1 without Minocycline](docs/PDB-Files/2d58_control.pdb)
- [Iba1 with Minocycline](docs/PDB-Files/2d58_minocycline.pdb)
- [CD163 without Minocycline](docs/PDB-Files/6k0o_control.pdb)
- [CD163 with Minocycline](docs/PDB-Files/6k0o_minocycline.pdb)
- [Code for Negative Control (ONLY WORKS FOR THOSE PROTEINS WITHOUT MINOCYCLINE)](docs/Experimental.py)
- [Code for Experimental (FOR WITH MINOCYCLINE)](docs/Control.py)
- [Excel Template for Collecting Data](docs/Template-For-DATA.xlsx)

The code is purely coded in Python, with the exception of OpenMM and PyRoseTTA. They have Python APIs which were used in this code, check the [Dependencies](#dependencies) section to download OpenMM and PyRoseTTA. 

### Running the Code

Make sure that all the files are in a single folder/directory that you will run the code from. Simply open up the code and edit a handful of set values:

- `output_file_excel_name`: Used to change the name of the output Excel File (.xlsx); ***Do NOT add the file extenstion, that is added during the code***
- `protein_choice`: Change the name inside the brackets to one of the names of the protein that is stored in the `proteins` dictionary
- `platform`: Change the platform name to one of the ones mentioned [here](#http://docs.openmm.org/latest/userguide/library/04_platform_specifics.html), OpenMM has optimization for NVIDIA GPU's, but any GPU is ideal. Take a look at the [OpenMM documentation](#http://docs.openmm.org/latest/userguide/) for more information or look online.
- `platformProperties`: Specify things that the simulation should run on, its dependent on what you put for `platform`; take a look at the [OpenMM Documentation on Platforms](#http://docs.openmm.org/latest/userguide/library/04_platform_specifics.html) for more information 
- `trajectory_name`: Change the name of the output trajectory file; ***Do NOT add the file extenstion, that is added during the code***

For help with some of the OpenMM things like `platform` and `platformProperties`, take a look at [OpenMM Setup](#https://github.com/openmm/openmm-setup) and go through with it and it will generate code for OpenMM simulations. There you can specify platform related settings and copy them to the code here. This was extremely useful when making the simulations and even the developers recommend using it.
## Dependencies, Licensing, and Attribution

This repository is licensed under a **BSD 3-Clause License**. See LICENSE for details.

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

Once again, thank you to the developers of OpenMM and PyRoseTTA for providing the necessary software for this academic project. All softwares were used with an academic license and with the intent to produce an application-based research project with them.


