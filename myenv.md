Olivier Kirsh <olivier.kirsh@u-paris.fr>  
20199814  

This folder contains yml files of miniconda envs.
All have been updated on 20190814.  
Cytoscape must not be updated. An alias start an env with the right jdk version and the app located in Apps/  
Last R version is 3.6.1, but my env with my packages runs on r-3.5.1

# conda environments:
```
conda env list
#
base                  *  /home/olivier/miniconda3
cytoscape                /home/olivier/miniconda3/envs/cytoscape
jpnb                     /home/olivier/miniconda3/envs/jpnb
ngs                      /home/olivier/miniconda3/envs/ngs
rst35ngs                 /home/olivier/miniconda3/envs/rst35ngs
rst36                    /home/olivier/miniconda3/envs/rst36
ufr                      /home/olivier/miniconda3/envs/ufr
```

# Export  

```
conda env export -n ufr --no-build > ufr-20190814.yml
conda env export -n rst36ngs --no-build > rst36ngs-20190814.yml
conda env export -n ngs --no-build > ngs-20190814.yml
conda env export -n rst35ngs --no-build > rst35ngs-20190814.yml
conda env export -n jpnb --no-build > jpnb-20190814.yml
conda env export -n cytoscape --no-build > cytoscape-20190814.yml
conda env export -n rst36 --no-build > rst36-20190814.yml
```

# restore  

```
conda env create -n ufr -f ufr-20190814.yml 
```

# Channels  

my channels configurated like at ifb core for a better interoperability with singularity.  
r channels is removed. It is needed to get the very last R version and rstudio, but conflicts with other packages can occur.  
conda-forge > bioconda. It is counterintuitive, but seems to be more up to date and complete than bioconda.  
R packages can easily be installe with conda ( -c r/bioconda/conda-forge), but for proper bioconductor installation prefere biocManager::install() inside R session. Clone **rst36** env at projects startup.  

```
conda env create --name myproject --clone rst36
```

or create one from rst36-20190814.yml

```
conda env create -n myproject -f rst36-20190814.yml
```

## Channel infos

```
conda config --get channels

--add channels 'defaults'   # lowest priority
--add channels 'bioconda'
--add channels 'conda-forge'   # highest priority
```

## Channel set up

```
conda config --add channels 'r'
```
the last will be the highest priority  

# infos
```
conda info

     active environment : base
    active env location : /home/olivier/miniconda3
            shell level : 1
       user config file : /home/olivier/.condarc
 populated config files : /home/olivier/.condarc
          conda version : 4.7.11
    conda-build version : not installed
         python version : 3.7.3.final.0
       virtual packages : 
       base environment : /home/olivier/miniconda3  (writable)
           channel URLs : https://conda.anaconda.org/conda-forge/linux-64
                          https://conda.anaconda.org/conda-forge/noarch
                          https://conda.anaconda.org/bioconda/linux-64
                          https://conda.anaconda.org/bioconda/noarch
                          https://repo.anaconda.com/pkgs/main/linux-64
                          https://repo.anaconda.com/pkgs/main/noarch
                          https://repo.anaconda.com/pkgs/r/linux-64
                          https://repo.anaconda.com/pkgs/r/noarch
          package cache : /home/olivier/miniconda3/pkgs
                          /home/olivier/.conda/pkgs
       envs directories : /home/olivier/miniconda3/envs
                          /home/olivier/.conda/envs
               platform : linux-64
             user-agent : conda/4.7.11 requests/2.22.0 CPython/3.7.3 Linux/4.15.0-55-generic ubuntu/18.04.3 glibc/2.27
                UID:GID : 1000:1000
             netrc file : None
           offline mode : False

```

