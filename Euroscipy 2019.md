# Euroscipy 2019

## Lundi 2 septembre 2019
### Jupyterlab tutorial

Python Academy
some extras magics :
%bookmark
%history
%save filename blocknumero
%run
%prun
%xmode
%prun
%whos

shortcuts :
esc+6 : change to markdown

### Reproducible science
[reproducible-data-science/tutorial-intro.ipynb at 10b69b54630ee3f8d0106f94043c800a3374c0bb · SwissDataScienceCenter/reproducible-data-science · GitHub](https://github.com/SwissDataScienceCenter/reproducible-data-science/blob/10b69b54630ee3f8d0106f94043c800a3374c0bb/presentation/tutorial-intro.ipynb)

Swiss data science center
renku

etude : 90% of 306 articles not reproducible at all
transparency, controlling of errors

4 key-ingredients :
	- [ ] versioned, well-strctured code
	- [ ] perserved and available data
	- [ ] runtimle environment
	- [ ] workflow description

tools :
	- [ ] version control git,github,gitlab
	- [ ] data repository : zenodo, figshare, dataverse
	- [ ] packaging and environment : pip, conda, containerization (docker,singularity)
	- [ ] workflow/pipeline description : workflow manager (airflow)

matrix of tools
binder, renku
doc : [Welcome to Renku! — RENKU 0.4.1 documentation](https://renku.readthedocs.io/en/latest/)

hands-on : [reproducible-data-science/README.md at master · SwissDataScienceCenter/reproducible-data-science · GitHub](https://github.com/SwissDataScienceCenter/reproducible-data-science/blob/master/hands-on/hosted_notebook/README.md)

papermill : notebooks ran as a script [Parameterize — papermill 1.1.0 documentation](https://papermill.readthedocs.io/en/latest/usage-parameterize.html)

comme on construit un workflow, si on modifie un petit truc au début, il suffit d’une ligne pour tout refaire !
et comme tout est  versionné on peut faire la différence entre les 2

### AirFlow

[About the workshop — EuroScipy tutorial  documentation](https://opendata-airflow-tutorial.readthedocs.io/en/latest/about.html)

pour le monitoring ?
plutot pour les taches repetitives

### Speeding your python code

[GitHub - jeremiedbb/tutorial-euroscipy-2019: Speed up your Python code](https://github.com/jeremiedbb/tutorial-euroscipy-2019)

INRIA

transformer du python en C pour améliorer les perfs

## Mardi 3 septembre 2019

### Geopandas

[GitHub - jorisvandenbossche/geopandas-tutorial: Tutorial on geospatial data manipulation with Python](https://github.com/jorisvandenbossche/geopandas-tutorial.git)

### Numpy

[GitHub - leriomaggio/numpy-euroscipy: Introduction to NumPy - Tutorial @ EuroSciPy](https://github.com/leriomaggio/numpy-euroscipy.git)

### Matplotlib

[GitHub - timhoffm/euroscipy2019-using-matplotlib: Tutorial at EuroSciPy 2019](https://github.com/timhoffm/euroscipy2019-using-matplotlib)

### PyComps

[GitHub - bsc-wdc/tutorial_apps: COMPSs and PyCOMPSs applications used for tutorials.](https://github.com/bsc-wdc/tutorial_apps)

## Mercredi 4 septembre

### GPU & Dask
peter andreas entschev nvidia
RAPIDS
GPU faster

### DataFrame and pipelines
maarten breaddels
vaex.io

apache arrow 

pour refaire une serie d’opérations : pipeline dans un json

### Open source projects update

numpy
pypi 7.1.1
pandas 0.24.0 Int64 type, join multi-index, , 0.25.0 python3, pandas 1.0 
matplotlib 3.2

### Scientific DevOps
Nicholas del Grosso

[GitHub - nickdelgrosso/devops_talk_euroscipy2019: Slides from the talk « Scientific DevOps: Designing Reproducible Data Analysis Pipelines with Containerized Workflow Managers » given at EuroScipy 2019 in Bilbao, Spain](https://github.com/nickdelgrosso/devops_talk_euroscipy2019)

snakefile : input + output + script, snakemake

### Caterva

like hdf and zarr, plus axé sur la mémoire

### Transonic
5 
[pres slides](http://www.legi.grenoble-inp.fr/people/Pierre.Augier/docs/ipynbslides/20190904-euroscipy-transonic/pres.slides.html#/)

utilise cython, numba, pythran tout ça en plus facile ?

### Best coding practices in jupyterlab
 [Alexander CS Hendorf](https://pretalx.com/euroscipy-2019/speaker/78ZETH/) 

it should be reproducible w minimal effort
maintainable transportable

run in sequence so re-run notebook, cache or save data
code cell should fit on the screen
split in smaller functions

no copy paste, import from other module
classes for processing pipelines

clean up constantly

dependencies : document pythin version, virtual environments

### Numba CUDA
[Lessons learned from comparing Numba-CUDA and C-CUDA ::  EuroSciPy 2019 :: pretalx](https://pretalx.com/euroscipy-2019/talk/UHMWGH/)

## Jeudi 5 septembre

### HPC and python
David Liu

tellement bla bla …
culture change 😒🤮

[Kubeflow Kale: from Jupyter Notebook to Complex Pipelines · GitHub](https://gist.github.com/leriomaggio/6d3c869ff1286d9105600003574e503f)

### Visual diagnostics at scale
[Visual Diagnostics at Scale ::  EuroSciPy 2019 :: pretalx](https://pretalx.com/euroscipy-2019/talk/D7WAFW/)

yellowbrick

### Parallel computing
[Recent advances in python parallel computing ::  EuroSciPy 2019 :: pretalx](https://pretalx.com/euroscipy-2019/talk/EQNGSQ/)
concept embarassingly parallel

multiprocessing vs ~~multithreading~~ (no data copies, transfert)

gil : global limitation multithreading -> sequential

libraries :
	- multiprocessing (pas bon dans interactive session)
	- loky = better multiprocessing

cloudpickle

### Numba

### Pypy

### Lightning talks

#### python profiling 
cProfile, line_profiler, vmprof

daal4py














