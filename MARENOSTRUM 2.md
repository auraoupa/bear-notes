# MARENOSTRUM
[Support Knowledge Center @ BSC-CNS](https://www.bsc.es/user-support/mn4.php)

pr1egh03, groupe pr1egh00, laurent pr1egh01

sbatch, scancel, etc …

envoyer ou récupérer des données via dt01.bsc.es

in case of REMOTE HOST IDENTIFICATION HAS CHANGED : do a ssh-keygen -f « /home/albert/.ssh/knwon_hosts »  -R dt01.bsc.es

in case of error while laoding shared libraries etc … -> ajouter la lib dans LD_LIBRARY_PATH

ssh -CX pr1egh03@mn1.bsc.es

enchainer les jobs tant qu’ils sont pas finis :

jobid=$(sbatch script.ksh | awk ‘{print $NF}’)
sbatch -d afternotok:$jobid script.ksh