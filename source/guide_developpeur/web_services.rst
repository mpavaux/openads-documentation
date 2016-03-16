.. _web_services_rest:

############
Web Services
############


.. _web_services_ressource_maintenance:

Ressource "maintenance"
#######################

================================================
Synchronisation des utilisateurs via un annuaire
================================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
          "module": "user"
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...


==============================================
Traitement des retours de consultation périmés
==============================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
          "module": "consultation"
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...


========================================
Traitement des événements suivant tacite
========================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
          "module": "instruction"
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...


==========================================================
Importation des documents numérisés
==========================================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
            "module": "import",
            "data": {
                // Ces deux paramètres sont facultatifs
                "Todo" : "chemin_dossier_source", // ou "" pour utiliser le chemin dans la configuration
                "Done" : "chemin_dossier_destination" // ou "" pour utiliser le chemin dans la configuration   
            }
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...


==========================================================
Purge des documents numérisés
==========================================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
            "module": "purge",
            "data": {
                // Ces trois paramètres sont facultatifs
                "dossier": "chemin_dossier", // ou "" pour utiliser le chemin dans la configuration
                "nombre_de_jour": nombre_de_jour, // ou "" pour n'imposer aucunes limites,
                "dossier_vide" : true // ou false pour supprimer le répertoire si celui-ci est vide.
            }
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...


==========================================================
Mise à jour de l'état des dossiers d'autorisations périmés
==========================================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
            "module": "update_dossier_autorisation",
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...


==========================================================
Synchronisation des contraintes depuis le SIG
==========================================================

.. http:post:: /services/rest_entry.php/maintenance

   **Requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/maintenance HTTP/1.1

      [
        {
            "module": "contrainte",
        }
      ]

   :statuscode 200: ...
   :statuscode 404: ...



.. _web_services_ressource_arretes:

Ressource "arretes"
###################

Cette ressource permet de mettre à jour le numéro d'arrêté d'un dossier 
d'instruction.

=================
Vocabulaire `PUT`
=================

*URI* :

`services/rest_entry.php/arretes/<ID>`




.. _web_services_ressource_consultations:

Ressource "consultations"
#########################

Cette ressource permet de mettre à jour une consultation d'openADS dont le retour 
d'avis du service aura été saisie dans son propre logiciel (ERP).

=================
Vocabulaire `PUT`
=================

*URI* :

`services/rest_entry.php/consultations/<ID>`

*Exemples de contenu* :

Retour d'avis d'une consultation sans fichier :

.. code-block:: javascript

    {
        "date_retour": "14/01/2012",
        "avis": "Favorable"
    }


Retour d'avis d'une consultation avec fichier :

.. code-block:: javascript

    {
        "date_retour": "14/01/2012",
        "avis": "Favorable",
        "fichier_base64": "JVBERi0xLjQKJcOkw7zDtsOfCjIgM",
        "nom_fichier": "plop.pdf"
    }



.. _web_services_ressource_dossier_autorisations:

Ressource "dossier_autorisations"
#################################

Cette ressource permet d'interfacer un dossier d'autorisation.

========================================
Arrêté effectué sur l'AT (Échange n°208)
========================================


.. http:put:: /services/rest_entry.php/dossier_autorisations/(string:dossier_autorisation_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /services/rest_entry.php/dossier_autorisations/PC0130551601234 HTTP/1.1

        {
            "arrete_effectue":"some",
            "date_arrete":"04/06/2014"
        }

   :statuscode 200: ...
   :statuscode 404: ...


===================================================================
Mise à jour du statut ouvert de l'établissement ERP (Échange n°202)
===================================================================

.. code-block:: javascript

    {
        "erp_ouvert":"12345",
        "date_arrete":"some"
    }

============================================================
Mise à jour du numéro de l'établissement ERP (Échange n°201)
============================================================

.. code-block:: javascript

    {
        "numero_erp":"12345",
        "avis":"some"
    }


=================
Vocabulaire `GET`
=================

*URI* :

`services/rest_entry.php/dossier_autorisations/<ID>`



.. _web_services_ressource_dossier_instructions:

Ressource "dossier_instructions"
################################

Cette ressource permet d'interfacer un dossier d'instruction.

=============
Échange n°211
=============

.. http:put:: /services/rest_entry.php/dossier_instructions/(string:dossier_instruction_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /services/rest_entry.php/dossier_instructions/PC0130551601234P0 HTTP/1.1

        {
            "message":"clos",
            "date":"27/10/2013"
        }

   :statuscode 200: ...
   :statuscode 404: ...

=============
Échange n°210
=============

.. http:put:: /services/rest_entry.php/dossier_instructions/(string:dossier_instruction_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /services/rest_entry.php/dossier_instructions/PC0130551601234P0 HTTP/1.1

        {
            "message":"complet",
            "date":"27/10/2013"
        }

   :statuscode 200: ...
   :statuscode 404: ...


.. _web_services_ressource_messages:

Ressource "messages"
####################

Cette ressource permet d'interfacer un message.

=============
Échange n°204
=============

.. http:post:: /services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/messages HTTP/1.1

        {
            "type": "Mise à jour de complétude ERP ACC",
            "date": "16/06/2014 14:12",
            "emetteur": "John Doe",
            "dossier_instruction": "PD12R0001",
            "contenu": {
                "Complétude ERP ACC": "non",
                "Motivation Complétude ERP ACC": "Lorem ipsum dolor sit amet..."
            }
        }

   :statuscode 200: ...
   :statuscode 404: ...


=============
Échange n°205
=============

.. http:post:: /services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/messages HTTP/1.1

        {
            "type": "Mise à jour de complétude ERP SECU",
            "date": "16/06/2014 14:12",
            "emetteur": "John Doe",
            "dossier_instruction": "PD12R0001",
            "contenu": {
                "Complétude ERP SECU": "oui",
                "Motivation Complétude ERP SECU": "Lorem ipsum dolor sit amet..."
            }
        }

   :statuscode 200: ...
   :statuscode 404: ...


=============
Échange n°206
=============

.. http:post:: /services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/messages HTTP/1.1

        {
            "type": "Mise à jour de qualification",
            "date": "16/06/2014 14:12",
            "emetteur": "John Doe",
            "dossier_instruction": "PD12R0001",
            "contenu": {
                "Confirmation ERP": "oui",
                "Type de dossier ERP": "Lorem ipsum dolor sit amet...",
                "Catégorie de dossier ERP": "Lorem ipsum dolor sit amet..."
            }
        }

   :statuscode 200: ...
   :statuscode 404: ...


=============
Échange n°207
=============

.. http:post:: /services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /services/rest_entry.php/messages HTTP/1.1

        {
            "type": "Dossier à enjeux ERP",
            "date": "16/06/2014 14:12",
            "emetteur": "John Doe",
            "dossier_instruction": "PD12R0001",
            "contenu": {
                "Dossier à enjeux ERP" : "oui"
            }
        }

   :statuscode 200: ...
   :statuscode 404: ...

