.. _installation:

############
Installation
############

.. note::

    openADS est une application sensible, nécessitant un paramétrage précis.
    Un mauvais paramétrage peut entrainer le non respect du code de l'urbanisme.
    Ni l'équipe du projet openADS ni le chef de projet ne peuvent être tenus
    pour responsables d'un éventuel dysfonctionnement comme ceci est précisé dans
    la licence jointe. Vous pouvez, si vous le souhaitez, faire appel a un
    prestataire spécialisé qui peut fournir support, hot-line, maintenance, et
    garantir le fonctionnement en environnement de production.


**********
Pré-requis
**********

Vous devez avoir installé :

- un serveur web (apache, ...)
- PHP
- le moteur de base de donnees PostGreSQL


Sous windows, il est facile de trouver de la documentation pour l'installation
de ces éléments en utilisant wamp (http://www.wampserver.com/) par exemple.


Sous Linux, il est facile de trouver de la documentation pour l'installation de
ces éléments sur votre distribution.


***********
Déploiement
***********

Installation des fichiers de l'applicatif
=========================================

Télécharger l'archive zip
-------------------------

http://adullact.net/frs/?group_id=390


Décompresser l'archive zip dans le répertoire de votre serveur web
------------------------------------------------------------------

- Exemple sous windows dans wamp : wamp/www/openads
- Exemple sous linux avec debian : /var/www/openads


Création et initialisation de la base de données
================================================

Créer la base de données
------------------------

Il faut créer la base de données dans l'encodage UTF8. Par défaut la base de données s'appelle openads.


Dans un environnement debian :

.. code-block:: bash

  createdb openads


Initialiser la base de données
------------------------------

Il faut initialiser les tables, les séquences et données de paramétrage grâce au script data/pgsql/install.sql


Dans un environnement debian depuis le répertoire data/pgsql/ :

.. code-block:: bash

  psql openads -f install.sql


Configuration de l'applicatif
=============================

Positionner les permissions nécessaires au serveur web
------------------------------------------------------

Dans un environnement debian : 

.. code-block:: bash

  chown -R www-data:www-data /var/www/openads


Configuration de la connexion à la base de données
--------------------------------------------------

La configuration se fait dans le fichier `dyn/database.inc.php` :

.. code-block:: php

    <?php
    ...
    // PostGreSQL
    $conn[1] = array(
        "openADS", // Titre 
        "pgsql", // Type de base
        "pgsql", // Type de base
        "postgres", // Login
        "postgres", // Mot de passe
        "tcp", // Protocole de connexion 
        "localhost", // Nom d'hote
        "5432", // Port du serveur
        "", // Socket
        "openads", // nom de la base
        "AAAA-MM-JJ", // Format de la date
        "openads", // Nom du schéma
        "", // Préfixe
        null, // Paramétrage pour l'annuaire LDAP
        "mail-default", // Paramétrage pour le serveur de mail
        "filestorage-default", // Paramétrage pour le stockage des fichiers
    );
    ...
    ?>

*************************
Connexion à l'application
*************************

Ouverture dans le navigateur
============================

http://localhost/openads/

'localhost' peut être remplacé par l'ip ou le nom de domaine du serveur.


Login
=====

* Utilisateur "administrateur" : 
   - identifiant : admin
   - mot de passe : admin

Le message de bienvenue doit être affiché "Votre session est maintenant ouverte."


***************
En cas d'erreur
***************

Activer le mode debug
=====================

Il est possible d'activer le mode debug pour visualiser les messages d'erreur
détaillés. Dans le fichier `dyn/debug.inc.php`, il faut commenter le mode
production et décommenter le mode debug.

Mode production :

.. code-block:: php

   //define('DEBUG', VERBOSE_MODE);
   //define('DEBUG', DEBUG_MODE);
   define('DEBUG', PRODUCTION_MODE); 

Mode debug :

.. code-block:: php

   //define('DEBUG', VERBOSE_MODE);
   define('DEBUG', DEBUG_MODE);
   //define('DEBUG', PRODUCTION_MODE); 

