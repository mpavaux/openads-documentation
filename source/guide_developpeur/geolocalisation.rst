.. _geolocalisation:

##################
La géolocalisation
##################

.. toctree::
    :numbered:

    geolocalisation_plugin_connecteur_sig.rst
    geolocalisation_ancien_exemple_d_integration_openfoncier.rst

###############
Les contraintes
###############

Synchroniser toutes les contraintes
###################################

Les contraintes de l'application sont comparées avec celles du SIG sur la base de l'identifiant de la contrainte sur le SIG.

Lorsque l'action "synchroniser les contraintes" est lancée, les champs numero, groupe, sous-groupe et libelle sont récupérés à partir du SIG de chaque contrainte sont récupérés. Les contraintes sont dans un état "générique", les textes à trous comme "distance du puits : ..... m" ne sont pas complétés.

Récupération des contraintes d'un dossier
#########################################

Lorsqu'on lance la récupération des contraintes dans le cadre de la géolocalisation d'un dossier (après vérification des parcelles et calcul de l'emprise et du centroide), on récupère les contraintes avec le texte des contraintes complété.
