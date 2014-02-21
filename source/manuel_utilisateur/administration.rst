.. _administration:

##############
Administration
##############

Libellés
########

.. _administration_collectivite:

=================
Les collectivités
=================

(:menuselection:`Administration --> Collectivité`)

Édition des collectivités présentes dans l'application.

.. _parametrage_parametre:

==============
Les paramètres
==============

(:menuselection:`Administration --> Paramètre`)

Édition des paramètres disponibles dans l'application.

Une convention de nommage existe. Il faut préfixer par :

* ged\_ les paramètres qui sont spécifiques à la GED ;

* erp\_ les paramètres qui sont spécifiques à ERP ;

* option\_ les paramètres qui sont spécifiques aux options ;

* id\_ les paramètres qui contiendront un numéro d'identifiant ;

* sig\_ les paramètres qui sont spécifiques au systeme d'information géographique.


Méthode d'utilisation :

* option_contrainte_di : la valeur par défaut est 'aucune', exemple 
  d'utilisation "liste_groupe=g1,g2...;liste_ssgroupe=sg1,sg2...;service_consulte=t".
  Toutes les options sont optionnelles.
  Les options liste_groupe et liste_ssgroupe peuvent contenir une valeur unique ou
  plusieurs valeurs separees par une virgule, sans espace.
  La derniere option service_consulte permet d'ajouter une condition sur le champ
  du meme nom. Il peut prendre t (Oui) ou f (Non) comme valeur.


Gestion Des Utilisateurs
########################


.. _administration_profil:

===========
Les profils
===========

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Profil`)

Édition des profils présentes dans l'application.

.. _administration_droit:

==========
Les droits
==========

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Droit`)

Édition des droits présentes dans l'application.

.. _administration_utilisateur:

================
Les utilisateurs
================

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Utilisateur`)

Édition des utilisateurs présentes dans l'application.

.. _administration_annuaire:

==========
L'annuaire
==========

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Annuaire`)

Gestion des utilisateurs grâce à un LDAP.

Tableaux de Bord
################


.. _administration_widget:

===========
Les widgets
===========

(:menuselection:`Administration --> Tableaux De Bord --> Widget`)

Widget pour les tableaux de bord.

.. _administration_composition:

===========
Composition
===========

(:menuselection:`Administration --> Tableaux De Bord --> Composition`)

Menu de composition du tableau de bord des utilisateurs.

Options Avancées
################


.. _administration_sousetat:

==============
Les sous-états
==============

(:menuselection:`Administration --> Options Avancées --> Sous États`)

Les sous-états des requêtes SQL.

.. _administration_omrequete:

===============
Les requêtes om
===============

(:menuselection:`Administration --> Options Avancées --> Om Requête`)

Les requêtes SQL des éditions.

.. _administration_import:

===========
Les imports
===========

(:menuselection:`Administration --> Options Avancées --> Import`)

Import des données au format CSV.


.. _administration_generateur:

=============
Le générateur
=============

(:menuselection:`Administration --> Options Avancées --> Générateur`)

Le générateur de fichier de l'application.
