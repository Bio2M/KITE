# KITE


## Installation

There are three ways to use KITE: download an apptainer/singularity container, create a container, or install the software via Miniconda.

### 1. Download apptainer container

prerequisite : apptainer (or singularity)

```
apptainer pull --arch amd64 library://devbio2m/kite/kite:latest
```

### 2. create container

prerequisite : apptainer (or singularity)

```
git clone https://github.com.Bio2M/KITE
cd KITE
apptainer build kite.sif kite.def
```

### 3. Miniconda

prerequisites : 

- miniconda installed and operational
- bc installed (shell calculator)


```
git clone https://github.coms.Bio2M/KITE
cd KITE
conda create -f kite_env.yml
export PATH=${PWD}/src:$PATH
```

## Usage

### With apptainer

**input files are in the working directory or HOME directory**

```
export PATH=/path/to/kite.sif/ 

kite.sif kcount -i metadata.csv -n 12 -d path/to/fastq
kite.sif kfilter -i metadata.csv -n 4 -s t -t 0.5
kite.sif kml -i metadata.csv -n 4
```

**input files are not in the working directory or the HOME directory**

```
apptainer run --bind /path/to/files path/to/kite.sif kcount -i metadata.csv -n 12 -d path/to/fastq
apptainer run --bind /path/to/files path/to/kite.sif kfilter -i metadata.csv -n 4 -s t -t 0.5
apptainer run --bind /path/to/files path/to/kite.sif kml -i metadata.csv -n 4
```

### with miniconda

```
conda activate kite 

kite kcount -i metadata.csv -n 12 -d path/to/fastq
kite kfilter -i metadata.csv -n 4 -s t -t 0.5
kite kml -i metadata.csv -n 4
```

