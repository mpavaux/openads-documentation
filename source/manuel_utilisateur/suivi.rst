.. _suivi:

#####
Suivi
#####

.. _suivi_menu:

Le menu
#######

.. image:: suivi_menu.png

.. _suivi_tableau_de_bord:

Le tableau de bord
##################

(:menuselection:`Suivi --> Tableau De Bord`)

Pour l'instant le tableau de bord suivi ne comporte aucun widget.

.. _suivi_suivi_des_pieces:

Suivi des pièces
################

.. _suivi_retours_de_consultation:

================================
Saisir un retour de consultation
================================

(:menuselection:`Suivi --> Suivi Des Pièces --> Retours De Consultation`)

Les retours de consultations peuvent se faire directement depuis le module
service consulté dans lequel le service consulté accède au logiciel pour y
saisir son avis.

Les retours de consultations peuvent aussi être envoyés par courrier ou par mail
lorsque la consultation du service se fait par voie papier. Dans ce cas, les
retours de consultation sont bippés, ce qui ouvre le formulaire de mise à jour
de consultation. L'utilisateur peut alors saisir le retour de consultation,
ainsi qu'un fichier, représentant le courrier. 

Un premier écran permet de rechercher la consultation : il suffit ici de saisir
l'identifiant de la consultation pour laquelle on souhaite saisir un retour.
Par exemple grâce au scan de code barre ou simplement en saisissant manuellement
son identifiant.

.. image:: suivi_retours_de_consultation_formulaire_recherche.png

Une fois le formulaire validé, trois cas de figures sont possibles :

* soit aucune valeur n'a été saisie :
  
  .. image:: suivi_retours_de_consultation_message_aucune_saisie.png

* soit l'identifiant de la consultation ne correspond à aucune consultation
  existante :
  
  .. image:: suivi_retours_de_consultation_message_consultation_inexistante.png

* soit la consultation existe, on obtient alors un formulaire de saisie du
  retour de consultation.


.. _suivi_mise_a_jour_des_dates:

=======================
Mettre à jour les dates
=======================

(:menuselection:`Suivi --> Suivi Des Pièces --> Mise À Jour Des Dates`)

.. _suivi_envoi_lettre_rar:

================
Imprimer les RAR
================

(:menuselection:`Suivi --> Suivi Des Pièces --> Envoi Lettre RAR`)

Cet écran permet un traitement en masse d'édition des pré-imprimés RAR pour les
courriers générés dans le cadre de l'instruction. Il suffit de saisir une date
d'envoi, par défaut la date du jour, et de bipper à la douchette les courriers
concernés (ou de saisir manuellement l'identifiant du courrier). Une fois que
tous les courriers sont bippés, un bouton permet de générer le fichier PDF qui
est adapté pour être imprimé sur les pré-imprimés RAR de La Poste.

Un seul fichier contient tous les RAR dans l'ordre de bip.

Lors de la génération du fichier des RAR, la date d'envoi RAR est mise à jour
sur les événements ayant servi à générer les courriers, avec la date saisie par
l'utilisateur.

.. image:: suivi_envoi_lettre_rar_formulaire.png

Une fois le formulaire validé, quatre cas de figures sont possibles :

* soit aucune valeur n'a été saisie :
  
  .. image:: suivi_envoi_lettre_rar_message_aucune_saisie.png

* soit l'identifiant de l'événement d'instruction ne correspond à aucun
  événement d'instruction existant :
  
  .. image:: suivi_envoi_lettre_rar_message_evenement_instruction_inexistant.png

* soit l'événement d'instruction existe et possède déjà une date d'envoi RAR qui
  est différente de la date passée en paramètre :
  
  .. image:: suivi_envoi_lettre_rar_message_evenement_instruction_deja.png

* soit l'événement d'instruction existe et n'a pas de date d'envoi RAR, on
  obtient alors un lien vers le fichier pdf permettant d'imprimer les
  pré-imprimés RAR :
  
  .. image:: suivi_envoi_lettre_rar_message_evenement_instruction_ok.png

.. _suivi_bordereaux:

==========
Bordereaux
==========

(:menuselection:`Suivi --> Suivi Des Pièces --> Bordereaux`)

Cet écran permet d'imprimer un bordereau permettant de lister tous les
documents transmis à une date en particulier. Par exemple :
* Bordereau des décisions,
* Bordereau des avis du Maire au Préfet,
* Bordereau contrôle de légalité,
* Bordereau des courriers à la signature du Maire qui ne sont pas des décisions.

L'écran permet de saisir la date d'envoi, qui est par défaut la date du jour et
de sélectionner le bordereau souhaité dans la liste des bordereaux.

.. image:: suivi_bordereaux_formulaire.png

Une fois le formulaire validé, trois cas de figures sont possibles :

* soit aucune date n'a été saisie :
  
  .. image:: suivi_bordereaux_message_aucune_date.png

* soit aucun bordereau n'a été sélectionné :
  
  .. image:: suivi_bordereaux_message_aucun_bordereau.png

* soit la saisie est correcte, on obtient alors un lien vers le fichier pdf du
  bordereau permettant de l'imprimer :
  
  .. image:: suivi_bordereaux_message_telechargement.png


.. _suivi_commissions:

Commissions
###########

.. _suivi_commissions_gestion:

=====================
Gérer les commissions
=====================

(:menuselection:`Suivi --> Commissions --> Gestion`)

Créer une commission
====================


Planifier/retirer un dossier
============================


Planifier un dossier spécifique
===============================


.. _suivi_commissions_demandes:

===============================
Lister les demandes de passages
===============================

(:menuselection:`Suivi --> Commissions --> Demandes`)



