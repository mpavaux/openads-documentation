.. _guichet_unique:

##############
Guichet unique
##############

.. _guichet_unique_tableau_de_bord:

Le tableau de bord
##################

...




Les nouvelles demandes
######################

==================
Saisir une demande
==================

...


Pour un nouveau dossier
=======================

...


Pour un dossier existant
========================

...


=====================
Imprimer un récépissé
=====================

...


===================================
Lister les pétitionnaires fréquents
===================================

...


.. _guichet_unique_affichage_reglementaire:

L'affichage réglementaire
#########################

Dans les conditions prévues par arrêté du ministre chargé de l'urbanisme, un
affichage au public (aussi appelé registre) de tous les dossiers d'instruction
en cours est obligatoire. Le guichet unique doit pouvoir imprimer une
attestation de cet affichage réglementaire pour un dossier d'instruction à la
demande d'un usager.


.. _guichet_unique_affichage_reglementaire_registre:

====================
Imprimer le registre
====================

(:menuselection:`Guichet Unique --> Affichage Réglementaire --> Registre`)

Cet écran permet d'imprimer le registre d'affichage réglementaire des dossiers
d'instruction en cours. La validation de ce traitement ajoute sur chacun des
dossiers d'instruction concernés un événement d'instruction spécifique
(uniquement si c'est la première édition du dossier d'instruction) qui offre la
possibilité d'imprimer une attestation d'affichage.

Il est nécessaire pour le registre de créer un événement sur chaque dossier
d'instruction affiché dans ce dernier qui permet de générer l'attestation
d'affichage. Cet événment Ensuite l'id de cet événement doit être modifié
dans l'enregistrement 'affichage_obligatoire' de l'écran "Administration" => "Paramètre".

.. _guichet_unique_affichage_reglementaire_attestation:

======================
Imprimer l'attestation
======================

(:menuselection:`Guichet Unique --> Affichage Réglementaire --> Attestation`)

Cet écran permet d'imprimer l'attestation d'affichage réglementaire d'un dossier
d'instruction. Pour le faire, il suffit de saisir le numéro du dossier
d'instruction dans le formulaire puis de cliquer sur le bouton valider.

.. image:: guichet_unique_affichage_reglementaire_attestation_formulaire.png

Une fois le formulaire validé, trois cas de figures sont possibles :

* soit l'identifiant saisi ne correspond à aucun dossier d'instruction existant :
  
  .. image:: guichet_unique_affichage_reglementaire_attestation_message_dossier_inexistant.png

* soit le dossier d'instruction existe mais ne possède pas d'attestation
  d'affichage :
  
  .. image:: guichet_unique_affichage_reglementaire_attestation_message_dossier_jamais_affiche.png

* soit le dossier d'instruction existe et possède une attestation d'affichage,
  on obtient alors un lien vers le fichier pdf de l'attestation permettant de
  l'imprimer :
  
  .. image:: guichet_unique_affichage_reglementaire_attestation_message_lien_attestation.png


