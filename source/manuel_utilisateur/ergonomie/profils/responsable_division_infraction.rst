###############################
RESPONSABLE DIVISION INFRACTION 
###############################

Description
===========

Ce profil permet à un utilisateur d'instruire les dossiers d'infraction.

Il va leur permettre :

- d'instruire les dossiers d'instruction qui leurs sont affecté.
- d'ajouter des demandes de passage en commission
- de consulter des services
- d'accéder aux dossiers liés
- de répondre directement depuis le logiciel aux consultations de service qui leurs sont adressés ;
- de voir les avis qui avaient été rendus ;
- de faire des exports CSV ;


L'utilisateur qui a ce profil doit forcément être rattaché un instructeur.

Fonctionnalités disponibles
===========================

Tableau de bord
---------------

.. image:: dashboard_instrserv.png

Widget *Infos profil*
#####################

- Visualiser les informations du profil de l'utilisateur connecté

Widget *Nouveau dossier*
########################

- Ajouter un nouveau dossier

Widget *Recherche accès direct*
###############################

- Rechercher un dossier d'instruction par son identifiant

Widget *Mes messages*
#####################

- Visualiser la liste des messages non lu des dossiers d'instruction affecté à l'utilisateur
- Accéder aux messages non lu des dossiers d'instruction affecté à l'utilisateur

Widget *Les AIT*
################

- Visualiser les 5 dossiers d'infraction les plus récent pour lesquels il y a un AIT signé

Widget *Les infractions non affectées*
######################################

- Visualiser les 5 dossiers infraction qui ne sont pas affectés à un Technicien les plus anciens en premier

Widget *Alerte Visite*
######################

- Visualiser les 5 dossiers infraction pour lesquels la date de réception est dépassée depuis plus de 3 mois et pour lesquels la date de premiere visite est nulle triés par date de réception la plus lointaine

Widget *Alerte Parquet*
#######################

- Visualiser les 5 dossiers infraction pour lesquels la date de réception est dépassée depuis plus de 9 mois et pour lesquels la date de de tansmission au parquet est nulle triés par date de réception la plus lointaine

Menu
----

.. image:: menu_instrserv.png

Rubrique *Autorisation*
-----------------------

Actions identiques à celles du profil "instructeur" (cf :ref:`Rubrique autorisation<profil_instructeur_rubrique_autorisation>`)

Rubrique *Instruction*
----------------------

Actions identiques à celles du profil "instructeur" (cf :ref:`Rubrique instruction<profil_instructeur_rubrique_instruction>`)

Rubrique *Demande D'avis*
-------------------------

Actions identiques à celles du profil "service consulté" (cf :ref:`Rubrique demande d'avis<profil_service_consulte_rubrique_demande_avis>`)
