# Outputs
The output of ST run is structured in the following directory structure (the output of a full run looks the same, but without the ```ST{st}``` subfolders and the main directory is called ```full_run```):
```
st_runs/K{kmer}/
├── ST{st}/
│   ├── cdbg.spydrpick_couplings.1-based.edges
│   ├── cdbg.spydrpick_couplings.1-based.outliers
│   └── cdbg.unitig_distance_outliers
├── pyseer_unitigs/
│   └── ST{st}_unitigs.pyseer
├── plink/
│   └── ST{st}/
│       └── plink.{bed,bim,fam}
├── hybridgwais/
│   └── ST{st}/
│       ├── results.logreg.scores
│       └── manhattan_plot.pdf
├── annotations/
│   └── ST{st}/
│       ├── annotated_pairs.tsv
│       └── enriched_pairs.tsv
└── network_comparison/
    ├── network_comparison.pdf
    └── summary.tsv
```

- ```cdbg.spydrpick_couplings.1-based.edges``` is the main Spydrpick output and contains the unitigs pairs with its associated MI value.
- ```cdbg.spydrpick_couplings.1-based.outliers``` is file containing all the outlier unitig pairs found by Spydrpick.
- ```cdbg.unitig_distance_outliers``` is the file containing the LD-filtered outliers found by unitig_distance from PanGWES.
- ```ST{st}_unitigs.pyseer``` the final unitigs file in pyseer format, containing either the LD-filtred outliers or the unitigs from the ```top_n_unitigs``` unitig pairs.
- ```plink.{bed,bim,fam}``` are the PLINK files needed for HybridGWAIS, created from the unitigs file.
- ```results.logreg.scores``` is the result file from HybridGWAIS, containing the most promising epistatic interactions.
- ```manhattan_plot.pdf``` is a Manhattan plot of HybridGWAIS's results.
- ```annotated_pairs.tsv``` are the results from HybdridGWAIS mapped to a Panaroo gene cluster.
- ```enriched_pairs.tsv``` is ```annotated_pairs.tsv``` enriched with gene names and functional annotations from Panaroo.
- ```network_comparison.pdf``` is a two-panel figure showing precision-recall and ROC curves for the comparison between HybridGWAIS predictions and known interactions from STRING and BioGRID.
- ```summary.tsv``` is a summary of the results of network comparison.