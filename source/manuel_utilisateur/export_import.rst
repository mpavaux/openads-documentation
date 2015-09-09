.. _export_import:

###############
Export / Import
###############

.. _export_sitadel:

Export SITADEL
##############

(:menuselection:`Export / Import --> Export SITADEL`)

Ce menu sert à générer un export SITADEL.

=============
Configuration
=============

Au préalable, il faut vérifier que certains paramètres (:menuselection:`Administration --> Paramètre`) 
soient correctement configurés :

* **region** : doit contenir le code insee de la région de la commune qui génère l'export ;
* **commune** : doit contenir le code insee de la commune référente pour l'export, sur trois chiffres.

=========
Exécution
=========

Afin de générer l'export SITADEL, vous devez choisir :

* une date de début ;
* une date de fin ; 
* un numéro d'ordre d'envoi.

Le numéro d'ordre d'envoi est le numéro de version de votre export.

========
Résultat
========

Deux fichiers sont générés : l'export SITADEL, à envoyer au pôle statistiques de 
votre région, et un fichier contenant les incohérences détectées dans les données.

Ce second fichier n'a qu'un but informatif. Il indique quel dossier et quelle 
information est incohérente.

Charge reste à l'utilisateur d'agir, ou non, en fonction du contenu de ce fichier.

Voici une liste exhaustive des messages qui peuvent être contenus dans ce fichier :

**La SHON existante avant travaux et la SHON demolie sont nulles alors cela devrait être une nouvelle construction.**
    → La nature du projet ou les surfaces saisies sont incorrectes

**La SHON existante avant travaux ne doit pas est supérieure à la SHON démolie.**
    → Les surfaces saisies ne sont pas correctes

**La SHON demolie s'accompagne obligatoirement de la SHON existante avant travaux.**
    → Les surfaces saisies ne sont pas correctes

**Les SHON globales vouees a la transformation et issues de la transformation de doivent etre egales.**
    → Les surfaces saisies ne sont pas correctes

**Les SHON relatives a la transformation s'accompagnent obligatoirement de SHON existante avant travaux non nulle.**
    → Les surfaces saisies ne sont pas correctes

**Un nombre de logements demolis strictement positif doit s'accompagner obligatoirement de SHON demolie.**
    → La surface démolie n'a pas été renseignée alors qu'elle aurait dû

**Un nombre de logements crees strictement positif doit s'accompagner obligatoirement de SHON creee ou de SHON issue de la transformation ayant pour destination l'habitation.**
    → La surface créée/transformée n'a pas été renseignée alors qu'elle aurait dû

**La SHON creee ou issue de la transformation concernant le service public ou l'interet collectif doit obligatoirement s'accompagner du choix de destination des constructions.**
    → La répartition des surfaces n'a pas été renseignée alors qu'elle aurait dû

**La destination principale du logement mise a residence principale ou residence secondaire doit obligatoirement s'accompagner d'un mode d'utilisation a occupation personnelle.**
    → Le mode d'utilisation du logement n'a pas été renseigné

**Le nombre total de logements crees doit etre egal a la somme des nombres de logements crees ventiles par type de financement.**
    → La somme total des logements par type de financement ne correspond pas au nombre total saisit

**Le nombre total de logements crees doit etre egal a la totalisation de la repartition des logements par nombre de pieces.**
    → La somme total des logements par nombre de pièce ne correspond pas au nombre total saisit

**Une ouverture de chantier ne peut concerner qu'un permis autorise.**
    → Deux DOC ont été déposées

**La date d'ouverture de chantier doit être superieur a la date d'autorisation.**
    → La date de dépôt du P0 doit être supérieure à la date de dépôt de la DOC

**Un achevement de chantier ne peut concerner qu'un permis autorise.**
    → Deux DAACT ont été déposées

**Un achevement de chantier ne peut concerner qu'un permis sur lequel un chantier a ete ouvert.**
    → La DOC n'a pas été déposée avant la DAACT

**La date d'achevement de travaux doit etre superieur a la date d'ouverture des travaux.**
    → La date d'ouverture de chantier doit être inférieure à la date d'achèvement des travaux 

.. _versement_archives:

Versement aux archives
######################

(:menuselection:`Export / Import --> Versement aux archives`)

Cette fonctionnalité permet d'importer automatiquement le numéro de versement
aux archives des dossiers depuis un fichier CSV.

==========================
Les interfaces utilisateur
==========================

