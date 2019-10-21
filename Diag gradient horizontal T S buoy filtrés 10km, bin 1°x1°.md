# Diag gradient horizontal T S buoy filtrés 10km, bin 1°x1°
#CMEMS diags# #TSG #GuillaumeSérazin

1. filtrage 2D fréquence de coupure 10 points de grille des sorties journalières de surface T et S  : script `/home/albert7a/python/filtering/make_filt_sst_sss_fc10.ksh`, résultats dans le dossier `/scratch/cnt0024/hmg2840/albert7a/NATL60/NATL60-CJM165-S/filt/`, fichiers `NATL60-CJM165_y*.1d_hgradT/S_filt-n80-f0.1.nc`, attention il faut garder la partie « large scale » et pas la partie « fine scale » …
2. calcul de la buoyancy à partir des champs de surface : script `/home/albert7a/python/cdfbuoy/make_cdfbuoy_job_all_NATL60_surf.ksh`
3. calcul de gradients horizontaux avec le cdftool cdfhgrad, script : `/home/albert7a/EXTRACT/compute_hgrad_surf_TS_filt.ksh`
4. ajout des tableaux nav_lat nav_lon dans les fichiers : script `/home/albert7a/EXTRACT/replace_nav_file_hgrad.ksh` avec outil fortran dans `/scratch/cnt0024/hmg2840/albert7a/DEV/REPLACE_NAV`
5. concaténation pour les saisons JFM et JAS : script `make_concat_JFM_JAS.ksh` dans le même dossier
6. sur occigen, binning 1°x1° et médiane sur les 3 mois : https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/binning_1file_3month.py, résultats `/scratch/cnt0024/hmg2840/albert7a/NATL60/NATL60-CJM165-S/filt/NATL60-CJM165_JFM/JAS_hgradT/S_filt10km_bin1x1.nc`
7. comparison plots are here : https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/TSG_JFM_data-NATL60.png and https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/TSG_JAS_data-NATL60.png
8. plots avec échelles log : https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/TSG_JAS_data-NATL60_log.png, https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/TSG_JFM_data-NATL60_log.png et le ratio entre hiver et été : https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/TSG_ratio-JFM-JAS_data-NATL60_log.png
9. binning sur l’année au lieu de 3 mois, concaténation sur l’année `make_concat_annee.ksh` puis binning et médiane sur l’année : https://github.com/auraoupa/CMEMS-diags/blob/master/TSG_Guillaume/binning_1file_year.py exécuté sur occigen, résultats `/scratch/cnt0024/hmg2840/albert7a/NATL60/NATL60-CJM165-S/filt/NATL60-CJM165_year_hgradT_filt10km_bin1x1.nc`
10. binning sur l’année pour les données : sur cal1
11. distribution dans 3 grandes boîtes GS : 65°W-60°Wx37°N-42°N, NE : 10°E-15°Ex55°N-60°N et AC 32°W-67°Wx31°N-36°N, définition des boîtes dans fichier natl60_3_5_by_5_boxes.py

30 nov. 2018

Comparaison NATL60 données pour les gradients T S et buoyancy, JFM et JAS, on se rend compte que plusieurs choses ne marchent pas :

en hiver :
1. gradients T en dehors du GS trop forts dans le modèle
2. gradients S dans les mers nordiques trop forts dans le modèle
3. donc gradients b en dehors du GS trop forts

en été :
1. gradients T dans l’est du bassin sont trop forts
2. gradients S dans les mers nordiques + est du bassin sont trop forts
3. mais gradients b plutot pas mal

On aimerait  regarder la répartition du nombre d’observations pour voir si l’est du bassin ne serait pas sous-représenté dans les obs -> je fais la figure

Plus généralement, on aimerait voir ce qu’il se passe sur toute l’année sans distinctions de saisons -> Guillaume est-ce que tu pourrais m’envoyer les données sur toute l’année.

Ensuite pour expliquer les différences de gradients de température on aimerait comparer les formes de distribution dans quelques grosses boites de 5°x5° : 1 dans le Gulf Stream, 1 dans le Nord Est et 1 aux Acores pour voir si on a plus de fronts ou des fronts intenses -> il me faudrait donc les données non moyennées (médianisées plutot) dans les bins

Enfin, et on le fera pas tout de suite, il serait interessant de comparer des spectres de température dans certaines régions avec des spectres de données satellite.

23 oct. 2018

Plot de buoyancy avec des valeurs hors colorbar le long des côtes.
Tentative de masker avec le nombre d’observations mais il en reste.
Récupérer le mask dû au filtrage pour l’appliquer : c’est le mask pour le filtrage plus haute resolution -> il faut le refaire pour le filtrage à 10km !
Avec les scripts `Weight2DLanczosHighPassFilter.py` et `mask_filt_n80-f0.1.ksh`  résultat `/scratch/cnt0024/hmg2840/albert7a/NATL60/NATL60-I/NATL60-CJM165_mask-surf_filt-n80-f0.1.nc`

Il faut maintenant appliquer le mask avant le binning …
17 oct. 2018

Par défaut l’ouverture des fichiers pour les 3 mois se fait avec n chunk en temps (time_counter :1), ce qui doit poser problème pour l’opération median
-> en chunkant en x et y plutot est-ce que ça marcherait pas mieux ?? non

La solution : concaténer les 3 mois en 1 seul fichier puis l’ouvrir simplament avec open_dataset, le reste des opérations marche nickel !!

16 oct. 2018

Ca ne marche pas terrible, des MemoryError, des time limits, en interactif du median is not yet implemented on dask arrays …

J’ai besoin de dask pour ouvrir les fichiers 3 mois de NATL60 -> en fait non !! Mais pb opération median avec dask …

15 oct. 2018

Problème MemoryError pour le binning des gradients filtrés pour une saison entière : en séparant temporellement c’est pas bon on perd le côté médiane dans un bin. Il vaut mieux parallèliser selon les bins  mais alors comment regrouper pour faire la carte finale ?!

Test sur un bin, qu’est-ce que ça donne dans le fichier final ?

Les premiers bins sont souvent vides, je teste sur une bande, en soulettant directement un job plutot que de lancer dans ipython.



