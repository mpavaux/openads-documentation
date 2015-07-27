.. _instruction:

###########
Instruction
###########

==================
Le tableau de bord
==================

(:menuselection:`Instruction --> Tableau De Bord`)

Le tableau de bord permet de lister les dossiers qui répondent à des critères particuliers.

Widget - Dossiers auxquels on peut proposer une autre décision
==============================================================

Ce widget liste les dossiers pour lesquels on peut proposer une autre décision.

Il s'agit de ceux dont le dernier événement d'instruction de type arrêté est finalisé,
n'est pas de type retour et ne dispose d'aucune date renseignée parmi les suivantes :

* date d'envoi pour signature ;
* date de retour de signature ;
* date d'envoi RAR ;
* date de retour RAR ;
* date d'envoi au contrôle légalité ;
* date de retour du contrôle de légalité.

=============================
Gestion des pièces du dossier
=============================

Chaque dossier d'instruction peut avoir plusieurs documents numérisés.

Ils sont listés dans l'onglet "Pièces" et organisés par date et catégorie des documents.

.. image:: piece_tab.png

Au clic sur le nom du document, il sera ouvert depuis le stockage au format PDF.

Pour ajouter un document il faut cliquer sur le "+" vert en haut de page à côtés de la mention "Ajouter un document".

.. image:: piece_form.png

Dans le formulaire qui apparaît tous les champs sont obligatoires :

* **Fichier** : Documents au format PDF à envoyer en GED.
* **Uid** : Documents au format PDF à envoyer dans le stockage.
* **Date de création** : Date de création du document.
* **Type de document** : Type du document.

===========================================
Documents numérisés ou reprise de l'arriéré
===========================================

Les documents numérisés ou repris doivent être placés dans le sous-dossier "Todo"
du dossier configuré dans la variable $config['path_scan'] (dyn/config.inc.php).

L'opérateur qui numérise les documents devra donc les déposer dans le sous dossier
nommé de la même façon que le dossier d'instruction lié. Par exemple, pour le 
dossier d'instruction AT 013055 12 00001P0, on aura un dossier nommé 
AT01305512.00001P0

Un service automatique (CRON) se chargera de traiter ces documents : les enregistrer
dans le système de stockage prédéfini ainsi que les lier au dossier d'instruction
dans openADS. Les documents traités sont ensuite supprimés.

========================
Événements d'instruction
========================

.. image:: instruction_form_edition.png

Événement
=========

* **événement** : sélection de l'événement d'instruction
* **date d'événement** : date de l'événement (date du jour par défaut)
* **lettre type** : choix de la lettre type affectée à cet événement d'instruction

Dates
=====

Dates de suivi chronologique de l'événement d'instruction.

* **date de finalisation du courrier**
* **date d'envoi pour signature**
* **date d'envoi RAR**
* **date d'envoi au contrôle légalité**
* **signataire** (on peut en sélectionner un par défaut, cf. `Paramétrage --> Organisation --> Signataire Arrêté`)
* **date de retour de signature**
* **date de retour RAR**
* **date de retour du contrôle de légalité**

Compléments
===========

Les champs de complément sont composés d'un éditeur riche permettant une mise en
page complexe.

Il est possible d'ajouter des compléments d'informations pour les événements 
d'instruction depuis les blocs "Complément" et "Complément 2".

La plupart des compléments d'informations sont disponibles depuis la bible.

.. image:: instruction_complement_bible.png

Il suffit de choisir l'élément que l'on désire voir apparaître dans le champ 
complément.
En laissant la souris sur le libellé une infobulle affichera le texte qui sera 
affiché.

