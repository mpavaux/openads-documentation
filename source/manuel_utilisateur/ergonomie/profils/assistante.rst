##########
ASSISTANTE
##########

Description
===========

Ce profil permet à un utilisateur d'assister les juristes et techniciens dans l'instruction de leurs dossiers.

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

Widget *Les contradictoires*
############################

- Présente les 5 dossier infraction les plus anciens pour lesquels:
	- La date de contradictoire est supérieure ou égale à la date du jour plus 3 semaines
	- Il n'y a pas d'événement type Annulation de contradictoire
	- Il n'y a pas d'AIT créé

ou:
	- La date de retour du contradictoire est vide
	- Il n'y a pas d'événement type Annulation de contradictoire
	- Il n'y a pas d'AIT créé

Widget *Les AIT*
################

- Visualiser les 5 dossiers d'infraction les plus récent pour lesquels il y a un AIT signé

Widget *Les audiences*
######################

- Visualiser les 5 dossiers pour lesquels une date d'audiance existe et est comprise entre le jour courant et un mois dans le future triés date d'audiance la plus proche

Widget *Les infractions non affectées*
######################################

- Visualiser les 5 dossiers infraction qui ne sont pas affectés à un Technicien les plus anciens en premier

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
