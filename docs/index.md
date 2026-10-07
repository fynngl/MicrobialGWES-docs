# Documentation of MicrobialGWES
MicrobialGWES is a Snakemake pipeline for detecting epistatic gene-gene interactions in bacterial genomes. It integrates genome assembly, pan-genome construction, LD and population structure correction, pairwise epistasis detection, gene annotation, and network-based validation.

## Contents
- [Usage](usage.md)
    - [Installation](usage.md#installation)
    - [Requirements](usage.md#requirements)
    - [Downloading of external data](usage.md#downloading-of-external-data)
    - [Running the pipeline](usage.md#running-the-pipeline)
- [Pipeline structure and tools](pipeline.md)
    - [Pipeline structure](pipeline.md#pipeline-structure)
    - [Underlying tools](pipeline.md#underlying-tools)
- [Inputs](inputs.md)
    - [Sample file](inputs.md#sample-file)  
    - [Config file](inputs.md#config-file)   
- [Outputs](outputs.md)
- [Example run](example.md)
    - [Parameters](example.md#parameters)
    - [Environment](example.md#environment)
    - [Runtime](example.md#results)
        - [LD and population structure correction](example.md#ld-and-population-structure-correction)
        - [Epistasis detection](example.md#epistasis-detection)
        - [Mapping](example.md#mapping)
        - [Network comparison](example.md#network-comparison)