#  Transforming SSH 1h NATL60-CJM165 into zarr


Mardi 30 avril 2019

Problème avec le time_counter, dans les attrs du zarr pour cette variable, le point de départ varie pour tous les mois donc dans les valeurs on a les heures depuis le début du mois et le début du mois qui change donc quand c’est transformé en datetime ca fait comme si tous les mois étaient le mois d’octobre 2012 alors que non (dans ssh les valeurs changent bien)

Il faut garder l’attribut hours since 2012-10-01 00h30 dans tous les zarrs
-> pour cela peut-etre la bonne méthode est de vider time_counter dans le fichier final et de le remplacer par le bon, obtenu en zarrifiant le time_counter de toute la période


Lundi 29 avril 2019

Stratégie de chunking selon les calculs :
	* 1mois x 2deg x 2deg pour diag freq/wave
	* 1h x tout en space pour plot 2D : moins d’1h à construire
	* tout en tps(1mois forcément) x 10 x 10 pour filtrage temporel

Jeudi 25 avril 2019

Sur la machine visu, en utilisant le script [pangeo-visu-occigen/make_zarr_NATL60_1h_visu_loop.py at master · auraoupa/pangeo-visu-occigen · GitHub](https://github.com/auraoupa/pangeo-visu-occigen/blob/master/make_zarr_NATL60_1h_visu_loop.py), construction du zarr mois par mois, 426G de données au départ, un zarr de 295G !

Reflexion sur les chunks :

Pour le transfert vers le cloud, depuis mon pc linux 
`gcloud auth login` qui ouvre une fenetre firefox pour me connecter à mon compte google
`gcloud init` mon projet est pangeo-181919, la région est US-CENTRAL1
puis pour uploader les données qq chose comme :
`gsutil -m scp -r albert7a@occigen.cines.fr:/store/albert7a/NATL60/NATL60-CJM165-S/1h/SSH/NATL60-CJM165-SSH-1h gs://pangeo-data/`


Mardi 16 avril 2019

Les infos sur le site pangeo :
[Pangeo and Data — Pangeo  documentation](https://pangeo.io/data.html#guide-to-preparing-cloud-optimized-data)


Récap de ce qui a été fait :

le 26 oct. 2018 : sur cal1, ouverture des SSH 1h ok après avoir corrigé les nav_lat, nav_lon, mais construction du zarr pas possible (memory leak, worker crash)

le 31 octobre 2018 : zarr sur occigen, bug : `module 'zarr' has no attribute 'Blosc`, réinstallation modules zarr et numcodecs avec pkgs directement issus de cal1 où ça marche + matplotlib -> depassement du worker memory limit
