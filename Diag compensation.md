# Diag compensation

## Vendredi 20 septembre 2019
Plots enfin finalisés :

		- [diag-turner-angle/2019-09-18-AA-polar-proj-phi-turner-angle-norm-NATL60-boxes-m03-09-1d-from-file-on-occigen.ipynb at master · auraoupa/diag-turner-angle · GitHub](https://github.com/auraoupa/diag-turner-angle/blob/master/2019-09-18-AA-polar-proj-phi-turner-angle-norm-NATL60-boxes-m03-09-1d-from-file-on-occigen.ipynb)
		- [diag-turner-angle/2019-09-18-AA-hist-turner-angle-complex-norm-NATL60-boxes-m03-09-1d-from-file-on-occigen.ipynb at master · auraoupa/diag-turner-angle · GitHub](https://github.com/auraoupa/diag-turner-angle/blob/master/2019-09-18-AA-hist-turner-angle-complex-norm-NATL60-boxes-m03-09-1d-from-file-on-occigen.ipynb)
		- [diag-turner-angle/2019-09-19-AA-hist-grad-buoy-spice-NATL60-boxes-m03-09-1d-from-file-on-occigen.ipynb at master · auraoupa/diag-turner-angle · GitHub](https://github.com/auraoupa/diag-turner-angle/blob/master/2019-09-19-AA-hist-grad-buoy-spice-NATL60-boxes-m03-09-1d-from-file-on-occigen.ipynb)

## Mardi 17 septembre 2019
beaucoup de changements !
beaucoup de tatonnements pour trouver la bonne facon de faire le plot en rose des vents : en fait pas du tout rose des vents mais plutot un plot polaire avec fabrication à la main des pdf pour chaque secteur du cercle

préprocessing en place sur occigen mais il faut refaire car le ratio pas normé : il faut également calculer alpha et beta pour que le ratio de gradient soit logique (si =1 n’était pas un bon critère sinon)

rajouter des pdfs de quasi buoyancy et quasi spicyness

## Mercredi 11 septembre 2019
notebook création du plot de pdf conjointe magnitude et angle sur une journée de données
repo github : diag-turner-angle
il faut masker

## Mardi 10 septembre 2019
Nouvelles refs : 
**Joint pdf of the complex ratio** fig 1 de Ferarri and Paparella 2003 : [http://ferrari.mit.edu/wp-content/uploads/publications/FerrariPaparellaJPO03.pdf](http://ferrari.mit.edu/wp-content/uploads/publications/FerrariPaparellaJPO03.pdf) (edited)

 [4:33 PM](https://meom-group.slack.com/archives/D71RDTQ20/p1568125990000800) 
**pdf of Turner angle** : fig 3 and Fig 6de Ferrarri and Rudnik 2001 : [http://ferrari.mit.edu/wp-content/uploads/publications/FerrariRudnick00.pdf](http://ferrari.mit.edu/wp-content/uploads/publications/FerrariRudnick00.pdf) (edited)
 [4:34 PM](https://meom-group.slack.com/archives/D71RDTQ20/p1568126060001200) 
**Joint pdf of T, S gradients** : plate 8 de Ferrari and Rudnik 2001 : [http://ferrari.mit.edu/wp-content/uploads/publications/FerrariRudnick00.pdf](http://ferrari.mit.edu/wp-content/uploads/publications/FerrariRudnick00.pdf) (edited)

variabilité de la compensation : see : [https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2014JC010455](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1002/2014JC010455) 

focus sur les 3 boîtes définies dans les diags TSG et surtout ACO
contraste mars vs septembre

Récap des épisodes précédents

ref :  [http://www.soest.hawaii.edu/PubServices/2001pdfs/Ferrari.pdf](http://www.soest.hawaii.edu/PubServices/2001pdfs/Ferrari.pdf) 

dans le rapport : R≡ (T x + iT y) /(S x + iS y)

turner angle
Intensité de la compensation des gradient T,S
On définit l’angle en chaque point. On trace des stat dans des boites.
Distribution de l’angle dans chaque boite.
Une carte de la valeur de l’angle en fonction de l’espace et du temps.

les données nécessaires :

gradients horizontaux de surface T et S ?