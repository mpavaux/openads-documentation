.. _evenement:

##############
Les événements
##############

Il est proposé de décrire dans ce chapitre le paramétrage de l'instruction au
niveau :

- des événements

- de la bible

- des lettres type




Le paramètrage des evenements
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

. enfin il est possible de rajouter de texte spécifique dans ce formulaire


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




Le paramètrage de l'instruction
===============================

<developpeur>

Le parametrage de l instruction est fait dans obj/instruction.class.php

La methode triggerajouter modifie les dates dans les actions suivantes ::

        action              
        
        initialisation   :  delai = delai de evenement                      
                            etat = etat de evenement
                            accord_tacite = accord tacite de evenement
                            date_complet = archive_date_depot
                            date_limite = date_courrier + delai evenement
                            date_notification_delai = date_complet + 1 mois (en dur)
                            archive de la date_complet dans instruction
                            
        notification :    
                            date_complet est celle precedemment saisie
                            date_limite avec delai de l evenement
                            date_notification_delai = date_complet + 1 mois
                            verification datecourrier <= date_delai_notification
                            
        retour   :          delai = archive_delai + delai de l evenement
                            etat  = etat de l evenement
                            accord_tacite = accord_tacite de l'evenement
                            la date_complet = datecourrier
                            date_notification_delai date_complet + 1 mois
        
        rejet   :           etat  = etat de l evenement
                            accord_tacite = accord_tacite de l'evenement
                            date_rejet = datecourrier 
                            date_limite =null;
                            date_notification_delai =null;
                            date_complet=null;
        
        majoration  :       delai = archive_delai + delai de l evenement
                            etat  = etat de l evenement
                            accord_tacite = accord_tacite de l'evenement
                            date_complet = archive_date_complet
                            majoration de la date_limite avec delai de l evenement
                            date_notification_delai date_complet + 1 mois
                            verification que la date du courrier ne doit pas etre depasse
                            par rapport au delai de notification
                            
        acceptation   :     etat  = etat de l evenement
                            avis  = avis de l'evenement
                            date_decision = datecourrier
                            date_validite = datecourrier + delai de l evenement
        
        refus :             etat = etat de l evenement
                            date_decision = datecourrier
                            avis = avis de l evenement
                            
        prolongation :      date_validite =  archive_date_validite +  delai de l'evenement
        
        
        sursis :            date_limite =  datecourrier+delai de l evenement
                            etat = etat de l evenement
                            accord_tacite= accord_tacite de l evenement
                            avis = avis de l evenement
                            date_decision = datecourrier
                            date_validite=date_limite + 2 mois (en dur)
                            
        execution  :        etat = etat de l'evenement
                            date_chantier =  datecourrier

        achevement          etat = etat de l evenement
                            date_achevement = datecourrier

        archivage :         etat = etat de l'evenement
                            date_conformite = datecourrier

        defaut :            etat = etat de l evenement


<Proposition> ::

    saisie de regle dans un textarea dans la table action
    ou table fille regle_action ?

</proposition>

</developpeur>


Le diagramme de classe evenement :
==================================

<developpeur>

.. image:: ../_static/uml_evenement.png

</developpeur>