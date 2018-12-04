# Récap du lundi 15 octobre
 #debug #NEMO #NEMO4.0_beta# 

Problème d’écriture des restants, pas dans le bon répertoire, motifs de domain.F90 et icestp.F90

⌦ relance

#diag TSG##binning#

Problème MemoryError pour le binning des gradients filtrés pour les saisons : en séparant temporellement c’est pas bon on perd le côté médiane dans un bin. Il vaut mieux parallèliser selon les bins  mais alors comment 