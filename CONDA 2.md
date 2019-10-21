# CONDA
#conda #tricks

`conda create —-name new-env —-clone old-env`

environnement par défaut : base

`conda info -—envs`



conda list --explicit > spec-file.txt
conda create --name myenv --file spec-file

source activate myenv

installer un package offline :

* trouver le package sur https://anaconda.org/conda-forge 
* le mettre dans anaconda2/pkgs
* conda isntall pkg

enlever un env : `conda remove —name myenv —all`