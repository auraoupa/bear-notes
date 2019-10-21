# Les simus NACHOS12.L75

- [ ] run NACHOS12.L75 2010-2013 NEMO version 4.0 (rev 10089)
	- [x] NACHOS12.L75-MAA4001 2010 ok (a part que 2011 est une copie de 2010)
	- [x] NACHOS12.L75 MAA4002 2011-2013 ok
	- [x] mail à l’équipe pour discuter des diffs
	
		
	- [ ] un run tout d’un coup ? MAA003 avec autres apports peut etre …
	

MAA4002 : suite de MAA4001, de 2011 à 2013, les restarts sont reconstruits puis copiés dans le TMPDIR

MAA4001 : première simu qui tourne avec le code NEMO4.0 de juillet 2018, 1 an  de simu exploitable, la 2e année a tourné avec des bdy 2010 dupliqués

PB : 
* est-ce que pour le damping on a 12 mois identiques ou pas ? oui c’est bon, en fait ça a surement été fait dans mk_BDY et non MK_INIT car dans init seulement 201001 …
* les restarts provenant dautres simus ou recombinés en restart-1.nc il faut les mettre dans le dossier simu-RST.1
* noms des restarts trop compliqués, modif drakkar dans restart.F90 et dans icerst.F90 