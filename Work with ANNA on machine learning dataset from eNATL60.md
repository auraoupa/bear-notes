# Work with ANNA on machine learning dataset from eNATL60

## Mardi 16 o octobre 
changer le calcul de densité avec gsw : pip install gsw

## Lundi 7 octobre
Toutes les étapes pour qu’Anna puisse faire tourner les diags sur occigen :

- [ ] environnement conda, demander a svp
- [ ] sshfs pour faire les git clone et push
- [x] module load firefox
- [ ] réglages pour dask-jobqueue :  /home/albert7a/.config/dask/jobqueue.yaml
- [ ] git clone https://github.com/serazing/xscale.git 
 
## Lundi 28 Septembre
- [ ] faire les 66 boîtes de LS -> 
- [ ] faire les 102 boîtes de GS  ->
- [ ] les profiles sur cal1 et meomdap
- [ ] check si w’b’ prossible aussi en single node pour chaque boîte ->
- [x] script pour extractions eORCA1
- [ ] mail à Anna

## Vendredi 27 Septembre
- [x] faire un script python qui construit tous les prédicteurs pour une boîte et une date
- [x] combien de temps ca prend -> 1h et quelques
- [ ] lancer sur 66 procs
- [ ] idem pour w’b’

## Jeudi 26 Septembre
Idée : faire un script pour une boîte, toutes les variables à sauver puis distribuer le script pour toutes les boîtes et une date sur les noeuds de calcul d’occigen

## Mercredi 25 Septembre

Je me casse la tête à retrouver les indices dans la grille ORCA1 au centre des boîtes, son script est vraiment tordu je prendrais les coordonnées au centre de chaque boîte et retrouverai les indices en fonction …
- [ ] faire profils prédicteurs dans eNATL60

1mn par boîte pour une variable et un jour c’est beaucoup …
et si je réduisais avant les calculs en coupant la région LS puis je passe en arrays non dask pour reparalleliser sur les 66 boîtes ?

## Mardi 24 Septembre

