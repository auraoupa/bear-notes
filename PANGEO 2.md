# PANGEO 
#pangeo #zarr #cloud

- [ ] apprendre a se servir de binder pour partager les notebooks !!


- [ ] construction du zarr à uploader sur le cloud
- [ ] check github xiaolong pour script et notebook
- [ ] machine visu cines deploiement de jupyter notebook et dask dashboard

24 avril 2019
test de la machine visu avec du ipython pour zarrifier les données :
pas possible de juste loader les données malgré les 8 coeurs et 48 coeurs …

zarr par partie ? [Continuously extending Zarr datasets – pangeo – Medium](https://medium.com/pangeo/continuously-extending-zarr-datasets-c54fbad3967d)



20 mars 2019
nouvel endroit pour accéder aux données du cloud : staging.ocean.pangeo.io avec identification ORCID (mdp M1rentx88)

16 nov. 2018
Hier meeting avec gens de Brest pour savoir où ils en sont.
Leur système est opérationnel ils font de la science sur la machine du CNES HAL avec. 
Nicolas Grima fait des tests de performances sur le rechunking des données
30 oct. 2018

sur occigen : dans pangeo/make_zarr.ksh

26 oct. 2018

sur cal1, ouverture des SSH 1h ok après avoir corrigé les nav_lat, nav_lon, mais construction du zarr pas possible (memory leak, worker crash)