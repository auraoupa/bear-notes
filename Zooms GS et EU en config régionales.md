# Zooms GS et EU en config régionales

- [ ] tout préparer pour le 1/36° avec Pedro [CMEMS-simus/2019-04-15-AA-setting-up-regional-configs-from-NACHOS12.ipynb at master · auraoupa/CMEMS-simus · GitHub](https://github.com/auraoupa/CMEMS-simus/blob/master/Regional_zooms/2019-04-15-AA-setting-up-regional-configs-from-NACHOS12.ipynb), new version [CMEMS-simus-regionales/2019-04-15-AA-setting-up-regional-configs-from-NACHOS12.ipynb at master · auraoupa/CMEMS-simus-regionales · GitHub](https://github.com/auraoupa/CMEMS-simus-regionales/blob/master/prep/2019-04-15-AA-setting-up-regional-configs-from-NACHOS12.ipynb)
- [ ] relancer tout pour GS36
	- [ ] coordinates
	- [ ] bathy
	- [ ] domain_cfg
	- [ ] runoff
	- [ ] ini
	- [ ] bdy
	- [ ] weights
	- [ ] autres fichiers ?
	- [ ] 150 niveaux ?


- [x] check bathys pour voir si c’est ok pour config régionale -> bof
- [x] construire bdy à partir du run en 4.0
- [x] tous les fichiers 1_ renommés
- [x] test GS au 1/24°
	- [x] run MAA004 -> explose à kt=1159
	- [x] rebuild XIOS.ABORT
	- [x] améliorer un peu la bathy avec bmgtools
	- [x] check précisément accord bathy et bdy -> les nan au Nord c’est vraiment moche
	- [x] enlever les nan avec ncap2
	- [x] debug précisément avec print et tout …`
	- [x] sortir les vitesses au pas de temps
	- [x] recommencer sosie avec cible = les bdy au lieu du domaine 3D entier
	- [x] test  avec bdy=ini  -> idem !!
	- [x] essayer new DCM -> idem
	- [x] ini from GLORYS
	- [x] ini from NACHOS avec tmask et non missing_value -> c’est déjà le cas
	- [x] test bathy rabotée
	- [x] refaire toute la cote avec bmg tools
	- [x] faire les runoffs from scratch ! : [GitHub - molines/eNATL60](https://github.com/molines/eNATL60)
		- [x] test -> youhou ca marche !!
		- [x] rajouter les bdy -> ca tourne toujours !!
		- [x] ecrire les restarts
- [x] comparer NACHOS12 et GS24 1mois
	- [x] mean GS24
	- [x] monitor GS24
	- [x] monitor month MAA4001
	- [x] extract GS in MAA4001
	- [x] plot compare
	
Lundi 15 avril 2019

1 mois de GS24 bien recombinés, bonne tête des sorties …
GS24 3x + CPU que NACHOS12 alors que 3X - de points de grille et dt seulement 2x +
à cause de bdy 1d au lieu de 1m ?


26 mars 2019

En enlevant les ini de glace, plus explosion à kt=4 avec gros patch de nan mais explosion à kt=44, salinité > 100 en un point près de la cote à z=6m de profondeur -> je rabote la bathy !

25 mars 2019

Problèmes xios avec la version de NEMO 10650 : il suffit de rajouter fasticepres dans field_ice.xml en fait …


19 mars 2019
petit bug c’était pas la bonne bathy dans le nouveau domain_cfg, à refaire avec aussi les sorties au pas de pas dans un fichier par pas de temps

quand la bathy change le découpage aussi !

13 mars 2019
plus de bugs bdy à cause d’un bdy ponctuel mais des NaN qui se propagent
test avec des bdy fabriqués avec sosie (l’interpolation a l’air un peu mieux en profondeur) -> MAA004


11 mars 2019

j’ai permuté les dimensions x et y dans les bdy Ebdy
pb fldread : «Subscript #2 of the array DTA_READ has value 595 which is greater than the upper bound of 20 »

test sans Ebdy pour voir ça vient de celle-là ? MAA003 -> pas possible c’est pas fermé du coup

25 févr. 2019

pour faire les bdy au 1/24° on passe par les nesting tools ? non c pas top
sosie plutot ? idem finalement mais bcp + long !

donc nesting tools it is …

5 mars 2019

compilation de la version 10650 du code NEMO ne marche pas …
je repasse en 4.0_beta, la version qui avait marché pour le run NACHOS12.L75-MAA4001 -> GS24.L75-MAA002

les bdy journaliers sont en cours, même si les nesting tools sont plus rapides que sosie, ca reste long …

le test sera fait avec un mois de bdy