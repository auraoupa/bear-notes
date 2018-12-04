# Récap du mercredi 31 octobre


* simus :
- [x] automatiser sosie pour init
- [ ] automatiser sosie pour bdy
- [x] test xios dev olga 
	- [x] debug ->
- [x] test nemo4.0_rev_10230
- [ ] MAA40noeliminit avec init sosie ->


* Pangeo
- [x] SSH 1h bon nav sur mon store
- [ ] zarr SSH 1h NATL60 sur occigen

nemo4.0_rev_10230 avec xios2.0_rev_1499 -> meme erreur xios sur les masks

xios dev olga, tout bien prendre de MAA40noelim pour écriture des restarts au bon endroit, forcage atm slp, etc … -> ca marche !! on va partir la dessus du coup !!

zarr sur occigen, bug : `module 'zarr' has no attribute 'Blosc`, réinstallation modules zarr et numcodecs avec pkgs directement issus de cal1 où ça marche + matplotlib -> depassement du worker memory limit