(Pour plus d'information sur la bible voir :ref:`parametrage_dossiers_bible`.)

Suppression
===========

Il est possible de supprimer le dernier événement d'instruction créé s'il remplit
ces critères :

 - le dossier d'instruction rattaché n'est pas clôturé
 - l'événement d'instruction n'est pas finalisé
 - les dates suivantes ne sont pas renseignées : envoi pour signature, retour de signature, envoi RAR, re­tour RAR, envoi au contrôle légalité, retour du contrôle légalité
 - l'événement lié n’est pas de type « retour »

.. _instruction_complement:

============
Finalisation
============

Finalisation des documents de l'instruction
===========================================

Pour finaliser l'édition de l'instruction, il faut cliquer sur le lien "Finaliser le document" du portail d'action de la visualisation.

.. image:: portlet_finaliser.png

Au clique sur le lien de l'édition dans le portail d'action de la visualisation de l'instruction, le document sera ouvert depuis le stockage au format PDF.

L'instruction n'est plus ni modifiable, ni supprimable.

Il est aussi possible de dé-finaliser le document au clique sur le lien "Reprendre la rédaction du document".

.. image:: portlet_definaliser.png

Lorsque le document est finalisé certaines informations concernant le dossier
lui sont associées lors de l'enregistrement.

Il est aussi possible de dé-finaliser le document au clique sur le lien "Reprendre la rédaction du document".

Le clique sur le lien de l'édition dans le portail d'action de la visualisation de l'instruction ouvrira le document généré à la volée au format PDF.

L'instruction est à nouveau modifiable et supprimable.


Finalisation des documents du rapport d'instruction
===================================================

Pour finaliser l'édition du rapport d'instruction, il faut cliquer sur le lien "Finaliser le document" du portail d'action de la visualisation.

.. image:: portlet_finaliser.png

Lorsque le document est finalisé certaines informations concernant le dossier
lui sont associées lors de l'enregistrement.

Au clique sur le lien de l'édition dans le portail d'action de la visualisation du rapport d'instruction, le document sera ouvert depuis le stockage au format PDF.

Le rapport d'instruction n'est plus ni modifiable, ni supprimable.

Il est aussi possible de dé-finaliser le document au clique sur le lien "Reprendre la rédaction du document".

.. image:: portlet_definaliser.png

Le clique sur le lien de l'édition dans le portail d'action de la visualisation du rapport d'instruction ouvrira le document généré à la volée au format PDF.

Le rapport d'instruction est à nouveau modifiable et supprimable.

Finalisation des documents de la consultation
=============================================

Pour finaliser l'édition de la consultation, il faut cliquer sur le lien "Finaliser le document" du portail d'action de la visualisation.

.. image:: portlet_finaliser_consultation.png

Lorsque le document est finalisé certaines informations concernant le dossier
lui sont associées lors de l'enregistrement.

Au clique sur le lien de l'édition dans le portail d'action de la visualisation 
de la consultation, le document sera ouvert depuis le stockage au format PDF.

La consultation n'est plus supprimable.

Il est aussi possible de dé-finaliser le document au clique sur le lien "Reprendre la rédaction du document".

.. image:: portlet_definaliser.png

Le clique sur le lien de l'édition dans le portail d'action de la visualisation 
de la consultation ouvrira le document généré à la volée au format PDF.

La consultation est à nouveau supprimable.


Enregistrement de l'arrêté
==========================

Lors de la finalisation d'un évènement d'instruction de type arrêté le document
est enregistré sur le systeme de fichier.
Lorsqu'il revient après signature par l'autorité compétente, les informations qui
le compose sont envoyé au référentiel des arrêtés, et le document finalisé est
enregistré dans le systeme de fichiers associé à certaines informations (numéro 
de l'arrêté dans le référentiel, informations concernant le signataire, le terrain,
et l'arrêté).

.. _instruction_dossier_contrainte:

=============================
Contraintes liées au dossier
=============================

.. _instruction_dossier_contrainte_view:

Visualisation des contraintes liées au dossier
===============================================

Les contraintes affichées dans le tableau de données sont groupées par groupe et
sous-groupe et sont classées par le numéro d'ordre d'affichage.

Chaque contrainte possède un bouton raccourcis pour ouvrir le formulaire en 
modification et un autre en mode suppression.
Seulement le champ **texte complété** est modifiable.

.. image:: instruction_dossier_contrainte_view.png

.. _instruction_dossier_contrainte_add_man:

Ajouter des contraintes manuellement
====================================

En cliquant sur le bouton **Ajouter des contraintes**, un formulaire présentant
toutes les contraintes de l'application apparait.

Les contraintes sont triées comme dans le tableau de données, par groupe, sous-groupe et par l'ordre d'affichage. Par défaut chaque groupe et sous-groupe sont
repliés.

Il suffit de cliquer sur un contrainte pour la sélectionner et de valider le
formulaire pour que celle-ci soit ajouter au dossier. Un message de validation 
apparait.

.. image:: instruction_dossier_contrainte_form.png

.. image:: instruction_dossier_contrainte_form_valide.png

.. _instruction_dossier_contrainte_add_auto:

Ajouter des contraintes automatiquement
=======================================

Depuis le formulaire de géolocalisation, il est possible de récupérées les 
contraintes d'un dossier depuis le SIG automatiquement en cliquant sur l'action 
**Récupérer les containtes**.
Attention cette action écrasera les précédentes contraintes récupérées 
automatiquement. Les contraintes récupérées automatiquement puis modifiées ne 
sont plus référencées comme provenant du SIG.

.. image:: instruction_geolocalisation_view.png