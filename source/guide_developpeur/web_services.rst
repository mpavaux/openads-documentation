.. _web_services_rest:

############
Web Services
############

Entrants (ERP → ADS)
####################

.. _web_services_rest_arretes:

===================
Ressource "arretes"
===================

Cette ressource permet de mettre à jour le numéro d'arrêté d'un dossier 
d'instruction.

.. _web_services_rest_consultations:

=========================
Ressource "consultations"
=========================

Cette ressource permet de mettre à jour une consultation d'openADS dont le retour 
d'avis du service aura été saisie dans son propre logiciel (ERP).

.. _web_services_rest_dossier_autorisations:

=================================
Ressource "dossier_autorisations"
=================================

Cette ressource va mettre à jour les données d'un dossier d'autorisation dans 
différent cas : ouverture de l'ERP (assignation d'un numéro ERP au bâtiment) et
arrêté d'ouverture signé.

On pourra à partir de cette ressource consulter certaines des données 
des dossiers d'autorisations.

.. _web_services_rest_dossier_instructions:

================================
Ressource "dossier_instructions"
================================

Cette ressource sert à signaler qu'un dossier d'instruction de type AT est 
complété ou clôturé.

Pour que cette ressource ajoute au dossier d'instruction ciblé le bon événement
de complétude ou de clôture, il faut renseigner les identifants des événements dans 
les paramètres 'id_evenement_completude_at' et 'id_evenement_cloture_at'.

(:menuselection:`Administration --> Paramètre`)

.. _web_services_rest_maintenance:

=======================
Ressource "maintenance"
=======================

Les actions de cette ressource sont expliquées dans 
:ref:`Liés à des CRONs <web_services_rest_lies_a_des_crons>`

.. _web_services_rest_messages:

====================
Ressource "messages"
====================

Cette ressource permet d'indiquer au service ADS qu'un dossier d'instruction est
complet ou pas, d'indiquer d'un dossier a été qualifié ou que certains dossiers 
d'instruction sont à enjeux.

Sortants (ADS → ERP)
####################

============
Consultation
============

Une demande d'instruction d'un dossier d'instruction de type PC pour un ERP 
et l'ajout d'une consultation ERP pour conformité sur un dossier d'instruction 
de type PC déclenchent l'envoi d'un message vers ERP.

===========
Instruction
===========

Les actions qui déclenchent l'envoi d'un message vers le référentiel arrêté sont :

- l'ajout de l'événement d'instruction d'arrêté sur un dossier d'instruction de type PC ;

- l'ajout de l'événement d'instruction d'arrêté sur un dossier d'instruction.

Une fois la décision de conformité rendue un message est envoyé vers ERP.

=====
Pièce
=====

L'ajout de pièces à un dossier d'instruction de type AT déclenche l'envoi d'un 
message vers ERP.

=====================
Dossier d'instruction
=====================

Les actions qui déclenchent l'envoi d'un message vers ERP sont :

- le dépôt d'un dossier d'instruction de type DAT ;

- la demande d'ouverture d'un ERP sur un dossier d'instruction de type DAT ;

- si on annule la demande précédente ;

- la demande d'ouverture d'un ERP sur un dossier d'instruction de type PC ;

- si un dossier d'instruction de type DAT a besoin de la qualification URBA ;

- la demande de complétude d'un dossier d'instruction de type PC pour un ERP ;

- la demande de qualification d'un dossier d'instruction de type PC pour un ERP.

.. _web_services_rest_lies_a_des_crons:

Liés à des CRONs
################

Certaines fonctionnalités de l'application ont besoin d'être effectuées de 
manière journalière. Elles ont été liées à un CRON.

Cinq CRONs différents ont été configurés.

Le premier sert à mettre à jour les utilisateurs de l'application via un LDAP.

Le second met à jour les consultations dont la date tacite est passée.

Le troisième met à jour les dossiers d'instruction dont la date tacité est 
passée.

Le quatrième gère la péremption des dossiers d'autorisation.

Le dernier synchronise les contraintes du SIG avec celles de l'application.