Il y a deux interfaces :

Le formulaire de saisie
=======================

Cette interface permet de saisir les informations concernant l'importation des
numéros de versement aux archives des dossiers.

.. image:: versement_archive_formulaire.png

Les informations à saisir sont :

* **insee** : code INSEE à cinq chiffres. Si ce champ est renseigné, seulement
  les dossiers ayant le même code INSEE seront traités,
* **fichier** : fichier csv comportant les données de mis à jour du numéro de
  versement,
* **séparateur** : sélection du caractère utilisé pour la séparation des 
  colonnes dans le fichier csv (';' ou ',').

Le message de résultat
======================

Cette interface permet d'avoir un résumé des actions effectuées par rapport au
fichier csv.

.. image:: versement_archive_resultat.png

Le message indique :

* le nombre de ligne lue : total des lignes ayant subit un taitement,
* le nombre de ligne acceptée : total des lignes dont la mise à jour a été
  correctement effectuée,
* le nombre de ligne rejetée : total des lignes qui n'ont pas put être traitées
  (voir :ref:`versement_archives_liste_statut_ligne`),
* le nombre de ligne ignorée : total des lignes qui n'ont pas été traitées car 
  le code INSEE renseigné dans le formulaire n'est pas le même que celui de la 
  ligne,
* la possiblité de télécharger le fichier CSV avec le détail pour chaque ligne.

==================
Format des données
==================

.. _versement_archives_format_donnees_entree:

Format des données en entrée
============================

Chaque ligne du fichier CSV en entrée doit respecter le format suivant :
Les champs doivent être séprarés par des ';'.
Le dernier champ de la ligne n'est pas suivi du séparateur ';' mais de la fin de
ligne.

* **Code insee** sur cinq caractères numériques,
* **Année** sur deux caractères,
* **Type du dossier d'autorisation** sur deux caractères alphanumérique
  (Exemple : PC, PA, etc...),
* **Numéro du dossier** sur cinq caractères maximum,
* **Numéro de version** sur deux caractères maximum,
* **Numéro de versement** sur trois ou quatre caractères numériques et suivi de 
  la lettre 'W' (Exemple : 1025W),
* **Numéro d'article** de 1 à 999999999999999.

Exemple de fichier CSV correct en entré :

03185;08;PC;1;0;1025W;111111

03185;08;RU;1;0;1025W;222222

01234;08;AT;1;0;1025W;333333

01234;12;PC;1;0;1025W;444444

Format des données en sortie
============================

Le fichier téléchargeable lors de la fin du traitement est le même CSV qu'en
entrée avec une colonne en plus qui précise le traitement fait sur la ligne.

.. _versement_archives_liste_statut_ligne:

==========================
Liste des statuts de ligne
==========================

Voici la liste des statuts possible pour une ligne du fichier CSV :

* **ligne rejetée : nombre de séparateur incorrect.** Indique que la ligne peut 
  être mal formaté, notamment au niveau du nombre de colonne,
* **ligne rejetée : contenu non conforme.** Indique que certaines données sont 
  non conforme aux spécifications 
  (voir :ref:`versement_archives_format_donnees_entree`),
* **ligne ignorée : code insee différent de celui indiqué dans le formulaire.**,
* **ligne rejetée : dossier inexistant dans l'application.**,
* **ligne acceptée : dossier mis à jour.**,

=====================
Exemple d'utilisation
=====================

Avec comme code INSEE fournis : 01234.

Fichier CSV en entré :

03185;08;PC;1;0;1025W;111111

03185;08;RU;1;0;1025W;222222

01234;08;AT;1;0;1025W;333333

01234;12;PC;1;0;1025W;444444

mmmmmmmjjjjjkkkklllll

aa;aa;aa;aa;aa;aa;aa


Fichier CSV en sortie :

03185;08;PC;1;0;1025W;111111;"ligne ignorée : code insee différent de celui indiqué dans le formulaire."

03185;08;RU;1;0;1025W;222222;"ligne ignorée : code insee différent de celui indiqué dans le formulaire."

01234;08;AT;1;0;1025W;333333;"ligne rejetée : dossier inexistant dans l'application."

01234;12;PC;1;0;1025W;444444;"ligne acceptée : dossier mis à jour."

mmmmmmmjjjjjkkkklllll;"ligne rejetée : nombre de séparateur incorrect."

aa;aa;aa;aa;aa;aa;aa;"ligne rejetée : contenu non conforme."
