# Diags wave w Andy

- [ ] bottom velocities 
- [ ] bathymetry
- [ ] refaire pdf & wavenumber freq diag à 200m
- [ ] EP flux profiles for big region


- [x] pdf of surface vorticity and strain, tide vs notide
	- [x] extract U V surf y2009m07d10-y2009m08d18 eNATL60 BLBT02
	- [x] extract U V surf y2009m07d10-y2009m08d18 eNATL60 BLB002
	- [x] calcul vorticity
		- [x] tide
		- [x] notide
	- [x] calcul strain
		- [x] tide
		- [x] notide
	- [x] calcul KE
		- [x] tide
		- [x] notide
	- [x] diag freq/wavenumber de la KE 
		- [x] tide
		- [x] notide
	- [x] filtrage temporel à 0.9f
		- [x] combien vaut f dans la région : entre 5.7 et 9.4 e-5
		- [x] check Guillaume tuto
		- [x] test filt sur U surf tide
		- [x] check plot temporel en 1 point
		- [x] filt U surf notide
		- [x] filt V surf
			- [x] tide
			- [x] notide
		- [x] calcul KE filt 
			- [x] tide
			- [x] notide
		- [x] diag freq/wave Ke filt
			- [x] tide
			- [x] notide

- [x] mail Callum

- [x] precise f in the box
- [ ] refaire pdf avec nouveau filtre

- [ ] extraction on ACO 10/07-09/08 U V W T S  Z 3D -> c’est bcp trop lent et ça ne finit pas toujours sur occigen (pb mémoire en job …) -> c ok sur le noeud de visu


	- [ ] mean over region and plot vertical profiles

- [ ] eNATL60 bottom u, v
	- [ ] 1 month average

- [ ] box Gulf Stream


effect worth parametrizing in no tides high resolution models ?
show it with currentmeter data ? intensification of a strong zonal flow