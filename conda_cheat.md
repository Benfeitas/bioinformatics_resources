# Conda cheat sheet

**Main commands**
- `conda create -p [environment_name]` - creates new environment
- `conda env create -f [file.yaml] -p [environment_name]` - creates env from file specifies path
- `conda activate [environment_name]` - activates the environment
- `conda install python=3.7` - installs software to the env
- `conda env update -f [file.yaml]` - updates current env based on file
- `conda deactivate` - deactivates and closes env
- `conda info --envs` - shows info from environments
- `conda env export -p [env_name]` - exports all. NOT RECOMMENDED
- `conda clean -a` - cleans previous environments

Search packages/versions in anaconda cloud: [https://anaconda.org/](https://anaconda.org/). Packages labeled noarch are compatible with all OS  

Good practice to add software is to ask conda to install but deny installation, as these will check for compatible versions. Then add it to `.yaml`
Main channels:
    Defaults
    Condaforge
    Bioconda

Example .yaml:
```
channels:
- conda-forge
- bioconda
- defaults
dependencies:
- r-base=3.5.1
- rstudio=1.1.456
- r-seurat=3.0.0
```