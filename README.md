# Computing Interaction Fingerprints for Molecular docking with CMDock
This work was conducted withint [Strasbourg Summer School in Chemoinformatics – 2024](https://infochim.chimie.unistra.fr/-Strasbourg-Summer-School-in-Chemoinformatics-2024-.html)
## Introduction
Protein–ligand interaction fingerprints (IFPs) are binary 1D representations of the 3D structure of protein–ligand complexes encoding the presence or absence of specific interactions between the binding pocket amino acids and the ligand. So we can use IFPs for analyzing a vast amount of potential drag molecules like Prioritizing Virtual Screening with Interpretable Interaction Fingerprints and so on. 

We present a full pipeline for docking and calculating interaction fingerprints. We conducted molecular docking for 102 pairs of protein-ligand from the DUD-E1 (Directory of Useful Decoys, Enhanced) using CMDock tool. DUD-E is a database of protein and ligand to use for docking with the addition of decoys. We used 3 different libraries for calculation of IFPs :
 	- ProLIF: A library for generating interaction fingerprints from protein-ligand complexes.
 	- fingeRNAt: A tool that focuses on RNA-ligand interactions but can be adapted for protein-ligand interactions.
 	- MD-IFP: A library designed to generate fingerprints from molecular dynamics simulations.
Obtaining results
As an input we used three different files with sdf and prm extensions. As an output we got sdf files with the conformation of the ligand afterbinding. We used the OS python library for incorporating the MD tool inside the python notebook for easier calculations. We ran the loop over all the dataset’s folders to conduct MD.

All three libraries for fingerprint calculations accept only pdb format files as an input, so we used OpenBabel library for converting mol2 and sdf files to pbd files for all the datasets.
Results

We calculated all the fingerprints using the PROLIFE and MD-IFP libraries for all 102 protein ligand pairs. Interaction fingerprints of ACE receptor with a ligand were calculated using fingeRNAt with one ligand. 

Fingerprints for ACE dataset were compared. We found that MD-IFP library gives absolutely different ligand-protein interactions for this dataset compared to the other two libraries. PROLIFE and fingeRNAt shows similar results: only four binding sites were different for this two libraries: TRP295, HIS291, ARG458, ASN26 (Figure 1.) 

We also found out that there were errors for some of the ligands during computation of the IF using PROLIFE libraries. In most of the cases ArgumentError arised, because of the explicit valence for nitrogen atom (ADA, FA7 datasets) or for oxygen atom (DEF). There is one error with the inability to kekulize the BRAF dataset.

Computational code for molecular dynamics and fingerprint calculations using PROLIFE library presenter via link: https://github.com/AnastasiyaKrokhina/Hackathon2024
 
## Discussion

The combination of molecular docking with interaction fingerprints allows for a detailed analysis of protein-ligand interactions. By using multiple libraries for IFP calculation, we ensured a comprehensive assessment of the binding modes and interactions. This approach facilitated the prioritization of virtual screening results and provided structural hypotheses for lead optimization.

## Conclusion

This report presents a full pipeline for molecular docking and interaction fingerprint calculation, demonstrating the use of CMDock for docking and three libraries (ProLIF, fingeRNAt, MD-IFP) for IFP calculation. The analysis of 102 protein-ligand pairs from the DUD-E database highlighted the utility of IFPs in prioritizing virtual screening and optimizing drug leads.

## References

1- DUD-E: Mysinger MM, Carchia M, Irwin JJ, Shoichet BK J. Med. Chem., 2012, Jul 5. doi https://doi.org/10.1021/jm300687e .

2- CMDock Tool Documentation

CMDock :
Lešnik, S., Jukič, M., Bren, U. (2023) Mechanistic Insights of Polyphenolic Compounds from Rosemary Bound to Their Protein Targets Obtained by Molecular Dynamics Simulations and Free-Energy Calculations. Foods, 12, 408. https://doi.org/10.3390/foods12020408

Bahun, M., Jukić, M., Oblak, D., Kranjc, L., Bajc, G., Butala, M., ... & Ulrih, N. P. (2021) Inhibition of the SARS-CoV-2 3CLpro main protease by plant polyphenols. Food Chemistry, 131594. doi.org/10.1016/j.foodchem.2021.131594

Jukič, M., Škrlj, B., Tomšič, G., Pleško, S., Podlipnik Č., Bren, U. (2021) Prioritisation of Compounds for 3CLpro Inhibitor Development on SARS-CoV-2 Variants. Molecules 26(10): 3003. doi.org/10.3390/molecules26103003

Ruiz-Carmona, S., Alvarez-Garcia, D., Foloppe, N., Garmendia-Doval, A. B., Juhos S., et al. (2014) rDock: A Fast, Versatile and Open Source Program for Docking Ligands to Proteins and Nucleic Acids. PLoS Comput Biol 10(4): e1003571. doi:10.1371/journal.pcbi.1003571
Morley, S. D. and Afshar, M. (2004) Validation of an empirical RNA-ligand scoring function for fast flexible docking using RiboDock®. J Comput Aided Mol Des, 18: 189--208. doi:10.1023/B:JCAM.0000035199.48747.1e

3- ProLIF : Bouysset, C., Fiorucci, S. ProLIF: a library to encode molecular interactions as fingerprints. J Cheminform 13, 72 (2021). https://doi.org/10.1186/s13321-021-00548-6 

4- fingeRNAt - a novel tool for high-throughput analysis of nucleic acid-ligand interactions
Natalia A. Szulc, Zuzanna Mackiewicz, Janusz M. Bujnicki, Filip Stefaniak
PLOS Computational Biology doi: https://doi.org/10.1371/journal.pcbi.1009783 

5- MD-IFP : D. B. Kokh, B. Doser, S. Richter, F. Ormersbach, X. Cheng , R.C. Wade "A Workflow for Exploring Ligand Dissociation from a Macromolecule: Efficient Random Acceleration Molecular Dynamics Simulation and Interaction Fingerprints Analysis of Ligand Trajectories" J. Chem Phys.(2020) 158 125102 doi: https://doi.org/10.1063/5.0019088.
