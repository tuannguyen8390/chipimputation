# Imputation Workflow h3abionet/chipimputation

[![Build Status](https://travis-ci.org/h3abionet/chipimputation.svg?branch=master)](https://travis-ci.org/h3abionet/chipimputation)
[![Nextflow](https://img.shields.io/badge/nextflow-%E2%89%A50.30.0-brightgreen.svg)](https://www.nextflow.io/)

[![install with bioconda](https://img.shields.io/badge/install%20with-bioconda-brightgreen.svg)](http://bioconda.github.io/)
[![Docker](https://img.shields.io/docker/automated/nfcore/chipimputation.svg)](https://hub.docker.com/r/h3abionet/chipimputation)
![Singularity Container available](
https://img.shields.io/badge/singularity-available-7E4C74.svg)

### Introduction
The pipeline is built using [Nextflow](https://www.nextflow.io), a workflow tool to run tasks across multiple compute infrastructures in a very portable manner. It comes with docker / singularity containers making installation trivial and results highly reproducible.
This  workflow which was developed as part of the H3ABioNet Hackathon held in Pretoria, SA in 2016.
 - We track our open tasks using github's [issues](https://github.com/h3abionet/chipimputation/issues)
 - The 1000ft view is located on [our Trello board](https://trello.com/b/Dp08chq7/stream-d-imputation-and-phasing).


### Documentation
The h3achipimputation pipeline comes with documentation about the pipeline, found in the `docs/` directory:

1. [Installation](docs/installation.md)
2. Pipeline configuration
    * [Local installation](docs/configuration/local.md)
    * [Adding your own system](docs/configuration/adding_your_own.md)
3. [Running the pipeline](docs/usage.md)
4. [Output and how to interpret the results](docs/output.md)
5. [Troubleshooting](docs/troubleshooting.md)

### Setup (native cluster)

#### Headnode
  - [Nextflow](https://www.nextflow.io/) (can be installed as local user)
   - NXF_HOME needs to be set, and must be in the PATH
   - Note that we've experienced problems running Nextflow when NXF_HOME is on an NFS mount.
   - The Nextflow script also needs to be invoked in a non-NFS folder
  - Java 1.8+

#### Compute nodes

- The compute nodes need access to shared storage for input, references, output
- The following commands need to be available in PATH on the compute nodes

  - `impute2` from [IMPUTE2](http://mathgen.stats.ox.ac.uk/impute/impute_v2.html)
  - `plink` from [PLINK 1.9+](https://www.cog-genomics.org/plink2)
  - `vcftools` from [VCFtools](https://vcftools.github.io/index.html)
  - `bcftools`from [bcftools](https://samtools.github.io/bcftools/bcftools.html)
  - `bgzip` from [htslib](http://www.htslib.org)
  - `eagle` from [Eagle](https://data.broadinstitute.org/alkesgroup/Eagle/)
  - `python2.7`

### Getting started

#### Basic test
 1. Clone this repo
 2. Run the "tiny" dataset included
```
nextflow run imputation.nf -c nextflow.test.tiny.config
```
 3. check for results in `outfolder`
```
wc -l output/impute_results/FINAL_VCFS/*
```

#### Larger dataset
 1. Download this slightly larger dataset: [small.tar.bz2](https://goo.gl/cYk51U) and extract into the `samples` folder
 2. Run this "small" dataset with
```
nextflow run imputation.nf -c nextflow.test.small.config
```
 3. check for results in `outfolder`
```
wc -l output/impute_results/FINAL_VCFS/*
```
