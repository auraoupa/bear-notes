# Abstract for EGU

- plusieurs elements poussent evolution des system operationel vers résolution effective de la mesoechelle. Typiquement 1/36° : future wide swath altimetry, user requirements. But :  meilleures courant et propriétés de surface. 

- not only a matter of resolution : mais beaucoup de choix possibles : schema, grille verticale, besoin de rationaliser. experience de sensibilité et métriques. 

- Mais attention il faut de métrique adaptée à échelle fine <100km et au modele libre. 

	- Ici : on présente une suite de diagnostique fine echelle adaptée à fine mes et submeso pour évaluation des run libres. Et adaptation evaluation des sortie de modele libre dans le cas HR. Packagée en toolbox. 

- On montrera résultat basé sur north atlantic 1/60° et systeme de resolution typique des systeme operationel globaux actuel. (1/12°) (rester flou sur les simulation exactes) 

- We will also discuss the practical implementation through Jupyter notebooks et possible evolution de la toolbox d’evaluation. Scalability des outils. 


Title : Lupa :  A series of ocean model inter-comparison metrics for assessing the sensitivity of resolved fine scales for designing future global prediction systems.

Authors : Aurélie Albert, Julien Le Sommer, Thierry Penduff, Jean-Marc Molines, Bernard Barnier, Laurent Brodeau
  

Several factors are pushing the evolution of global operational oceanography towards an effective mesoscale-resolving spatial resolution, typically 1/36° : users of ocean products provided by CMEMS seek fine scales, between 10 and 100km (User uptake, Service Evolution CMEMS Workshop, 2015) and the future SWOT SAR-interferometry wide-swath altimeter mission is designed to provide global SSH data resolving spatial scales down to 15-20km (Fu et Ubelmann, 2014). By explicitely resolving mesoscale we aim at providing a more accurate representation of the state and variability of global currents and surface properties of the ocean.

Upgrading the operational systems to the mesoscale resolving stage is not only a matter of spatial resolution, some other choices are to be made alongside, concerning physical and numerical schemes and also vertical grids. Sensitivity tests and indicators suited to fine scales must therefore be designed in order to rationalize these choices.

Here, we propose a suite of diagnostics fitted to the fine scales that will evaluate free runs and also an adaptation of large scale evaluations versus observations adapted to high resolution runs. This suite of metrics is written in python and fortran and is packaged in a toolbox called Lupa.

We will show results of this toolbox applied to a very high resolution (1/60°) North Atlantic simulation and a simulation with spatial resolution comparable to current operational systems (1/12°). We will also discuss the practical implementation through Jupyter notebooks and the possible evolution of the Lupa toolbox in terms of scalability.