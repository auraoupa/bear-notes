# visu avec occigen

- [ ] calculs sur fichiers sur store -> check si sur bande avant
- [ ] test gestion librairies sur pypi -> en fait c’est pip

- [ ] se connecter sur visu.cines.fr
	- [ ] lancer la commande vizalloc
	- [ ] ouvrir turbovnc et se connecter -> ca ne marche pas ..

- [ ] se connecter sur visu.cines.fr
	- [ ] source activate pangeo
	- [ ] in `/home/albert7a/.jupyter/jupyter_notebook_config`
`.py`
	- [ ] 	commenter la ligne `c.NotebookApp.password = ...`
	- [ ]  décommenter la ligne `c.NotebookApp.open_browser=True`
	- [ ] module load firefox
	- [ ] lancer jupyter-notebook
		- [ ] ca ne marche plus …

	
- [ ] conda environment
- [ ] python -m ipykernel install —user —name env —display-name
	- [ ] en offline uniquement, installation avec pip, ou en demandant l’installation par svp@cines
	

- [ ] Pour faire fonctionner le jupyterhub :
	- [ ] se connecter et selectionner un noeud de visualisation
	- [ ] la commande depuis le même terminal (qui nous a rendu la main car ca se deconnecte aussitot) : `ssh -N -L 8889:visu10.sis.cnes.fr:5902 alberta@hal.cnes.fr`
	- [ ] client vnc (turbovnc sur ma machine) localhost:8889, cela ouvre un émulateur windows dans lequel on ouvre mozilla
	- [ ] adresse` https://jupyterhub.sis.cnes.fr`
	- [ ] le wiki : `https://gitlab.cnes.fr/hpc/wikiHPC/wikis/jupyter`
	- [ ] exemple de notebook : `https://gitlab/cnes.fr/inno/rt-nouvelles-technos-distrib/`
