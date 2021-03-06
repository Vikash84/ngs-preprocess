# ngs-preprocess pipeline

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3451405.svg)](https://doi.org/10.5281/zenodo.3451405) ![](https://img.shields.io/github/v/release/fmalmeida/ngs-preprocess) [![Build Status](https://travis-ci.com/fmalmeida/ngs-preprocess.svg?branch=master)](https://travis-ci.com/fmalmeida/ngs-preprocess) ![](https://img.shields.io/docker/cloud/build/fmalmeida/ngs-preprocess) [![Documentation Status](https://readthedocs.org/projects/ngs-preprocess/badge/?version=latest)](https://ngs-preprocess.readthedocs.io/en/latest/?badge=latest) ![](https://img.shields.io/badge/Nextflow-v20.07-yellowgreen)


ngs-preprocess is an easy to use nextflow docker-based pipeline that uses state-of-the-art software for pre-procesing ngs reads of Illumina, Pacbio and Oxford Nanopore Technologies and has only two dependencies: [Docker](https://www.docker.com/) and [Nextflow](https://github.com/nextflow-io/nextflow). It wraps up the following software:

* [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
* [TrimGalore](https://github.com/FelixKrueger/TrimGalore)
* [FLASH](https://ccb.jhu.edu/software/FLASH/)
* [Lighter](https://github.com/mourisl/Lighter)
* [Porechop](https://github.com/rrwick/Porechop)
* [pycoQC](https://github.com/a-slide/pycoQC)
* [bam2fastx](https://github.com/PacificBiosciences/bam2fastx)
* [bax2bam](https://github.com/PacificBiosciences/bax2bam)
* [lima](https://github.com/PacificBiosciences/barcoding)
* [pacbio ccs](https://ccs.how/)
* [NanoPack](https://github.com/wdecoster/nanopack).

## Table of contents

* [Requirements](https://github.com/fmalmeida/ngs-preprocess#requirements)
* [Quickstart](https://github.com/fmalmeida/ngs-preprocess#quickstart)
* [Documentation](https://github.com/fmalmeida/ngs-preprocess#documentation)
  * [Full usage](https://github.com/fmalmeida/ngs-preprocess#usage)
  * [Command line examples](https://github.com/fmalmeida/ngs-preprocess#command-line-usage-examples)
  * [Configuration File](https://github.com/fmalmeida/ngs-preprocess#using-the-configuration-file)
  * [Interactive and graphical execution](https://github.com/fmalmeida/ngs-preprocess#interactive-graphical-configuration-and-execution)

## Requirements

* Unix-like operating system (Linux, macOS, etc)
* Nextflow (version 20.01 or higher)
* Java 8
* Docker
  * Image: `fmalmeida/ngs-preprocess`

## Quickstart

1. If you don't have it already install Docker in your computer. Read more [here](https://docs.docker.com/).
    * You can give this [in-house script](https://github.com/fmalmeida/bioinfo/blob/master/dockerfiles/docker_install.sh) a try.
    * After installed, you need to download the required Docker image

          docker pull fmalmeida/ngs-preprocess

> Each release is accompanied by a Dockerfile in the docker folder. When using releases older releases, users can create the correct image using
the Dockerfile that goes alongside with the release (Remember to give the image the correct name, as it is in dockerhub and the nextflow script).
The latest release will always have its docker image in dockerhub.

2. Install Nextflow (version 20.01 or higher):

       curl -s https://get.nextflow.io | bash

3. Give it a try:

       nextflow run fmalmeida/ngs-preprocess --help

> Users can get let the pipeline always updated with: `nextflow pull fmalmeida/ngs-preprocess`

## Documentation

### Usage

* Complete command line explanation of parameters:
    + `nextflow run fmalmeida/ngs-preprocess --help`
* See usage examples in the command line:
    + `nextflow run fmalmeida/ngs-preprocess --examples`
* However, users are encouraged to read the [complete online documentation](https://ngs-preprocess.readthedocs.io/en/latest/?badge=latest).

### Command line usage examples

Command line executions are exemplified [in the manual](https://ngs-preprocess.readthedocs.io/en/latest/examples.html).

### Using the configuration file

All the parameters showed above can be, and are advised to be, set through the configuration file. When a configuration file is set the pipeline is run by simply executing `nextflow run fmalmeida/ngs-preprocess -c ./configuration-file`

Your configuration file is what will tell to the pipeline the type of data you have, and which processes to execute. Therefore, it needs to be correctly set up.

Create a configuration file in your working directory:

* Complete config:

      nextflow run fmalmeida/ngs-preprocess --get_full_config

* For Illumina data:

      nextflow run fmalmeida/ngs-preprocess --get_illumina_config

* For Pacbio data:

      nextflow run fmalmeida/ngs-preprocess --get_pacbio_config

* For ONT data:

      nextflow run fmalmeida/ngs-preprocess --get_ont_config

### Interactive graphical configuration and execution

Users can trigger a graphical and interactive pipeline configuration and execution by using [nf-core launch](https://nf-co.re/launch) utility.

#### Install nf-core

```bash
# Install nf-core
pip install nf-core
```

#### launch the pipeline

nf-core launch will start an interactive form in your web browser or command line so you can configure the pipeline step by step and start the execution of the pipeline in the end.

```bash
# Launch the pipeline
nf-core launch fmalmeida/ngs-preprocess
```

It will result in the following:

<p align="center">
<img src="./images/nf-core-asking.png" width="500px"/>
</p>

<p align="center">
<img src="./images/nf-core-gui.png" width="400px"/>
</p>

#### nextflow tower

This pipeline also accepts that users track its execution of processes via [nextflow tower](https://tower.nf/). For that users will have to use the parameters `--use_tower` and `--tower_token`.

# Citation

To cite this tool please refer to our Zenodo tag or directly via the github url.

Users are encouraged to cite the programs used in this pipeline whenever they are used. They are: [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), [TrimGalore](https://github.com/FelixKrueger/TrimGalore), [FLASH](https://ccb.jhu.edu/software/FLASH/), [Lighter](https://github.com/mourisl/Lighter), [Porechop](https://github.com/rrwick/Porechop), [pycoQC](https://github.com/a-slide/pycoQC), [bax2bam](https://github.com/PacificBiosciences/bax2bam), [bam2fastq](https://github.com/PacificBiosciences/bam2fastx), [lima](https://github.com/PacificBiosciences/barcoding), [pacbio ccs](https://ccs.how/) and [NanoPack](https://github.com/wdecoster/nanopack).
