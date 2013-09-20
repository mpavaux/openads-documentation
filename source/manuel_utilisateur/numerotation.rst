.. _numerotation:



############################
La numerotation des dossiers
############################


openFoncier propose la possibilité de paramètrer la numérotation
dans dyn/var.inc



option_numero_unique permet de numéroter de manière unique tous les dossiers
le paramètre $lettre est la lettre de la collectivité dans le dossier


Dans var.inc ::

    option_numero_unique dossier =1
    sinon = 0 numerotation par nature de dossier
    $option_numero_unique=0;
    $lettre='R'; //  R pour ARLES

    Ces parametres sont utilisés pour constituer le numéro unique du dossier



<developpement> 

    Il faudra transférer ces paramètres en om_collectivite pour la multicollectivité
    la methode qui utilise est setId() de obj/dossier.class.php
    Cette modification est prise en charge par Marseille (gestion par secteur)
    
</developpement>