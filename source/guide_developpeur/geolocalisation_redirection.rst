.. _geolocalisation_redirection:

########################
Redirection vers openADS
########################

openADS permet la redirection depuis une application externe vers la fiche ou une sélection d’objet. Pour cela il est nécessaire de passer par le script d’entrée à l’application app/web_entry.php.

Accéder à la fiche d'un objet
#############################

L'URL doit être composée des paramètres suivants :

* **obj** objet de l'élément que l'on souhaite visualiser (*dossier_instruction*) ;
* **value** Identifiant de l'objet à chercher.

Exemple d'URL à composer : https://[URL_ADS]/app/web_entry.php?obj=dossier_instruction&value=AT0999991700001P0

Accéder à une collection d'objets
#################################

L'URL doit être composée des paramètres suivants :

* **obj** objet de l'élément que l'on souhaite visualiser (*dossier_instruction*) ;
* **field** champ de l'objet sur lequel chercher les valeurs (*dossier*) ;
* **value** valeur à chercher séparées par des *;*.

Exemple d'URL à composer : https://[URL_ADS]/app/web_entry.php?obj=dossier_instruction&field=dossier&value=AT0999991700001P0;CU0999991700001P0
