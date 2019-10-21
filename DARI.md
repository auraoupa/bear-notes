# DARI

bilan 2018-2019

Evolution résolution kilométrique

Stratégie de simulations

Mise en place nouvelle version de NEMO (release juillet 2018 mais instabilité, on doit suivre les derniers developpements pour que ça marche …)
AGRIF et changement de grille verticale pas encore disponible dans version récente de NEMO, on choisit de faire des configurations régionales forcées aux frontières par la simu NACHOS12 de référence. Nouvel objectif CMEMS : sensibilité à la grille verticale, nombre de niveaux et répartition.
Les mêmes régions : Gulf Stream (GS) et côte Europe (EU)

Coût calcul des simulations

- NACHOS12.L75 : 1609x1568x75, rdt=360, (NEMO4.0 + vvl) 20 000h CPU/an
- GS24.L75 : 1138x676x75, rdt=180, (NEMO4.0 + vvl) 38 000h CPU/an
- GS36.L75 (config en developpement) : 1468x950x75, rdt cible=90/120, (NEMO4.0 + no vvl) ~60 000 CPU/an
- GS36.L150 (config à developper) : 1468x950x150, rdt cible=90/120, (NEMO4.0 + no vvl) ~120 000 CPU/an
- GS36.L300 (config à developper) : 1468x950x300, rdt cible=90/120, (NEMO4.0 + no vvl) ~240 000 CPU/an
- EU36.L75 (config à developper) : demander à Pedro
- EU36.L150 (config à developper) : demander à Pedro
- EU36.L300 (config à developper) : demander à Pedro


Simulations effectuées en 2019 :

- développement et production 4 ans NACHOS12 avec nouvelle version code NEMO : ~180 000h CPU
- développement et production 1 an zoom GS 1/24° : ~60 000h CPU
- développement zoom GS 1/36° (en cours) : ~30 000h CPU


Estimations pour Julien

		- [x] diag w’b’ tout eNATL60 
		- [x] filtrage spatial 
		- [x] filtrage temporel classique
		- [ ] filtrage temporel lagrangien
			- [x] mail Andy
		- [x] zarrification
		- [ ] x-batcher


résultats unitaires :
		- [ ] filtrage 2D 1 champs 2D eNATL60 24h: 14min elapsed,  10 noeuds, CPU = 30min*240
		- [ ] filtrage temporel 1 champs 2D eNATL60 24h: 3 min elapsed, 10 noeuds, CPU = 30min*240
		- [ ] profils wprimebprime in 9 box 2x2, 10 noeuds,  elapsed 30minx240
		- [ ] zarr 1 champs 2D 1month : 11min elapsed
		- [ ] zarr 1 champs 3D 1 day :  18min elapsed
	
réponse à Julien :

opération | elapsed time | nombre de coeurs | total CPU
 
