.. _autorisations:

#############
Autorisations
#############

Introduction
============

Le dossier d'autorisation contient l'ensemble des informations en cours de
validité des dossiers d'instruction qui lui sont liés.

Liste des dossiers d'autorisation
=================================

Il est possible de lister les dossiers d'autorisation depuis le menu "Autorisation".

Ces dossiers d'autorisation sont listés par ordre alphabétique.

Une recherche peut être effectuée sur plusieurs critères :

- numéro de dossier

- type detaillé de dossier d'autorisation

- nom du demandeur

- parcelle

- l'adresse du terrain

- l'arrondissement

- l'état

- la date de premier dépôt

- la date de décision

Ce tableau permet d'accéder à la visualisation des dossiers d'autorisation.

Visualisation des dossiers d'autorisation
=========================================

.. image:: ../manuel_utilisateur/autorisation_visualisation.png

La visualisation contient deux blocs d'informations :

- "En cours de validité" : informations des dossiers d'instructions soumis à un arrété.

    * En noir : les informations importantes en cours de validité
    * En vert : la liste des lots et leurs petitionnaire principal en cours de validité
    * En rouge : la liste des décisions en cours de validité
    * En bleu : un lien vers toutes les données technique en cours de validité

- "En cours d'instruction" : données du dossier d'instruction en cours d'instruction.

    * En noir : les informations importantes en cours d'instruction
    * En vert : la liste des lots et leurs petitionnaire principal en cours d'instruction


Mise à jour des informations
============================

Il exite 3 groupes d'informations :

- celles mises à jour lors de la création d'un dossier d'instruction initial ou lorsqu'un dossier d'instruction est accepté :

    - l'adresse du terrain
    - les références cadastrale
    - les demandeurs
    - les lots

- les dates qui sont calculées de manière individuelle :

    - date de premier dépôt : date de dépôt du dossier d'instruction initial
    - date de première décision : date de décision du dossier d'instruction initial
    - date de fin de validité : plus haute date de validité tous dossier d'instruction confondu
    - date de dépôt DOC : date d'ouverture de chantier du dernier dossier d'instruction accepté
    - date de dépôt DAACT : date de fin de chantier du dernier dossier d'instruction accepté

- trois informations concernant l'état du dossier d'autorisation :

    - l'état du dernier dossier d'instruction
    - l'état du dossier d'instruction initial après décision si un seul dossier d'instruction, sinon l'état du dernier dossier d'instruction accepté
    - l'avis de la décision du dossier d'instruction initial après décision si un seul dossier d'instruction, sinon l'avis de la décision du dernier dossier d'instruction accepté

Ces informations sont recalculées à chaques ajout, modification, suppression des dossiers d'instruction et événements d'instruction.

Autres informations accessibles
===============================

.. image:: ../manuel_utilisateur/autorisation_liste_di.png

Liste des dossiers d'instruction liés au dossier d'autorisation (voir :ref:`instruction`).

.. image:: ../manuel_utilisateur/autorisation_liste_pieces.png

Liste des pièces liées au dossier d'autorisation.
