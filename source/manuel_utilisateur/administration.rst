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

* **option_sig** : la valeur par défaut est *aucun*. Les valeurs possibles sont
  *sig_externe*, *sig_interne* ou *aucun*.
* **option_referentiel_arrete** : la valeur par défaut est *false*. Les valeurs 
  possibles sont *true* ou *false*.
* **option_localisation** : la valeur par défaut est *false*. Les valeurs possibles 
  sont *true* ou *false*.
* **option_erp** : la valeur par défaut est *false*. Les valeurs possibles sont 
  *true* ou *false*.
* **option_contrainte_di** : la valeur par défaut est *aucun*, exemple 
  d'utilisation "liste_groupe=g1,g2...;liste_ssgroupe=sg1,sg2...;service_consulte=t".
  Toutes les options sont optionnelles.
  Les options liste_groupe et liste_ssgroupe peuvent contenir une valeur unique 
  ou plusieurs valeurs séparées par une virgule, sans espace.
  La dernière option service_consulte permet d'ajouter une condition sur le champ
  du même nom. Il peut prendre t (Oui) ou f (Non) comme valeur.
* **option_afficher_division** : la valeur par défaut est *false*. Les valeurs 
  possibles sont *true* ou *false*.
* **option_arrondissement** : la valeur par défaut est *false*. Les valeurs 
  possibles sont *true* ou *false*.
  Cette option indique si la commune est divisée en arrondissements.
* **option_instructeur_division_numero_dossier** : la valeur par défaut est *false*. Les valeurs 
  possibles sont *true* ou *false*.
  Cette option indique si le numéro de dossier tient compte de la vision de l'instructeur auquel il est affecté.
* **portail_acces_citoyen** : si cette option est activée, l'ajout de nouvelle demande génère une clé d'accès au portail citoyen pour les pétitionnaires. Cette clé est affichée sur le dossier d'instruction et il devient possible de générer ou régénérer une clé d'accès depuis celui-ci. Les valeurs possibles sont *true* ou *false* (par défaut *false*).

La suppression d'une option entraîne la désactivation des fonctionnalités liées 
à l'option.

Gestion Des Utilisateurs
########################


.. _administration_profil:

===========
Les profils
===========

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Profil`)

Édition des profils présents dans l'application.

.. _administration_droit:

==========
Les droits
==========

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Droit`)

Édition des droits présents dans l'application.

.. _administration_utilisateur:

================
Les utilisateurs
================

(:menuselection:`Administration --> Gestion Des Utilisateurs --> Utilisateur`)

Édition des utilisateurs présents dans l'application.

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

Un widget, contraction de window (fenêtre) et gadget, est un composant du
tableau de bord proposant des informations.

Son paramètrage nécessite la saisie de quatre champs :

* **libellé** : le titre du widget
* **type** : *file* lorsqu'il s'agit d'un script ou *web* lorsqu'il s'agit d'un
  appel à un web service
* **script** ou **lien** selon respectivement le type *file* ou *web* : nom du
  script ou URL du web service
* **arguments** ou **texte** selon respectivement le type *file* ou *web* :
  paramètres du script ou texte du widget (iframe, JavaScript, AJAX ...)

Seuls les widgets de type *file* sont utilisés dans openADS.

Les arguments sont déclarés ainsi :

::

  argument1=valeur1
  argument2=valeur2

Les scripts disponibles sont les suivants :

dossiers_limites
================

Ce widget permet d'afficher les dossiers d'instruction tacites dont la date
limite est dans moins de X jours.
Seuls les 10 premiers résultats sont affichés. Un lien *Voir +* permet d'accéder
au listing complet.
Davantage d'informations sont disponibles :ref:`ici<dossiers_limites>`.

Trois arguments facultatifs faisant office de critères sont paramétrables :

* **filtre** [par défaut *instructeur*] - les filtres disponibles sont *aucun*,
  *division* et *instructeur*
* **nombre_de_jours** [par défaut *15*] - délai en jours avant la date limite à
  partir de laquelle on souhaite voir apparaître les dossiers
* **codes_datd** [par défaut tous les types sont affichés] - liste des types de
  dossiers à afficher séparés par un point-virgule. exemple : *PCI;PCA;DPS;CUa;CUb*

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

(:menuselection:`Administration --> Options Avancées --> Import spécifique`)

Import des données au format spécifique.
========================================

Ce menu permet d'accéder au module d'import des données au format ADS 2007.

Dans le "Module Import ADS 2007" :

- importer le fichier csv
- choisir le séparateur (, ou ;)
- valider le formulaire d'import

.. NOTE:: L'encodage du fichier csv à importer doit être ISO-8859-15.
          
          Seuls les séparateurs , ou ; sont admis.
          
          Les références cadastrales doivent être séparées par une virgule.
  
Une fois le chargement terminé un récapitulatif des traitements effectués est affiché, dans celui-ci un fichier de rejet est disponible.

.. NOTE:: Si dans un dossier une date de decision est définie mais qu'il n'a pas de nature de decision alors le dossier est implicitement accordé.

Ce fichier de rejet contient toutes les lignes du csv importées qui sont en erreur. Les erreurs sont ajoutées en fin de ligne dans une nouvelle colonne.

Exemple d'erreurs typiques :

- Le code INSEE n'est pas paramétré : un code INSEE doit être défini pour chaque commune dans les paramètres.
- Dossiers non clôturés (pas de date d'accord/rejet/refus tacite ou de date de décision).
- Mauvais format des références cadastrales.
- Dossier avec date de décision mais pas de nature de décision.

Après correction ce ficher de rejet peut être ré-importé.

Des dossiers importés peuvent être mis à jour hors d'openADS, lors du prochain import les données du dossiers et des données techniques seront mises à jour. Attention, les demandeurs ne sont pas mis à jour.


.. _administration_generateur:

=============
Le générateur
=============

(:menuselection:`Administration --> Options Avancées --> Générateur`)

Le générateur de fichiers de l'application.
