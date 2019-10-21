# Running GS36

Following :  [CMEMS-simus-regionales/2019-04-15-AA-setting-up-regional-configs-from-NACHOS12.ipynb at master · auraoupa/CMEMS-simus-regionales · GitHub](https://github.com/auraoupa/CMEMS-simus-regionales/blob/master/prep/2019-04-15-AA-setting-up-regional-configs-from-NACHOS12.ipynb)


## Vendredi 18 octobre 2019

dans le cas rim de 10 il faut adapter la bathy pour pas qu’il y ait de mur à l’entrée des bdy, peut être aussi dans le cas bdy de rim 1 dailleurs …
solution de facilité = pas de mask des champs interpolés ?

r96 avec rdt=120 -> plante le 28 janvier

## Mardi 15 Octobre 2019

	* r97, MAA013 : bdy avec rim de 10 like Pedro -> bug dans nambdy certains bdy etaient a etat init -> bug rim à 1 dans nambdy -> ca plante a kt=1 pb de mask frontière est
	* r96, MAA012 : bdy de rim 1 test avec rdt=120 -> 

## Jeudi 10 Octobre 2019

Investigation de pourquoi ca plante MAA012 au bout de 11 jours :
		- [ ] 	crash en ssh à i=1377 et j=2 frontière sud
		- [ ] rien de suspect sur les sorties horaires


## Semaine du 16 au 20 septembre

check des bdy 1rim : la frontière nord est tout à 0 car pas pris le bon niveau
question : avec rim est-ce qu’on prend aussi le niveau = 0 ou cela s’entend sans ? ce n’est pas le cas à la frontière sud bizarrement !
c’était pas le bon niveau pour la frontière nord


## Semaine du 2 au 6 septembre 2019

MAA008 : ca tourne !
		- [ ] rdt = 60 -> oui
		- [ ] rdt = 120 -> oui
		- [ ] rdt = 240 -> non
		- [ ] rdt = 180 -> oui

construction des bdy avec nouveau sosie -> done
test MAA009 : 
		- [ ] 	rdt = 60
		- [ ] 

test MAA010 avec un rim de 1 : plein d’erreurs puis explosion 

## Vendredi 30 aout 2019

Ini refait et maské pas de petits trucs chelous
MAA008 pour tester sans bdy : 

## Jeudi 29 aout 2019

j’avais pas refait les états initiaux avec nouvelle grille 3.6like ?
j’avais pas non plus mis de bathy dans la namelist sosie …
utilisation du sosie de JM : bug en surface, je reprends sa namelist -> en fait j’enlève une de ses modifs

sans les bdy, rdt=60 explosion Smax en 1208,2,59 au bout de 59 pas de temps -> check ini : des petits points a 20PSU …

## Mercredi 28 aout 2019
Récap :
- run GS36.L75-MAA007 (91) : avec bdy, rdt=30, BDW28, segmentation fault mxm_handle_error

pour Jean-Marc ca tourne avec 150 niveaux, BDY et meme ubs avec pas de temps 120 (90 avec bdy)

- [ ] refaire init et bdy avec new sosie
- [ ] check init et bdy en sections
- [ ] faire config avec 150 niveaux


## Vendredi 2 aout 2019
j’essaie de rajouter les bdys : pb HDF error, permissions ? non, test en nc3


## Mardi 30 juillet 2019

meeting w Jean Marc : plusieurs pb : vvl activé, ebdy_coordinates pas bon, quelques paramètres à changer
MAA006 : ca marche pour un jour avec pas de temps de 30, (40 ca explose)
aussi grille verticale definie dans domain_cfg différente que dans 3.6, qu’est-ce que ça change ? test dans MAA007, diff des mesh mask 

## Vendredi 26 juillet 2019

smooth init ne change pas grand chose, toujours explosion
test : avec la glace et avec viscosité plus forte (j’ai donc enlevé ubs pour le départ)

## Mardi 23 juillet 2019

dans l’état initial de temp et alt quelques points chelous après interpolation par sosie, ca doit être ça qui fout le bordel ! (comparer aux fichiers GS24 c’est flagrant)

test du smooth_out dans sosie : 

## Lundi 22 juillet 2019

Ca explose quel que soit les pas de temps (même 6 secondes !)
Plutôt dans le Gulf Stream pas loin de l’île cheloue en arc de cercle

Petit bug dans les run-offs pas les bons indices pour le coupage, ok

On dirait que les vitesses initiales ont une sale gueule, je compare les output.init avec GS24 qui tourne

Test nouvelle version de NEMO qui va avec la  nouvelle version du DCM, version xios qui va avec -> done et toujours l’explosion !! 