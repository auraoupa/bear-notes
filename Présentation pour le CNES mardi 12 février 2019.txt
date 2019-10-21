# Présentation pour le CNES mardi 12 février 2019
on recommence …
plus concise,  directe

1-titre : bonjour à tous, je suis aurélie albert ingénieur de recherche dans l’équipe MEOM, je vais vous parler maintenant des activités NEMO haute résolution pour l’opérationnel qui ont eu lieu dans l’équipe et plus particulièrement dans le cadre d’un projet de R&D du CMEMS 
ce projet nous a permis d’étudier très précisément les fines échelles dans la simulation NATL60 qui sert à de nombreuses études en relation avec la future mission SWOT

2-projet : ce projet a pour but de contribuer à l’amélioration des systèmes opérationnels opérés par MERCATOR dans la mission copernicus et MEOM  apporte ici son expertise des runs à très haute résolution et des approches probabiliste. Je vais vous parler plus particulièrement  du travail que l’on a fait sur les fines échelles.

3 : ce qui a motivé ce projet c’est le retour des utilisateurs des produits de Mercator qui demandent plus de fines échelles  (inférieures à 100km) dans un monde où les ressources en calcul ne sont pas illimitées il y a des choix à faire et des compromis à trouver
on peut également envisager que à terme Mercator voudra assimiler dans son système de prévision les données fines échelles issues de l’altimétrie, il faudra donc que le système de modélisation soit capable de simuler ces fines échelles

on a proposé donc tout d’abord d’établir des critères qui permettent de dire si un modèle représente correctement les fines échelles, c’est la partie diagnostics
et ensuite on définit un banc d’essai pour définir les meilleurs choix que l’on qualifiera à l’aide de ces metriques

4 : les métriques proposées ont été mises en place sur la simulation NATL60 et sont de 2 types : lors de la comparaison du modèle avec un jeu d’observation une approche statistique est menée car il y a peu de chances que la variabilité synoptique du modèle soit en phase avec celle des obs donc on fait une hypothèse d’ergodicité et on compare par exemple 

5 : un profil avec un ensemble de profils du modèle que l’on définit par des statistiques simples : la moyenne et les percentiles 10 et 90. on répète cette opération pour chaque profil et pour plus de lisibilité on moyenne dans ces boîtes

6 : le résultat pour les profils de température 
7 : et de salinité
on observe alors un très bon comportement du modèle et même en profondeur

8: dans une autre catégorie de diagnostic, on s’interesse à la comparaison fines échelles/large échelle dans la répartition des energies cinétiques en surface grâce à un filtre spatial qui nous permet de séparer les échelles. on observe alors une forte saisonalité dans cette répartition avec des fines échelles qui l’emporte surtout en hiver et dans le nord du bassin

9: c’étaient 2 exemples parmi tout un catalogue de métriques que l’on a mis en place et qui s’interesse entre autres à l’intensité des fines échelle, leur taille, leurs interactions avec les échelles plus grandes

10: tous ces dvp ont été regroupés dans une toolbox qui est disponible à tous via github. Pour chaque métrique on apporte une définition , une liste d’étapes necessaires à son calcul les références des librairies ou logiciels utiles et enfin le calcul en lui-même et son illustration tout cela dans un seul document de type jupyter notebook

11: un petit mot au passage sur l’optimisation des calculs, étant donné la quantité de données que représente la simulation et la durée de certaines étapes de calcul il a fallu essayer d’être effiace au maximum. Pour cela les methodes proposées par la communauté pangeo qui réfléchit beaucoup au passage à l’échelle des calculs ont été très utiles et utilisées.

12: maintenant que ces métriques sont définies, elles vont nous servir à déterminer les meilleurs choix de modélisation dynamique dans une configuration test, qui reprend les caractéristiques du système de prévision actuel de Mercator. un banc d’essai pour des tests de sensibilités va être mis en place grâce à 2 zooms dans 2 régions à la dynamique contrastée

13: ces tests vont se focaliser principalement sur la résolution verticale et la distribution des niveaux verticaux associées à une réosuktion horizontale cible de 1/36°

14: voilà donc dans le cadre d’un projet CMEMS comment on a pu étudier de très près (à la loupe) les fines échelles dans le run NATL60 qui est une référence maintenant pour les études spatiales



1er slide :

bonjour à tous, je vais vous parler maintenant des activités NEMO haute résolution pour l’opérationnel qui ont eu lieu dans l’équipe MEOM et plus particulièrement dans le cadre du projet CMES GLO-HR pour global high resolution

2e slide :

c’est un projet auquel participe une bonne partie de l’équipe MEOM et qui a pour objet de contribuer à l’amélioration des systèmes opérationnels opérés par MERCATOR en proposant 3 axes : 1 partie amélioration des prévisions physico-biogéochimiques, 1 partie sur les produits opérationnels probabilistes et une partie échanges de codes, de configurations entre MEOM et Mercator, voir entre Mercator et ses partenaires

j’ai essentiellement contribué au le 1er axe, et plus précisément sur la partie dynamique et je pense que Stéphanie vous parlera plus tard de la partie probabiliste

3e slide

ce qui a motivé ce projet c’est le retour des utilisateurs des produits de Mercator qui demandent plus de fines échelles  (inférieures à 100km) dans un monde où les ressources en calcul ne sont pas illimitées il y a des choix à faire et des compromis à trouver
MEOM a proposé à Mercator de travailler sur la partie modèle libre à fines échelles, étant donné l’expérience de l’équipe dans ce domaine
on a proposé donc tout d’abord d’établir des critères qui permettent de dire si un modèle représente correctement les fines échelles, c’est la partie diagnostics
et ensuite une série de tests de sensibilités à la résolution horizontale, verticale dans un cadre atlantique nord

4e slide
tout d’abord les métriques qui évaluent les fines échelles dans les modèles 