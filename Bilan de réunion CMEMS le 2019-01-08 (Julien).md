# Bilan de réunion CMEMS le 2019-01-08 (Julien)



## Bilan de discussion fin novembre à Mercator Ocean

**- verifier accès gitlab et lien dans le rapport.**
- (+rescan des diags sur gitlab et update des manquants si besoin.) 

**- banc de test : cible zoom dispo pour fin janvier.**
 
- interaction autour stage M2R : 
**- visite Aurélie pour PANGEO**
	- visite de l’étudiant au printemps en debut de stage
- on prépare plan d’expériences au 1/36° : optimisation grille verticale. 
- pour le plan d’experiences : proposition fermeture et run 1/24 illustratif
- une discussion avant fin décembre pour caller la proposition. 
 
 
 
## informations  

- arrivée Pedro : 1 mars
- bascule Ocean Next.  : en octobre. 
- plan d’experience : centré sur 1/36° choix de niveau verticaux, une simulation 1/24° pour illustration
 
 
## statut des simulations 
- un os : elimination des proc terre avec les zoom 
- run ok sans zoom. evaluation en cours
 
 
## Priorité 

Mettre en place banc de simulation
  Timing ideal : 28/01
  Timing wcs : 1/03
 
 Preparer le plan de simulation 
 
 Puis discussion avec MO
 
 Implementation avec Pedro : production / analyse.  À decider en mars à son arrivée. 
 Le plus efficace sera sans doute : 
- Production : Pedro
- Chaine de traitement : Aurélie 
- Analyse et interpretation : à deux. 
 
 Concernant les diags : poursuivre compensation T, S quand le systeme tournera. 
  
  
 ## plan de simulation 
 
 On peut commencer à remplir le rapport 
 
1. Choix de schema au 1/36°
 Identifier les possibles choix (advection de traceurs et fermeture)
 
2. Choix de resolution verticale au 1/36°
 75 versus 100 versus 150
 Réflechir à comment les répartir.  
	- L75 : distribution actuelle
	- L100 : deux scenario : par exemple 33% des niveaux NATL60
	- L150  : deux scenario : par exemple 50% NATL60
 
 Quantifier combien de simulation on peut se permettre.  
 
3. Illustration du gain versus 1/24° 
  1/24° L75 et 1/24° Lcible avec la disposition décidé
  
  
  
## abstract : 
Discussion un abstract diagnostics fine echelle pour EGU
  
 oral. 
 
Title : XXX :  A series of ocean model inter-comparison metrics for assessing the sensitivity of resolved fine scales for designing future global prediction systems
  

- plusieurs elements poussent evolution des system operationel vers résolution effective de la mesoechelle. Typiquement 1/36° : future wide swath altimetry, user requirements. But :  meilleures courant et propriétés de surface. 

- not only a matter of resolution : mais beaucoup de choix possibles : schema, grille verticale, besoin de rationaliser. experience de sensibilité et métriques. 

- Mais attention il faut de métrique adaptée à échelle fine <100km et au modele libre. 

	- Ici : on présente une suite de diagnostique fine echelle adaptée à fine mes et submeso pour évaluation des run libres. Et adaptation evaluation des sortie de modele libre dans le cas HR. Packagée en toolbox. 

- On montrera résultat basé sur north atlantic 1/60° et systeme de resolution typique des systeme operationel globaux actuel. (1/12°) (rester flou sur les simulation exactes) 

- We will also discuss the practical implementation through Jupyter notebooks et possible evolution de la toolbox d’evaluation. Scalability des outils. 


  

 ## decision : 

0. abstract pour EGU. 
Ouverture un google doc à Laurent, JMM, TP, BB, JLS
 
1. Simulations : 
	- evaluation rapide du run 1/12°
	- preparer les zooms pour v4.0 
	- interagir avec Jerome pour elimination des proc terre
	- des que ca tourne : organiser discussion Mercator. 1ere quinzaine de février. (Verifier les vacances scolaire Toulouse et Grenoble) idéalement semaine du 28/01 ou semaine du 4/02. But convenir du plan de test et des modalité de transfert des diags

2. Plan de simulation 
	- organiser réunion de preparation du plan de simulation : réunion interne avec JMM, LB, BB, TP semaine du 28. 

3. outreach
	- verifier avec Marie si stagiaire
 
4. Durant réunion avec mercaror.  
	- organiser visite Toulouse (durant réunion avec Mercator)
	- organiser une discussion pour caller les test 
 

—
Julien Le Sommer
Research Scientist
IGE/MEOM group
   [http://lesommer.github.io/](http://lesommer.github.io/)  [http://meom-group.github.io/](http://meom-group.github.io/) 