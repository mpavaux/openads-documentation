.. _evenement:

##############
Les événements
##############

Il est proposé de décrire dans ce chapitre le paramétrage de l'instruction au
niveau :

- des événements

- de la bible

- des lettres type

- des acteurs



Le paramétrage des evenements
=============================

Le paramétrage des evenements se fait dans le formulaire evenement 

.. image:: ../_static/form_evenement.png

Le paramétrage dans le cas plus haut correspond à la notification de pièces manquante :

- cet evenement s'applique à tous les dossiers

- l'action est d' "appliquer un délai de rejet"

- le dossier sera dans l'état "rejeter"

- le delai de rejet est de 3 mois

- il n'y a plus d'accord tacite si le delai d'instruction est dépassé

- la lettre type qui s'applique est la lettre "piecescomplementaire"


La case consultation permet lorsqu elle est cochée de récupérer automatiquement les
avis de consultation. Cette case est surtout interessante pour la mise en oeuvre d'arrêtés
qui vise les consultations en zone "complement1". 



La bible
========

Dans l'onglet, il est possible de voir les textes applicables à l'événement décrit plus haut
Ces textes seront insérés dans les lettres type de chaque événement :


.. image:: ../_static/tab_bible.png


Le formulaire de saisie d'un texte de la bible est décrit ci dessous :


.. image:: ../_static/form_bible.png

Dans notre exemple, il est demandé :

"une notice faisant apparaitre les matériaux utilisés et les modalités d'execution des travaux"

Ce texte ne sera pas appellé automatiquement et sera inscrit dans le complément 1 et ne concerne
que les déclarations préalables.


Les lettres type
================

Le formulaire ci dessous permet de modifier la lettre type "piecescomplementaire"

.. image:: ../_static/lettretype_evenement.png

La description du paramétrage de lettre type est décrite dans le guide du
développeur openMairie.

De manière générale, il y a donc plusieurs niveaux de paramétrage de lettre type
suivant le niveau de spécificité :

. il est crée un canevas dans om_lettretype, et il est inséré les champs de la base
avec le paramètrage de la requête SQL et on rajoute des variables applicatives
(table parametre de la collectivité ou date système ...)

. les textes issus de la bible de manière automatique ou manuelle le sont dans le
formulaire instruction

. enfin il est possible de rajouter du texte spécifique dans ce formulaire



La mise en pratique dans une phase d'instruction
================================================

Il est proposé de saisir dans un dossier de "DP" la phase d'instruction "rejet par manque de pièce complementaire" :

Il est choisi dans le formulaire d'instruction l'événement correspondant.

Avec la bible automatique ou manuelle, il est complété complement1 du formulaire instruction:

.. image:: ../_static/evenement_instruction.png

et on rajoute en complement le texte suivant :

 "un exemple de construction similaire"
 
 
ce qui donne la saisie suivante :

.. image:: ../_static/evenement_instruction2.png


L'édition de la lettre type devient avec les paramètres du formulaire instruction :


.. image:: ../_static/instruction_lettretype.png


Le paramètrage des actions
==========================

Le parametrage des actions  est fait dans la table action (option paramétrage du menu).
Cette table contient les règles applicables aux champs de la table dossier lors
de la mise à jour d'un événement d'instruction.


.. image:: ../_static/tab_action.png

Le formulaire de saisie des actions est le suivant :

.. image:: ../_static/form_action.png


Mise en place des règles de modification des champs du dossier :

Il est possible de modifier les règles applicables au dossier sur les champs suivants ::

        Il est possible de modifier 14 champs de la table dossier
        en paramétrant les champs "regle"
        
        Champ texte :                   regle unique = valeur de l'évènement
            regle_etat                  etat (de l evenement)
            regle_accord_tacite         accord _tacite (de l'évèvenement)
            regle_avis                  avis (de l evenement)
            regle_autorite_competente   autorite_competente (de l'évènement)
        Champ calcule                   regle de calcul delai avec ou sans ajout
            delai                       delai (de l evenement) + Nombre de mois
            
        Dates
        
            regle_date_complet
            regle_date_limite
            regle_date_notification_delai
            regle_date_limte
            regle_date_decision
            regle_date_validite
            regle_date_chantier
            regle_date_echevement
            regle_date_conformite
            
            Les regles possibles sont les suivantes
                exemple : avec 3 opérandes
                    datecourrier (de l evenment) + delai + nombre de mois
                exemple : avec 2 opérandes
                    date_complet + nombre de mois
                exemple avec 1 operande
                    null

Champs utilisable :

**Valeurs du dossier avant l'évènement**

[archive_etat] [archive_delai] [archive_accord_tacite] 
[archive_avis]
[archive_date_dernier_depot] [archive_date_complet] 
[archive_date_rejet] [archive_date_limite] 
[archive_date_notification_delai] [archive_date_decision] 
[archive_date_validite] [archive_date_achevement] 
[archive_date_conformite] [archive_date_chantier] 
[archive_etat_pendant_incompletude] [archive_date_limite_incompletude]
[archive_delai_incompletude] [archive_autorite_competente] 
[duree_validite]

**Paramètres de l'évènement**

[etat] [delai] [accord_tacite] [avis_decision] 
[delai_notification] [date_evenement] [autorite_competente]

**Paramètres du type detaillé du dossier d'autorisation**

[duree_validite_parametrage]

**Suppression de la valeur**

[null]

Le diagramme de classe evenement :
==================================

Il est proposé ci dessous de présenter le diagrame de la classe evénement

.. image:: ../_static/uml_evenement.png

