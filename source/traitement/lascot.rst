.. _lascot:



###############
L'export lascot
###############

Il est proposé de décrire la procedure de transfert "lascot"

la procédure est utilisée pour transmettre les données à l'application lascot utilisé par
le service cadastre de la DGI (direction générale des impots)

La procédure "sitadel" semble se substituer à cette procédure.

Le paramètrage des travaux
==========================

Il se fait dans le formulaire "travaux"

Le but du paramètrage est de déterminer les travaux imposables pour permettre à la
DGI de suivre la masse taxable.


<experience> ::

    Il est nécessaire de ne pas multiplier les types de travaux et de paramétrer
    le "travaux" correspondant à l ADS
    Il vaut mieux ne pas avoir recours à une description type "autres travaux"
    La ville d arles utilise une zone temp (voir dossier_zone supplementaire) pour
    expliciter un "travaux"

    La case solde a permis d'éliminer les erreurs de paramètrage initiaux.
    

La table travaux permet de faire la correspondance entre les travaux définit dans
la loi sur les ADS applicable au 01/10/2007 et l'application "lascot" du cadastre
qui définit sur un seul caractère (1 chiffre ou une lettre) l'information imposable
ou non imposable (9 destinations possibles)

Les fichiers d'exportation sont normalisés :

- LOmmaaPC.132

- LOmmaaDT.132

- LOmmaaPA.132

mm = mois sur 2 chiffres

aa = année sur 2 chiffres

La transmission se fait mois par mois par rapport à la date de dépot.


Les dessins de fichiers
=======================


Les dessins de fichiers à transmettre sont différents suivant les natures.

dessins de fichier PC : format de longueur fixe ::

    No  zone                longueur    position        openfoncier / dossier

    1   departement             2           1           parametre collectivite
    2   commune                 3           3           parametre collectivite
    3   annee depot             2           6           annee           
    4   numero                  5           8           dossier
    5   modificatif             1           13          dossier
    6   annee depot precedent   2           14          vide
    7   no dossier precedent    2           16          vide
    8   modificatif precedent   1           21          vide
    9   maitre ouvrage (mo)     32          22          demandeur-civilite + nom
    10  2eme ligne              32          54          demandeur_societe
    11  adresse 1               32          86          demandeur_adresse
    12  adresse 2               32          118         vide
    13  adresse 3               32          150         vide
    14  cp                      5           182         demandeur_cp
    15  commune                 26          187         demandeur_ville
    16  telephone mo            20          213         vide
    17  cadastre                7           233         parcelle
    18  1ere ligne              32          240         terrain-numero + compl + adresse
    19  2eme ligne              32          272         terrain_adresse_complement
    20  3eme ligne              32          304         vide
    21  cp                      5           336         terrain_cp
    22  commune                 26          341         terrain_ville
    23  decision  (200704)      6           373         date_decision
    24  categorie mo            6           376         vide
    25  nature travaux          1           374         codelascot de travaux
    26  type annexe habitation  1           375         vide
    27  shon totale             6           376         vide
    28  shon habitation         6           382         shon
    29  utilisation             1           388         shon
    30  util loc non hab        1           389         vide
    31  destination             1           390         vide (plusieurs destinations)
    32  nb logement             3           391         logement_nombre
    33  nb maison               3           394         vide
    34  nb logement collectif   3           397         vide
    35  nb batiments            3           400         batiment_nombre
    36  nb 1 piece              3           403         vide
    37  nb 2 piece              3           406         vide    
    38  nb 3 piece              3           409         vide    
    39  nb 4 piece              3           412         vide
    40  nb 5 piece              3           415         vide
    41  nb 6 piece  et +        3           418         vide
    42  shon non hab            6           421         vide    
    43  1er type ouvrage        2           427         vide
    44  shon associé 1er type   6           429         vide
    45  code APET               4           435         vide
    46  nature logement         1           439         vide
    47  capacité acceuil        3           440         vide
    total 443
    
dessins de fichier DT / PD ::

    No  zone                longueur    position        openfoncier / dossier

    1   departement             2           1           parametre collectivite
    2   commune                 3           3           parametre collectivite
    3   annee depot             2           6           annee           
    4   numero                  5           8           dossier
    5   decision  (200704)      6           13          date_decision
    6   label PD ou DT          2           19          nature
    7   maitre ouvrage (mo)     32          21          demandeur-civilite + nom
    8   2eme ligne              32          53          demandeur_societe
    9   adresse 1               32          85          demandeur_adresse
    10  adresse 2               32          117         vide
    11  adresse 3               32          149         vide
    12  cp                      5           181         demandeur_cp
    13  commune                 26          186         demandeur_ville
    14  1ere ligne terrain      32          212         terrain-numero + compl + adresse
    15  2eme ligne              32          244         terrain_adresse_complement
    16  3eme ligne              32          276         vide
    17  cp                      5           308         terrain_cp
    18  commune                 26          313         terrain_ville
    19  cadastre                7           339         parcelle
    20  destination             1           346         vide (plusieurs destinations)
    total 376


Les imports PA ne sont pas implémentés ::

    No  zone                longueur    position        openfoncier / dossier

    1   departement             2           1           parametre collectivite
    2   commune                 3           3           parametre collectivite
    3   annee depot             2           6           annee           
    4   numero                  5           8           dossier
    5   modificatif             1           13          dossier
    6   label PD ou DT  ou pc   2           14  
    7   date annulation         6           16
    8   motif annulation        1           22
    total 23


<developpeur> ::

    
    Les scripts sont les suivants :

    spc/export_pc.php
    
    spc/export_dp.php pour dp et pd
    
