# Construction bdy et init via sosie 3D
1. installation newest sosie : in `/scratch/cnt0024/hmg2840/albert7a/DEV`, `git clone https://github.com/brodeau/sosie.git sosie-3.0`
2. compilation avec la macro `make.macro_ifort_OCCIGEN2`
3. namelist adéquate


6 nov. 2018
Pour bdy, après sosie, ncks comme il faut dans  `DEV/MK_BDY_GLORYS2NACHOS_SOSIE`

Pour init, enlever les 0 dans GLORYS avec make_vosaline_nozeros.ksh in GLORYS2V4/data/2010 :
`ncap2 -O -s ‘where (vosaline<10) vosaline=9.96921e+36f’ GLORYS2V4_ORCA025_201001_gridS_nozero.nc GLORYS2V4_ORCA025_201001_gridS_nozero.nc`
sosie, puis re-drown pour eliminer les 0 apparus dans sosie ?? dans `DEV/MK_INI_GLORYS2NACHOS_SOSIE`

5 nov. 2018
Des 0 dans le fichier resultat de salinité final car qq uns dans le fichier GLORYS -> les enlever avant de sosifier, dans /scratch/cnt0024/hmg2840/albert7a/GLORYS2V4/data/2010/make_vosaline_nozero.ksh

25 oct. 2018
test GLORYS2V4 -> NACHOS12 erreur à l’éxecution `Error occured in procedure DIMS` à cause de pas de nav_lon, nav_lat dans le fichier coordinates -> je remplace par mask
c’était pas l’erreur que je croyais, il fallait aussi mettre ctype_z_src à z en fait dans la namelist

29 oct. 2018
Segmentation fault après les `treated latitude of target domain`
-> lancer dans un job