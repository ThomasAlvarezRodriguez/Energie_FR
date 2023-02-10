DSIA_4101C
=========================================================================================================

Guide d'utilisateur : 

Pour creer et visualiser le dashboard, il suffit d'executer le fichier app.R depuis Rstudio apres avoir ouvert le projet (DSIA_4101C.Rproj) depuis Rstudio ou l'explorateur de fichiers. 

=========================================================================================================

Fichier app.R : 

Cree le dashboard, l'UI et le serveur en utilisant la librairie Shiny. 
Une meilleure maniere de faire cela aurait ete de le diviser en 3 fichiers, mais au vu de la complexite reduite de notre dashboard, cela serait excessif. 

Fichier Carte.R : 

Utilise les donnees de data_util.csv pour creer la carte en se servant des librairies tidyverse, readr, ggplot2, maps. 
La carte est ensuite sauvegardee dans le dossier www pour etre utilisee par le dashboard. 

Fichier Histo.R :
Utilise et traite les donnees de data_util.csv pour creer l'histogramme en se servant des librairies tidyverse, readr et ggplot2.
Utilise la fonction geom_bar pour creer l'histogramme et non la fonction geo_histogram car jugee trop peu pratique.     
Sauvegarde ensuite l'histogramme dans le dossier www pour etre utilise par le dashboard. 

Fichier SortData.R : 

Lit, traite et fusionne les donnees de Data.csv et Geo.csv afin de retourner data_util.csv, contenant les donnees codeinseecommune, nom_commune, latitude, longitude, filiere, technologie et puismaxinstallee. 
Ce csv est utilise par les fichiers Histo.R et Carte.R. SortData.R utilise la librairie readr pour lire les fichiers csv traites. 

=========================================================================================================

Journal de developpement : 

Changelog : 02/11/2022 

Creation de SortData

Changelog : 04/11/2022

Push de SortData apres reprise de service des serveurs ESIEE

Changelog : 05/11/2022

Debut de recherche sur la creation de l'histogramme
Allegement du code amenant plus de bugs 
Debut de carte

Changelog : 06/11/2022

Creation de la carte et de l'histogramme

Changelog : 10/11/2022

Amelioration de la carte 
Amelioration de l'histogramme

Changelog : 11/11/2022

Creation du dashboard
Amelioration visuelle de l'histogramme
Changement d'echelle de la carte
