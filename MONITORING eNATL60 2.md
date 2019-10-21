# MONITORING eNATL60

1. linker les sorties de Laurent chez moi en changeant les noms de fichier en type DRAKKAR : sur marenostrum, dans `/home/pr1egh00/pr1egh03/scripts/make_links_drakkar_simus.ksh`
2. mkmeans CONFIG CASE
3. moyennes mensuelles 1h pour var de surface : gridT, gridV, gridU, flxT : `config_moy.ksh` à régler dans `CTL/CDF` de la simu puis `./RUN_calmoy.ksh YEAR`
4. extraire niveaux verticaux pour sorties 3D à 1d ou 5d : réglage dans `config_moy.ksh` puis `./RUN_extract_levels.ksh`


7 nov. 2018
- [ ] monitoring fin 2008 BLB000
	- [ ] moy mens 1h
	- [ ]] ext lev 5d