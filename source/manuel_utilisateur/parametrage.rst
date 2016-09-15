.. _parametrage:

###########
Paramétrage
###########

Libellés
########

.. _parametrage_civilite:

=============
Les civilités
=============

(:menuselection:`Paramétrage --> Civilité`)

Édition des civilités présentes dans l'application.

.. _parametrage_arrondissement:

===================
Les arrondissements
===================

(:menuselection:`Paramétrage --> Arrondissement`)

Édition des arrondissements disponibles dans l'application.


.. _parametrage_quartier:

=============
Les quartiers
=============

(:menuselection:`Paramétrage --> Quartier`)

Édition des quartiers disponibles dans l'application.


Organisation
############


.. _parametrage_genre:

==========
Les genres
==========

(:menuselection:`Paramétrage --> Organisation --> Genre`)

Édition des genres de dossiers (ERP, URBA).

.. _parametrage_groupe:

===========
Les groupes
===========

(:menuselection:`Paramétrage --> Organisation --> Groupe`)

Édition des groupes de dossiers (ERP, ADS, Contentieux, Changement d'usage, ...).

.. _parametrage_direction:

============
La direction
============

(:menuselection:`Paramétrage --> Organisation --> Direction`)

Édition des informations concernant la direction du service ADS.

.. _parametrage_division:

=============
Les divisions
=============

(:menuselection:`Paramétrage --> Organisation --> Division`)

Éditions des différentes divisions traitant les demandes.

.. _parametrage_instructeur:

================
Les instructeurs
================

(:menuselection:`Paramétrage --> Organisation --> Instructeur`)

Éditions des différents instructeurs traitant les demandes.

.. _parametrage_signataire_arrete:

===============
Les signataires
===============

(:menuselection:`Paramétrage --> Organisation --> Signataire Arrêté`)

Éditions des signataires d'arrêtés.
En cochant la case "défaut" le signataire sera préselectionné lors de l'ajout d'une instruction.


.. _parametrage_taxe_amenagement:

=====================
La taxe d'aménagement
=====================

(:menuselection:`Paramétrage --> Organisation --> Taxe D'aménagement`)

Éditions de la taxe d'aménagement par collectivité.
Il ne peut y avoir qu'un seul paramétrage de taxe par collectivité. Sans ce paramétrage il n'est pas possible de simuler la taxe d'aménagement sur un dossier d'instruction.

Gestion des commissions
#######################

.. _parametrage_type_commission:

========================
Les types de commissions
========================

(:menuselection:`Paramétrage --> Gestion des commissions --> Type De Commission`)

Éditions des différents types de commissions (Commission technique d'urbanisme).

Gestion des consultations
#########################

.. _parametrage_avis_consultation:

=========================
Les avis de consultations
=========================

(:menuselection:`Paramétrage --> Gestion des consultations --> Avis Consultation`)

Éditions des différents avis possibles en réponse aux consultations de services

.. _parametrage_service:

============
Les services
============

(:menuselection:`Paramétrage --> Gestion des consultations --> Service`)

Ce menu sert au paramétrage des services consultés de l'application.

.. image:: service_parametrage.png

Dans le cadre 'Coordonnées', il faut saisir les coordonnées du service.

Le champ 'notification par mail' sert à indiquer si le service souhaite être 
notifié par mail lors de l'ajout d'une nouvelle demande de consultation. Le mail envoyé
au service consulté contient 2 liens d'accès à openADS, qui sont :ref:`paramétrables <parametrage_parametre_mails_services_consultes>`.

Le champ 'type de délai' spécifie le type du délai, c'est-à-dire si le calcul de la date limite doit être fait en mois ou en jours.

Le champ 'délai' indique le temps dont dispose le service pour répondre à une 
demande de consultation.

Le champ 'consultation papier' indique si un PDF doit être généré pour 
l'instructeur au moment de la demande de consultation.

Dans le cadre 'Validité' peuvent être indiquées les dates pour lesquelles une 
demande de consultation à ces services est possible.

Le champ 'type de consultation' spécifie le type de la consultation. Le type 
choisi a un impact sur le logiciel :

- "Pour information", qui permet à l'instructeur de signaler à un service l'existence d'une opération en cours. Elle est strictement « informative » et n'implique pas de retour d'avis de la part du service concerné.
- "Avec avis attendu", que l'instructeur déclenche lorsqu'il attend un retour d'avis de la part du service consulté. Elles s'afficheront avec un fond jaune dans le tableau listant les demandes de consultation du dossier d'instruction
- "Pour conformité", similaire à la précédente, mais qui n'intervient pas au même moment au cours du processus métier : le contenu de la demande de consultation et le délai associé différent.

Le champ 'type d'édition de la consultation' sert à indiquer le type d'édition
lié à la demande de consultation. Ce select est populé grâce aux états. 


Pour qu'un état apparaisse dans la liste des types d'édition possibles, il faut 
que le libellé de l'état soit préfixé par 'consultation\_'.

.. _parametrage_thematique_services:

===========================
Les thématiques de services
===========================

(:menuselection:`Paramétrage --> Gestion des consultations --> Thématique Des Services`)

Éditions des groupes de services.

.. _parametrage_lien_service_thematique:

===============================================
Les liens entre les services et les thématiques
===============================================

(:menuselection:`Paramétrage --> Gestion des consultations --> Lien Service / Thématique`)

Liaison des services aux différents groupes de services.

Gestion des dossiers
####################

.. _parametrage_etat_dossier_autorisation:

=====================================
Les états des dossiers d'autorisation
=====================================

(:menuselection:`Paramétrage --> Gestion des dossiers --> États Des Dossiers D'autorisation`)

Liste des états de dossiers d'autorisation possibles.

.. _parametrage_lien_evenement_da:

======================================================================
Les liens entre les évènements et les types de dossiers d'autorisation
======================================================================

(:menuselection:`Paramétrage --> Gestion des dossiers --> Lien Événement Dossier Autorisation Type`)

Liens entre les événements et les types de dossiers d'autorisation.

.. _parametrage_affectation_autmatique:

=============================
Les affectations automatiques
=============================

(:menuselection:`Paramétrage --> Gestion des dossiers --> Affectation Automatique`)

Configuration de l'affectation automatique des instructeurs aux dossiers par
arrondissement, quartier et/ou section.

.. _parametrage_autorite_competente:

=========================
Les autorités compétentes
=========================

(:menuselection:`Paramétrage --> Gestion des dossiers --> Autorité Compétentes`)

Édition des autorités compétentes possibles pour les dossiers de l'application.

.. _parametrage_phase:

==========
Les phases
==========

(:menuselection:`Paramétrage --> Gestion des dossiers --> Phase`)

La phase est un indicateur permettant un pré-aiguillage des courriers lors d'un retour d'avis de réception d'une :ref:`lettre recommandée <suivi_envoi_lettre_rar>`.
Son affichage ne se fera que si elle est paramétrée sur l':ref:`événement <parametrage_dossiers_evenement>` qui génère une édition adressée au demandeur.

Le formulaire est constitué de seulement trois champs :

  * **code** : code de la phase sur 15 caractères, c'est la valeur affichée sur les lettres recommandées ;
  * **date de début de validité** : date de la mise en service de la phase (par défaut la date courante) ;
  * **date de fin de validité** : date de fin de service de la phase, après cette date la phase ne sera plus sélectionnable depuis les événements.

.. image:: parametrage_phase.png

.. _parametrage_gestion_pieces:

Gestion des pièces
##################

.. _parametrage_document_numerise_type_categorie:

====================
Catégorie des pièces
====================

(:menuselection:`Paramétrage --> Gestion des pièces --> Catégorie des pièces`)

Paramétrage des catégories de pièces possibles.

.. _parametrage_document_numerise_type:

===============
Type des pièces
===============

(:menuselection:`Paramétrage --> Gestion des pièces --> Type des pièces`)

Paramétrage des types de pièces possibles.

Les champs du formulaire lors de l'ajout :

  * **Code** : Code du type de pièce, champ obligatoire utilisé pour composer le nom des pièces ;
  * **Libellé** : Libellé du type de pièce, champ obligatoire ;
  * **Catégorie de pièces** : Catégorie du type de pièce, champ obligatoire ;
  * **Ajoutable par les instructeurs** : Permet de définir si le type de pièce peut être utilisé par un instructeur, par défaut coché ;
  * **Affiché sur les demandes d'avis** : Permet de définir si les pièces de ce type peuvent êtres visualisées sur les demandes d'avis, par défaut coché ;
  * **Affiché sur les DA** : Permet de définir si les pièces de ce type peuvent êtres visualisées sur les dossiers d'autorisation (affichage publique), par défaut coché.

.. image:: parametrage_document_numerise_type_form.png

Lors de la modification d'un type de pièce, si les champ **Affiché sur les demandes d'avis** et/ou **Affiché sur les DA** sont modifiés alors les informations sur les fichiers de ce type seront mise à jour lors du prochain :ref:`traitement des métadonnées <parametrage_document_numerise_type_traiter_metadonnees>`.

.. _parametrage_document_numerise_type_traiter_metadonnees:

==========================
Traitement des métadonnées
==========================

(:menuselection:`Paramétrage --> Gestion des pièces --> Traitement des métadonnées`)

Mise à jour des métadonnées des fichiers stockés dont le type de pièce a été modifié.

Lors de la modification d'un type de pièce, si les champ **Affiché sur les demandes d'avis** et/ou **Affiché sur les DA** sont modifiés, un marqueur identifie le changement, mais les fichiers des pièces ciblées ne sont pas mises à jour.
Ce changement peut être appliqué ensuite à l'intégralité des fichiers des pièces de ce type par deux méthodes :

  * depuis l'interface reservé aux administrateurs ;
  * de manière désynchronisée, en tâche de fond, par un appel à un service web de maintenance.

Depuis l'interface
==================

.. image:: parametrage_document_numerise_metadata_treatment.png

Il suffit de cliquer sur le bouton **Mise à jour des métadonnées** pour lancer le traitement.

.. image:: parametrage_document_numerise_metadata_treatment_res.png

L'écran de résultat affiche un rapport détaillant les fichiers mis à jour.
