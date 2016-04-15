.. _service_consulte:

################
Service consulté
################

.. _service_consulte_tableau_de_bord:

Le tableau de bord
##################

(:menuselection:`Demandes D'avis --> Tableau De Bord`)

Pour l'instant le tableau de bord service consulté ne comporte aucun widget.

.. _service_consulte_demandes_en_cours:

Demandes en cours
#################

(:menuselection:`Demandes D'avis --> Demandes en cours`)

Ce menu permet d'accéder à la liste des demandes d'avis en cours, envoyées au service
connecté.

La liste des demandes d'avis en cours se compose des demandes d'avis dont :

- la date limite n'est pas dépassée
- l'avis n'a pas été rendu

Ces demandes sont triées par date limite croissante.

.. image:: service_consulte_types_demande_avis.png

Chaque type consultation possède son code couleur :

- Jaune : demande pour conformité
- Gris : demande pour information
- sans : demande avec avis attendu

En cliquant sur la demande d'avis l'utilisateur accède à la synthèse du dossier qu'il peut marquer/dé-marquer.

.. _service_consulte_demandes_avis_en_cours:

Export des demandes d'avis en cours
===================================

Les utilisateurs des services peuvent exporter un ensemble de demandes d'avis 
filtrées via la recherche avancée dans un format exploitable sur tableur.
Pour cela, il clique sur la rubrique export.

.. XXX insérer une capture

Saisie d'avis
=============

  .. image:: service_consulte_demande_avis_en_cours_form.png

Pour mettre à jour l'avis, l'utilisateur clique sur l'action de contexte Rendre
un avis de la synthèse du dossier. Un formulaire apparaît en surimpression de la
page courante, lui proposant de formuler son avis via trois champs :

- Avis, qui propose une liste d'avis pré-définis : Favorable, Défavorable, Favorable avec réserve, Tacite, Autre. Ce champ est obligatoire ;
- Motivation, qui lui permet de saisir du texte libre motivant son avis. Ce champ est facultatif ;
- Retour d'avis, qui lui donne la possibilité de joindre un fichier au format PDF. Ce champ est également facultatif.

Une fois les informations saisies, l'utilisateur valide le formulaire. Il est redirigé sur la liste
des demandes d'avis en cours : la demande précédente n'y figure plus, mais il
peut y accéder via la rubrique Demandes d'avis passées ;

.. _service_consulte_demandes_passees:

Demandes passées
################

(:menuselection:`Demandes D'avis --> Demandes passées`)

Ce menu permet d'accéder à la liste des demandes d'avis auxquelles le service
consulté à répondu.

La liste des demandes d'avis passées se compose des demandes d'avis dont :

- la date limite est dépassée
- l'avis a été rendu

Ces demandes sont triées par date limite croissante.

Chaque type consultation possède son code couleur :

- Jaune : pour conformité
- Gris : pour information
- sans : avec avis attendu

En cliquant sur la demande d'avis l'utilisateur accède au résumé de la demande, à l'avis rendu, ainsi qu'à la synthèse du dossier d'instruction.

.. image:: service_consulte_demande_avis_passee_form.png

Export des demandes d'avis passées
==================================

Les utilisateurs des services peuvent exporter un ensemble de demandes d'avis 
filtrées via la recherche avancée dans un format exploitable sur tableur.
Pour cela, il clique sur la rubrique export.

.. XXX insérer une capture ou lien vers
