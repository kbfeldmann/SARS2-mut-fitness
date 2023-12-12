### 🌎 Virus Evolution &nbsp; &nbsp; &nbsp; 🔍 Enriched Mutations &nbsp; &nbsp; &nbsp; 📈 Phylogenetics

The discontinuous evolution of SARS-CoV-2 led to large jumps in genetic differentiation and the emergence of unique variants that can be characterized by one or more phylogenetic clades. Mutations unique to certain phylogenetic clades can experience different directions and degrees of selection which may influence SARS-CoV-2 evolution. The goal of this project was to generate two-clade comparisons for SARS-CoV-2 phylogenetic clades. Using these comparisons, we can estimate the fitness effects of SARS-CoV-2 mutations by comparing the observed mutations to those expected from the mutation rate. 

This project was originally based off the analyses in [Neher (2022)](https://www.biorxiv.org/content/10.1101/2022.08.22.504731v1.full), but aimed to verify the assumption that the synonymous mutation rate was conserved across SARS-CoV-2 clades.

**Research Question:** *How does the ratio of observed to expected mutations compare between SARS-CoV-2 phylogenetic clades?*

![Snakemake](https://github.com/kbfeldmann/SARS2-mut-fitness/assets/47021794/e1666553-82ac-4a81-9943-1dfbee13bf6e)

**Figure 1:** A Snakemake pipeline was used to parallelize (1) calculating q-values using a Fisher’s exact test and false-discovery rate correction and (2) visualizing q-values using volcano plots across the 91 two-clade comparisons. Orange and green boxes indicate that nucleotide and amino acid comparisons for each two-clade comparison were also generated in parallel.

Although mutations experiencing different directions and degrees of selection can be identified using experimental approaches, using a computational pipeline to identify significantly enriched mutations is an effective way to analyze the entire SARS-CoV-2 genome rather than a specific region of a protein (e.g., receptor-binding domain of the spike protein). One interesting result is that significantly enriched synonymous amino acid mutations in the spike protein are near known deletions. However, this result represents a potential caveat with the computationally-derived results – the synonymous mutations may be due to incorrect sequence alignment at the deletion site.

![Deletions](https://github.com/kbfeldmann/SARS2-mut-fitness/assets/47021794/71726267-0e9e-4996-a4d8-f2802539ba9d)

**Figure 2:** Minimum q-values for synonymous amino acid mutations in the spike protein. Mutations not near notable deletions are black. P25P is near L24-, P25- and P26-. V70V is near H69- and V70-. Y145Y is near Y144-. For more information visit https://covariants.org/shared-mutations.

To learn more, check out my poster for graduate-level biologists and computer scientists: [click here]()  
Additionally, visit the [original repository](https://github.com/jbloomlab/SARS2-mut-fitness) to explore this research and related projects in greater depth.

## Parallel Computing

The code generated for this project can be found in the `expected_and_actual_counts_ratio` folder. To calculate q-values (Fisher's exact test and false discovery rate correction) and generate volcano plots, the `scripts` are run in parallel using the `Snakefile`. Further analyses were conducted in the `notebooks`. Below is the directed acyclic graph (DAG) for the `expected_and_actual_counts_ratio/Snakefile`:

![DAG](https://github.com/kbfeldmann/SARS2-mut-fitness/assets/47021794/c2eb3187-80f3-43a8-a1eb-60469407aa7d)
