# Semaine du 16 au 20 september 2019

## Mardi 17 

Idées :
	- [ ] runs 
		- [x] 	run sur noeuds BDW28
		- [ ] encore moins de procs : 10 noeuds  r94
		- [ ] dépeupler : 20 noeuds à moitié r93
		- [ ] enlever les liens de liens
		- [ ] bdy=init -> ca marche, faire un an ?
	- [ ] diag
		- [ ] données horaires sur 15 jours
c’était pas la bonne variable que je plottais, phi et tu et non r et tu…

après réunion avec Julien :
	- [x] rajouter alpha et beta dans le calcul de R
	- [x] sauver quasi buoyancy et quasi spicyness
	- [ ] refaire histogrammes
	- [ ] histogrammes buoy et spice
	- [ ] refaire polar plot + autres régions

Avant de partir :
		- [ ] 	lancer extractions Sammy
			- [ ] attente réponse pour taille région
		- [x]  répondre à Anna

## Mercredi 18

Dans l’ordre :
		- [ ] diags tout beau pour rapport
		- [ ] rapport
		- [ ] simus on continue le debug
		- [ ] profils Anna

### diag Turner angle		
- [ ] process new phi, tu + buoy, spice
- [ ] histogrammes
- [ ] polar plot
- [ ] figures in rapport
- [ ] texte in rapport

### simus
- [ ] rajouter les bdy a la place du init petit a petit
- [ ] bdy from glorys
- [ ] bdy from another nachos

## Vendredi 20

J’ai compris un truc : pb dans la reconstruction des fichiers horaires Tsurf , dedans il y a aussi ssu et ssv, donc un x_gridU etc… pas de x et y du coup le programme de reconstruction est perdu !!
-> séparer les outputs horaires de surface selon les grilles !!

