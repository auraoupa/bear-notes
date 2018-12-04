# Faire tourner NEMO4.0_beta avec 2 zooms AGRIF
#CMEMS simus# #simus #NEMO
#NEMO4.0_beta# #debug #xios #occigen

## Récap :

1. Fabrication du domain_cfg.nc avec le nemo tool DOMAINcfg, sur occigen : `/scratch/cnt0024/hmg2840/albert7a/DEV/NEMO/trunk/tools/DOMAINcfg`
	1. compilation du tool avec arch-X64_OCCIGEN2jm2.fcm : `./maketools -n DOMAINcfg -m X64_OCCIGEN2jm2`
	2. copie de la namelist MAA13 dans namelist_cfg
	3. copie des fichiers coordinates et bathymetry
	4. `mpirun -np 1 ./make_domain_cfg.exe`
	5. résultat  `/scratch/cnt0024/hmg2840/albert7a/NACHOS12.L75/NACHOS12.L75-I/NACHOS12.L75_domain_cfg.nc`

2. nouveau DCM : `git clone https://github.com/meom-group/DCM.git DCM_4.0_beta`
3. nouveau NEMO : dans DCMTOOLS/NEMOREF : `svn co http://forge.ipsl.jussieu.fr/nemo/svn/NEMO/trunk -r 9974 NEMO4`
4. nouveau module : module/NEMODRAK/4.0_beta
5. nouveau xios : `svn co http://forge.ipsl.jussieu.fr/ioserver/svn/XIOS/dev/dev_olga rev 1587`
	1. copie des arch files de l’ancienne version
	2. compilation : `./make_xios --arch X64_OCCIGEN`
6. fabrication du resto.nc avec le cdftool cdfmkresto, sur occigen : script  `/scratch/cnt0024/hmg2840/albert7a/DEV/MKRESTO/make_resto.ksh`,  résultat : `/scratch/cnt0024/hmg2840/albert7a/NACHOS12.L75/NACHOS12.L75-I/NACHOS12.L75_resto.nc`
7. Phasing des namelists : https://github.com/auraoupa/CMEMS-simus/blob/master/new_version_NEMO-trunk-rev9853/2018-08-29-AA-phasing-namelists.ipynb
8. Nouveau script de lancement du run :  `/scratch/cnt0024/hmg2840/albert7a/DEV/DCM_4.0_beta/RUNTOOLS/bin/nemo4.0.ksh` (corrigé au fur et à mesure des erreurs …)
9. Nouveaux bdy et init à partir de sosie : [Construction bdy et init via sosie 3D](bear://x-callback-url/open-note?id=0349E23B-17FE-4F56-82BF-1EC314486C6A-4356-00006852A6BD678E)

## Problèmes rencontrés :

1. `mpp_init` assez différents entre les 2 versions pour que les découpages obtenus avec l’outil MPP_PREP ne colle plus -> nouveau découpage 66x45 = 1576
2. la nouvelle version de xios ne gère pas encore l’élimination des procs terre -> pas d’élimination 66x45=2970
3. erreur au niveau de stp_ctl : Smin=0 ou Smax= 250 -> sans bdy ni init ca tourne !
4. merge des sorties pas faites -> il faut linker domcfg.nc au lieu de coordinates.nc qui n’existe plus, modif dans DCM_4.0_beta/RUNTOOLS/bin/function_4.0_all.ksh

30 nov. 2018
Toujours pas d’état initial qui marche.

Plus le pb pour la salinité mais U dépasse 10m/s dans mers Caraibes avec instabilités en salinité et alors que dans l’état initial c ok …

Le drowning de salinité vers les continents ne marche pas très bien : apparition de 0 intempestifs, près des côtes -> remplacer la valeur par défaut sur les continents par 30 au lieu 0 ?

5 nov. 2018

MAA40devolga tourne ok, sans les flags, en faisant bien gaffe aux chemins vers la version xios

Et le mvnc2s.ksh il se fait dans XIOS.1 pas dans le WRK.xxx !!

30 oct. 2018

MAA40devolga debug :

in traadv_fct.f90, interp_4th_cpt : subscript #3 of the array pt_in has value 0 which is less than the lower bound of 1

29 oct. 2018

2 pistes pour que l’élimination des procs terre fonctionne :
* test avec xios 2.5 devolga -> erreur xios `Not enough data in buffer to unqueue the data` malgré paramètre de Romain dans iodef.xml `optimal_buffer_size` , `buffer_size_factor` et `min_buffer_size`
-> mais en fait ça marche !!
* test xios 2.0_rev_1499 avec NEMO4.0_rev_10230 -> idem pb xios mask