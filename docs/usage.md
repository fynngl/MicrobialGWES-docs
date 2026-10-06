# Usage

## Installation
The code for MicrobialGWES can be found on [Gitlab](https://git.rz.tu-bs.de/scibiome/theses/studienarbeit/fynn-glaeser).

## Requirements
MicrobialGWES requires different third-party software and packages. Its recommended to run it in a Docker container created from the Dockerfile in the repository, where you can also derive all the nessessary requirements if you do not want to use Docker. An image of such an container can be found on [Dockerhub](https://hub.docker.com/layers/fygl/microbialgwes5/latest/images/sha256:dea6ef5286262a82b98dbee32055f33ddefa2dfaf9275df00d14db5ab4e8b921?uuid=5afac366-b18f-4c61-bebd-c1156bd20445).

## Downloading of external data
The databases for the network comparison, the stringMLST database and the raw reads need to be downloaded before running the pipeline to prevent common download restrictions on servers. Example scrips for downloading the databases are provided in this repository (download_databases.sh and get_mlst_scheme.sh). The raw reads need to be in a folder called ```raw_reads```:
```
raw_reads/
│   ├── <sample_name>_1.fastq.gz
│   ├── <sample_name>_2.fastq.gz
│   ├── ...
```

!!! note
    You can skip this step, if you already have the assemblies of your input data. You then need to create a .txt-file (assembly file) with the path to your assemblies in the following format:
    ```
    /path/to/assembly1.fa
    /path/to/assembly2.fa
    ...
    ```

## Running the pipeline
The pipeline can be run with:
```
snakemake --cores <number of cores for the pipeline to use>
```