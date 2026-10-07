# Example run
Here we will go over an example run, using data from a study by [Moradigaravand et al. 2018](https://doi.org/10.1371/journal.pcbi.1006258) containing 1936 E.coli strains. The phenotype examined was ampicillin resistance.

## Parameters
The config-file parameters used for this run are the following:

| parameter | value |
| :------------ | :------ |
|   ```run_mode```  |   "full"   |
|   ```kmer```  |   127   |
|   ```threads```  |   64   |
|   ```shovill_ram```  |   32   |
|   ```shovill_depth```  |   50   |
|   ```bakta_genus```  |   ""   |
|   ```mi_values```  |   50000000   |
|   ```maf```  |   0.05   |
|   ```reweighting_threshold```  |   0.2   |
|   ```top_n_unitigs```  |   1000   |
|   ```phenotype```  |   "AMP"   |
|   ```alpha```  |   0.05   |
|   ```ignore_bonferroni```  |   true   |
|   ```top_n_pairs```  |   1000   |
|   ```blast_identity```  |   70   |
|   ```blast_coverage```  |  0.8    |
|   ```blast_evalue```  |   1e-10   |
|   ```string_taxid```  |   511145   |
|   ```string_score_threshold```  |   400   |
|   ```biogrid_organism```  |   "Escherichia_coli_K12_W3110"   |
|   ```network_edge_weight```  |   "pval"   |

The species used for the MLST scheme was "Escherichia coli#1". Change the thread and RAM parameters according to your system.

## Environment
Due to the specifications on the server the test was conducted on, the Dockerimage was converted to ```.sif``` on a different system, copied to the server and run with Singularity. Then the pipeline was started within the container with the command from the [Running the pipeline chapter](usage.md#running-the-pipeline).

## Runtime
The total runtime was about 15 days, with the assembly process taking the most time. If you already have assemblies, it is recommended that you skip this step and use your assemblies instead.

| pipeline step | time |
| :------------ | :------ |
|   assembly  |   ca. 10 days   |
|   gene-cluster creation  |   ca. 2 days   |
|   PanGWES  |   ca. 2 days   |
|   epistasis detection, mapping, network comparison  |   ca. 1 days   |

## Results

### LD and population structure correction
Spydrpick did not find any outliers, therefore the top 1000 unitigs with the highest MI were used for the rest of the pipeline.

### Epistasis detection
HybridGWAIS found under the top 1000 most relevant interactions 14 Bonferroni-corrected significant interactions. The following Manhatten plot is the visualization of the results:

![Mahatten plot results](img/manhattan_plot.pdf)

### Mapping
Out of the 14 significant interactions with p-values between around 4.132e−05 and around 2.115e−06,
10 included unmapped unitigs with the identifier u51, u52 and u366. u51 and u52 interacted with an
unnamed gene-cluster representing the protein glutamate decarboxylase, while u366 interacted with
the hypothetical protein Aec71. In the other four cases, glutamate decarboxylase interacted with the
characterized protein yjdJ. All of the interactions have an OR in range of around 1.73 to around 3.41,
so samples with those interactions have higher odds of ampicillin resistance.

### Network comparison
Neither String nor BioGRID had found interactions between those genes, therefore not
network comparison was possible.