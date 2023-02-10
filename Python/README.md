DSIA_4101A
=========================================================================================================

Guide d'utilisateur :

Pour creer et visualiser le dashboard, il suffit d'executer Main.py, ce qui peut prendre quelques dizaines de secondes. Ensuite, copier coller l'adresse apparaissant dans le terminal dans un navigateur internet. L'affichage peut également prendre un certain temps.

Le dashboard donne acces a 10 cartes interactives, accessibles depuis un menu deroulant. La legende est visible a gauche pour la carte regroupant toutes les filieres. Cliquer sur un point de la carte donne acces a la puissance maximale installee par installation presenete sur le site. 

 L'histogramme est visible en-dessous. 

=========================================================================================================

Fichier Carte.py : 

Utilise les donnees de carte.csv, folium et pandas. Cree une carte du monde incluant toutes les filieres de production / stockage electrique en France, puis une carte par filiere. Sauvegarde chaque carte en html. 

Fichier Histogramme.py : 

Utilise les donnees de Data.csv, pyplot, pandas et warnings. Cree un histogramme du nombre d'installations de production d'énergie nucléaire par puissance max installee. 

Fichier Main.py : 

Utilise dash, pandas, PIL, SortData, Carte, Histogramme afin de creer le dashboard. On importe les 3 autres fichiers, ce qui permet de les executer, de creer la carte et l'histogramme depuis le dashboard.
Le dashboard est ensuite accessible en local host, a l'adresse indiquee dans le terminal. 

Fichier SortData.py : 

Utilise numpy, pandas et csv. Lit, nettoie et traite les fichiers Data.csv et geo.csv afin de fournir les csv carte.csv et histogramme.csv aux fichiers du même nom. 

=========================================================================================================

Journal de developpement : 

Changelog : 26/10/2022

Fichier SortData.py : 
Creation d'un dataframe utilisant pandas
Correction d'un probleme du a un nombre inegal de colonnes
Passage d'un separateur ; a un separateur ,
Tri des colonnes selon leur pertinence, 26 seront conservees sur les 47 originales

Changelog : 30/10/2022

Implementation de Geo.csv et de merge data

Fichier SortData.py : 
Normalisation des codes communes INSEE afin de les utiliser pour la geolocalisation
Exploitation des codes INSEE des communes pour obtenir latitude et longitude
Creation d'une dataframe avec les donnees geographiques

Changelog : 31/10/2022

Fichier SortData.py :
Idee de reperer les lignes dupliquees, objectif : 1 seule ligne par code commune INSEE
Necessite de denombrer les lignes dupliquees, afin d'obtenir le nb d'installations par commune
Creation d'un attribut count dans le dataframe dfdatageo qui compte le nombre d'apparitions de chaque code insee commune dans le dataframe.
Drop les lignes dupliquees, pour n'avoir qu'une seule ligne par commune, gardant le nombre de fois qu'elle a ete referencee dans le csv de base. 
Passage de 94485 lignes a 20495 dans dfdatageo. 
Creation du dataframe dfcarte prenant en compte le code insee commune, la latitude, la longitude, l'attribut count et la filiere de l'installation afin de pouvoir l'utiliser en tant que carte de repartition des differentes installations en fonction des filieres en France. 
Nouveau changement : Suppression de 4 lignes dans dfdatageo qui avaient des NaN pour latitude et longitude, donc pas exploitables pour la carte
Creation du csv carte.csv a partir du dataframe dfcarte. 

Creation de carte.py : 
Import de folium
Creation d'un dataframe dfloc (pour localisation) qui va lire carte.csv 
Creation d'une map avec folium qui met un point rouge pour chaque localisation donnee par le couple latitude longitude de chaque ligne (chaque commune)
Sauvegarde de cette map en fichier html
Creation d'une fonction color_producer, assignant un code couleur a chaque type d'energie 
Utilisation de la fonction a la creation des points dans folium.Circle

Changelog : 02/11/2022

Creation du dashboard
Modification de la map
Incorporation de la map au dashboard 
Creation de 9 maps et d'un menu deroulant dans le dashboard pour selectionner la filiere que l'on souhaite afficher 
Creation de l'histogramme sur le nucleaire et d'un bar chart 
Amelioration de la lisibilite du code
Maintenance electrique annuelle de l'ecole, impossible d'acceder aux contenus

Changelog : 04/11/2022

Modification du dashboard afin d'y integrer l'histogramme. Echec. 

Changelog : 05/11/2022

Modification du dashboard afin d'y integrer l'histogramme. Reussite. 
Tentative de centralisation de l'execution par le fichier main. Impossible d'acceder au dashboard ainsi. Besoin de plus d'attention. 

Changelog : 06/11/2022 

Dashboard.py est devenu le main, facilitation d'execution pour tout le programme. 
Nettoyage approfondi du code, simplification, clarification des commentaires. 
Changement de taille de la carte sur le dashboard
Ajout de messages affiches dans le terminal pour donner des indications sur la progression d'execution du programme
Problème rencontré : Les messages s'affichent en boucle à cause de l'actualisation continue.
Solution : Suppression, au moins temporaire, des messages.