- [x] check scripts Anna pour les boîtes : [Code_local/2019-09-18-ADS-test-boxes-ORCA1x1_LS.ipynb at master · AnnaDSMS/Code_local · GitHub](https://github.com/AnnaDSMS/Code_local/blob/master/2019-09-18-ADS-test-boxes-ORCA1x1_LS.ipynb)
J’ai fait tourner ses scripts sur occigen, 66 boîtes dans le labrador, 102 dans le Gulf Stream et plus de 400 dans MNA …
- [x] faire les boîtes aux 1/60°

## Avant

- [ ] check filtrage boxcar from xscale -> choose the best filt
	- [x] [formation_ANNA/2019-07-19-AA-testing-hanning-window-filtering.ipynb at master · auraoupa/formation_ANNA · GitHub](https://github.com/auraoupa/formation_ANNA/blob/master/check_filtrage/2019-07-19-AA-testing-hanning-window-filtering.ipynb) : meilleur résultat hanning, cutoff=20, n=30
	- [x] demander à Guillaume de conseils 
	- [x] réponse Guillaume 
- [x] mail à Anna compte rendu discussion Julien
- [x] calcul w’b’ 1 niveau 1h
	- [x] tester différents chunks
		* 1000x1000 c le mieux
	- [x] tester plusieurs boites pour un ficher
		* on ne multiplie pas par le nombre de boîtes, ouf !
		* 1 boite = 1mn
		* 2 botîtes = 2mn
		* 14 boîtes = 14mn
- [x] ecrire netcdf au fur et a mesure
- [ ] préparer profiles w’b’ pour 1 jour et 1 niveau vertical : moyenne sur 1 jour
	- [ ] calcul pas fini avec dask-jobqueue [Dask job-queue](bear://x-callback-url/open-note?id=84F12E8E-0B7C-49C9-88B6-A24FD4C83FB6-2273-00006140FEEC829D)
- [x] préparer script pour T,S,U,V,dxT,dyT,dxS,dyS,dxU,dyU,dxV,dyV
- [x] tester optimisation avec numba pour une boucle sur les niveaux verticaux -> pas possible, numba pas adapté à mon calcul
- [ ] boucle sur les fichiers et les boîtes

Par instant il y a 3 zones:
GS: 33.5-39.5N, 70.6-60W,min depth = 840.646
LS: 56-61N, 55-50W, min depth = 2955.2122m
MNA: 42-55N, 40-20W, min depth = 663.58m

## 2 aout 2019

Salut Anna (et Julien pour un point sur l’avancement),

Voilà où j’en suis avant de partir en vacances concernant la construction
des profils :
- le notebook qui génère les profils moyens de T,S,U,V,W
 [https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/make_profiles/2019-07-24-AA-make-u-v-t-s-w-profiles-dask-jobqueue-in-netcdf.ipynb](https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/make_profiles/2019-07-24-AA-make-u-v-t-s-w-profiles-dask-jobqueue-in-netcdf.ipynb) ,
environ 5-6mn par variable pour une moyenne des 24h, les 300 niveaux et
14 boîtes de 2°x2°
- le notebook qui calcule les gradients horizontaux de ces mêmes
variables :
 [https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/make_profiles/2019-07-25-AA-make-dx-dy-u-v-t-s-w-profiles-dask-jobqueue-in-netcdf.ipynb](https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/make_profiles/2019-07-25-AA-make-dx-dy-u-v-t-s-w-profiles-dask-jobqueue-in-netcdf.ipynb) ,
on est plus sur du 20mn par variable
- le notebook pour le calcul de w’b’ :
 [https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/make_profiles/2019-07-31-AA-make-wprimebprime-profiles-dask-jobqueue-in-netcdf.ipynb](https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/make_profiles/2019-07-31-AA-make-wprimebprime-profiles-dask-jobqueue-in-netcdf.ipynb) ,
je n’ai pas encore pu le faire tourner en entier pour toutes les boîtes,
il faut que je trouve la bonne combinaison de nombre de workers et
nombres de processeurs pour avoir assez de mémoire

Il n’y a pas eu d’optimisation particulière, mis à part l’utilisation de
chunks à l’ouverture des fichiers qui permettent la parallelisation de
certains calculs. Numba ne s’applique pas dans notre cas. J’espère avoir
de nouvelles idées au meeting euroscipy où je vais début septembre …

Pour le filtrage j’ai utilisé un filtre spatial avec fenêtrage de hanning
d’une taille de 30 points de grille et une fréquence de coupure d’environ
20km, c’est la combinaison de paramètres qui me donnent les meilleurs
résultats sur les spectres (avant dernier plot du notebook
 [https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/check_filtrage/2019-07-23-AA-filtering-lanczos-like.ipynb](https://github.com/auraoupa/preparation_eNATL60_profiles_ANNA/blob/master/check_filtrage/2019-07-23-AA-filtering-lanczos-like.ipynb) )

Une fois que tu auras défini les nouvelles boîtes en 2°x2° et 1°x1°
correspondant aux grilles ORCA1 et ORCA2, je pense que tu pourras utiliser
mes notebooks pour générer les profils prédicteurs dans les runs ORCA1 et
ORCA2 que tu auras trouvé sans problèmes sur ton ordi (avec les bonnes
librairies python et xscale pour le filtrage). En revanche les faire
tourner sur occigen sur eNATL60 me parait plus compliqué, peut être c’est
mieux d’attendre que je sois rentrée fin août pour qu’on le fasse
ensemble.

## 17 juillet 2019

Tout d’abord comme l’idée finale c’est d’améliorer les modèles basses résolutions il faudrait faire des boîtes 2°x2° et 1°x1° en fonction des grilles ORCA2 et ORCA1.

Et pour valider les prédicteurs il faudrait vérifier que les profils T,S,U, V dxT, dyT etc … soient comparables quand on fait la moyenne de eNATL60 et quand on prend un profil d’un run ORCA1 ou ORCA2.

Est-ce que tu aurais des runs ORCA1 et ORCA2 disponibles au LOCEAN par Julie peut-être ?

Dans l’idéal il faudrait que tu choisisses 2 régions de latitudes différentes (par exemple dans le Gulf Stream et dans la mer du Labrador) et que tu définisses quelques boîtes 1°x1° et les 2°x2° correspondantes à l’intérieur.

Avec ces boîtes moi je produit les profils moyens des prédicteurs et tu les compares avec les profils ORCA1 et ORCA2. Je produis ensuite les profils moyens de w’b’ et tu les compares entre eux, on veut qu’ils soient lisses et robustes.

Je ferais différents tests aussi sur quelle période temporelle je moyenne (entre 1 jour et 10 jours, voire 1 mois maximum)

Qu’est-ce que tu en penses ? Est-ce que ça te va comme plan ? Tu vois comment faire pour fabriquer des nouvelles boîtes dans un script du genre : [https://github.com/auraoupa/formation_ANNA/blob/master/make_boxes/2019-07-08-AA-test-boxes-2x2.ipynb](https://github.com/auraoupa/formation_ANNA/blob/master/make_boxes/2019-07-08-AA-test-boxes-2x2.ipynb) ? Je pense qu’il faut définir les limites des boîtes latmin, latmax, lonmin, lonmax en fonction des points des grilles ORCA1 et ORCA2 (lon_ORCA1-0.5°, lon_ORCA1+0.5° par exemple )