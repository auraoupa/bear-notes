# Dask job-queue on occigen

réglages par défaut dans /home/albert7a/.config/dask/jobqueue.yaml

options sbatch à connaître :
- cpus-per-task
- ntasks : nb de processeurs
- nodes : nb de noeuds
- ntasks-per-node : nb de processurs par noeuds (24 sur HSW24, 28 sur BDW28)
- n = ntasks

options dask-jobqueue
- cores : total number of cores per job = ntasks
- processes : number of processes per job

noeuds > processeurs > coeurs