.. _dossier_zonesup:

############################################
Ajouter des zones supplementaires au dossier
############################################


openFoncier propose la possibilité de paramètrer 5 zones supplémentaires
dans dyn/var.inc

ces zones sont numérotées de $temp1 à $temp5


Il est possible de paramétrer le type :

- hidden : la zone est cachée

- text : la zone est visible

et le libellé.


Dans var.inc ::

    // zones dossier : text = visible // hidden : cache
    $temp1_type = "hidden";             // text ou hidden
    $temp1_lib= "Emplacement archive";  // libelle sur le formulaire
    $temp2_type = "hidden";
    $temp2_lib= "zone 2";
    $temp3_type = "hidden";
    $temp3_lib= "zone 3";
    $temp4_type = "hidden";
    $temp4_lib= "zone 4";
    $temp5_type = "hidden";
    $temp5_lib= "zone 5";

<experience> ::

    la zone $temp1 permet de décrire les travaux si il y en a plusieurs pour un même dossier

</experience>