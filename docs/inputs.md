# Inputs

## Sample file
The pipeline also needs a .tsv-file with all sample names called ```samples.tsv``` in the following format:

| sample | `<phenotype>` |
| ------ | ------ |
|   `<sample_name>`    |   `<0 or 1>`    |
|     ...   |     ...   |

!!! note
    Only samples named in the samples file are considered for the pipeline, even if you have more in the ```raw_reads``` folder.

## Config file
All the parameters the pipeline needs are drawn from the config file (```config.yaml```) and need to be configured before the run. Here is an explaination for each parameter in it:

| parameter | description |
| :------------ | :------ |
|   ```run_mode```  |   Choose, if you want the pipeline to be run on every ST group of your data seperately ("per_st") or on all samples at one ("full_run"). The ST groups needs to have at least ```min_samples``` number of samples to be considered.   |
|     ```assemblies```   |     Path to the assembly file.   |
|     ```kmer```   |     Kmer-lenght used to create the unitigs with Cuttlefish.   |
|     ```threads```   |     Number of cores Snakemake should use for a job.  |
|     ```shovill_ram```   |     Amount of RAM Shovill is allowed to allocate.   |
|     ```shovill_depth```   |     Sequencing depth of the Shovill run.   |
|     ```bakta_genus```   |     Optional: Genus of the bacteria your dataset is based on for the GFF-file creation with Bakta.   |
|     ```mi_values```   |     The number of top MI-scored unitigs pairs SpydrPick will return.  |
|     ```maf```   |     Minor allele frequency threshold for SpydrPicks position filtering.   |
|     ```reweighting_threshold```   |    Reweighting threshold Spydrpick uses for population structure correction.    |
|     ```min_samples```   |     Minimum number of samples a ST group needs to have to be considered for a run (only relevant for ```run_mode``` = "per_st")   |
|     ```top_n_unitigs```   |     Number of the unitigs with the highest MI to be considered for epistasis detection with HybridGWAIS.   |
|     ```phenotype```   |     The phenotype examined for this run.   |
|     ```alpha```   |     The alpha used for the Bonferroni correction.   |
|     ```ignore_bonferroni```   |     When true, ignores the Bonferroni correction for the gene mapping and takes the  ```top_n_pairs``` instead. |
|     ```top_n_pairs```   |     Number of pairs with the lowest p-value returned by the epistasis detection to consider for gene mapping (only relevant when ```ignore_bonferroni``` = true).   |
|     ```blast_identity```   |     Sequence identity threshold in percent for a unitig-gene-cluster combination to be accepted as a hit by BLAST+.   |
|     ```blast_coverage```   |    Fraction of the unitigs that has to be covered by the alignment to be accepted as a hit by BLAST+.    |
|     ```blast_evalue```   |     Maximum expected value threshold for a hit to be accepted by BLAST+.  |
|     ```string_taxid```   |     STRING tax identifier of the bacteria your data is based on for network comparison.  |
|     ```string_score_threshold```   |    Confidence score threshold between 0-1000 of two proteins interacting used for network comparison.   |
|     ```biogrid_organism```   |     Name in the BioGRID database of the bacteria your data is based on for network comparison.   |
|     ```network_edge_weight```   |     Edge weight used for the interaction network (choose between "pval", "chisq" or "OR").   |