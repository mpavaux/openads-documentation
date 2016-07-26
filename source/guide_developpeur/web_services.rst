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

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "user"
      }

   **Exemples de réponse** :

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: text/javascript

      {
        "http_code": 200,
        "http_code_message": "200 OK",
        "message": "Synchronisation terminée."
      }

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: text/javascript

      {
        "http_code": 200,
        "http_code_message": "200 OK",
        "message": "L'option 'annuaire' n'est pas configurée."
      }

   .. sourcecode:: http

      HTTP/1.1 500 Internal Server Error
      Content-Type: text/javascript

      {
        "http_code": 500,
        "http_code_message": "500 Internal Server Error",
        "message": "Erreur interne"
      }

   :statuscode 200: Tout s'est déroulé correctement.
   :statuscode 500: Erreur interne.


==============================================
Traitement des retours de consultation périmés
==============================================

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "consultation"
      }

   **Exemple de réponse** :

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: text/javascript

      {
        "http_code": 200,
        "http_code_message": "200 OK",
        "message": "Aucune mise a jour."
      }



========================================
Traitement des événements suivant tacite
========================================

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "instruction"
      }



==========================================================
Importation des documents numérisés
==========================================================

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "import",
        "data": {
          // Ces deux paramètres sont facultatifs
          "Todo" : "chemin_dossier_source", // ou "" pour utiliser le chemin dans la configuration
          "Done" : "chemin_dossier_destination" // ou "" pour utiliser le chemin dans la configuration   
        }
      }



==========================================================
Purge des documents numérisés
==========================================================

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "purge",
        "data": {
          // Ces trois paramètres sont facultatifs
          "dossier": "chemin_dossier", // ou "" pour utiliser le chemin dans la configuration
          "nombre_de_jour": nombre_de_jour, // ou "" pour n'imposer aucunes limites,
          "dossier_vide" : true // ou false pour supprimer le répertoire si celui-ci est vide.
        }
      }



==========================================================
Mise à jour de l'état des dossiers d'autorisations périmés
==========================================================

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "update_dossier_autorisation",
      }



==========================================================
Synchronisation des contraintes depuis le SIG
==========================================================

.. http:post:: /openads/services/rest_entry.php/maintenance

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/maintenance HTTP/1.1
      Host: localhost

      {
        "module": "contrainte",
      }



.. _web_services_ressource_consultations:

Ressource "consultations"
#########################

Cette ressource permet d'interfacer une consultation de service.

======================================
Retour de consultation (Échange n°209)
======================================

.. http:put:: /openads/services/rest_entry.php/consultations/(int:consultation_id)

   **Exemple de requête** : Retour d'avis d'une consultation sans fichier

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/consultations/12 HTTP/1.1
      Host: localhost

      {
        "date_retour": "14/01/2012",
        "avis": "Favorable"
      }

   **Exemple de requête** : Retour d'avis d'une consultation avec fichier

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/consultations/12 HTTP/1.1
      Host: localhost

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


.. http:put:: /openads/services/rest_entry.php/dossier_autorisations/(string:dossier_autorisation_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/dossier_autorisations/PC0130551601234 HTTP/1.1
      Host: localhost

      {
        "arrete_effectue":"some",
        "date_arrete":"04/06/2014"
      }



===================================================================
Mise à jour du statut ouvert de l'établissement ERP (Échange n°202)
===================================================================

.. http:put:: /openads/services/rest_entry.php/dossier_autorisations/(string:dossier_autorisation_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/dossier_autorisations/PC0130551601234 HTTP/1.1
      Host: localhost

      {
        "erp_ouvert":"12345",
        "date_arrete":"some"
      }

============================================================
Mise à jour du numéro de l'établissement ERP (Échange n°201)
============================================================

.. http:put:: /openads/services/rest_entry.php/dossier_autorisations/(string:dossier_autorisation_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/dossier_autorisations/PC0130551601234 HTTP/1.1
      Host: localhost

      {
        "numero_erp":"12345",
        "avis":"some"
      }


===============
(Échange n°203)
===============

.. http:put:: /openads/services/rest_entry.php/dossier_autorisations/(string:dossier_autorisation_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      GET /openads/services/rest_entry.php/dossier_autorisations/PC0130551601234 HTTP/1.1
      Host: localhost




.. _web_services_ressource_dossier_instructions:

Ressource "dossier_instructions"
################################

Cette ressource permet d'interfacer un dossier d'instruction.

=============
Échange n°211
=============

.. http:put:: /openads/services/rest_entry.php/dossier_instructions/(string:dossier_instruction_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/dossier_instructions/PC0130551601234P0 HTTP/1.1
      Host: localhost

        {
            "message":"clos",
            "date":"27/10/2013"
        }


=============
Échange n°210
=============

.. http:put:: /openads/services/rest_entry.php/dossier_instructions/(string:dossier_instruction_id)

   **Exemple de requête** :

   .. sourcecode:: http
      
      PUT /openads/services/rest_entry.php/dossier_instructions/PC0130551601234P0 HTTP/1.1
      Host: localhost

        {
            "message":"complet",
            "date":"27/10/2013"
        }


===============================
Détail de dossier d'instruction
===============================

.. http:get:: /openads/services/rest_entry.php/dossier_instructions/(string:dossier_instruction_id)

   **Exemple de requête sur dossier avec en pétionnaire principal une personne physique** :

   .. sourcecode:: http
      
      GET /openads/services/rest_entry.php/dossier_instructions/PC0130551601234P0 HTTP/1.1
      Host: localhost

        {
          "dossier_instruction": "PC0130551600001P0",
          "dossier_autorisation": "PC0130551600001",
          "terrain_adresse_voie_numero": "10",
          "terrain_adresse_lieu_dit": "Les Baïsses",
          "terrain_adresse_code_postal": "13333",
          "terrain_adresse_cedex": "13366",
          "terrain_adresse_voie": "rue du 14 juillet",
          "terrain_adresse_bp": "13380",
          "terrain_adresse_localite": "Marseille",
          "terrain_superficie": "22",
          "references_cadastrales": [
            {
              "prefixe": "202",
              "quartier": "810",
              "section": "A",
              "parcelle": "0020"
            },
            {
              "prefixe": "202",
              "quartier": "810",
              "section": "A",
              "parcelle": "0021"
            },
            {
              "prefixe": "202",
              "quartier": "810",
              "section": "A",
              "parcelle": "0022"
            }
          ],
          "dossier_autorisation_type": "Permis de construire",
          "dossier_autorisation_type_detaille": "Permis de construire pour une maison individuelle et / ou ses annexes",
          "collectivite": "MARSEILLE",
          "instructeur": "Louis Laurent",
          "division": "subdivision H",
          "etat_dossier": "dossier rejeter manque de pieces",
          "statut_dossier": "cloture",
          "date_depot_initial": "2016-07-25",
          "date_limite_instruction": "2016-09-25",
          "date_decision": "2016-07-25",
          "enjeu_urbanisme": "false",
          "enjeu_erp": "false",
          "petitionnaire_principal": {
            "demandeur": "13",
            "qualite": "particulier",
            "particulier_civilite": "Monsieur",
            "particulier_nom": "LOUIS",
            "particulier_prenom": "Daniel",
            "particulier_date_naissance": "1982-10-20",
            "particulier_commune_naissance": "Puyricard",
            "particulier_departement_naissance": "13",
            "numero": "20",
            "voie": "rue du 14 juillet",
            "complement": "Bat A2",
            "lieu_dit": "Lambda",
            "localite": "Marseille",
            "code_postal": "13013",
            "bp": "13099",
            "cedex": "13010",
            "pays": "France",
            "division_territoriale": "DH3",
            "telephone_fixe": "0406042266",
            "telephone_mobile": "0622334123",
            "indicatif": "33",
            "courriel": "d.louis@wanadoo.fr",
            "fax": "0406042270"
          },
          "donnees_techniques": {
            "co_tot_log_nb": "52",
            "co_cstr_exist": "true",
            "co_uti_pers": "true",
            "co_uti_vente": "true",
            "co_uti_loc": "true",
            "su_tot_shon_tot": "40",
            "su_avt_shon_tot": "20",
            "am_lot_max_nb": "100",
            "am_empl_nb": "23"
          }
        }


.. _web_services_ressource_messages:

Ressource "messages"
####################

Cette ressource permet d'interfacer un message.

=============
Échange n°204
=============

.. http:post:: /openads/services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/messages HTTP/1.1
      Host: localhost

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



=============
Échange n°205
=============

.. http:post:: /openads/services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/messages HTTP/1.1
      Host: localhost
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



=============
Échange n°206
=============

.. http:post:: /openads/services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/messages HTTP/1.1
      Host: localhost

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



=============
Échange n°207
=============

.. http:post:: /openads/services/rest_entry.php/messages

   **Exemple de requête** :

   .. sourcecode:: http
      
      POST /openads/services/rest_entry.php/messages HTTP/1.1
      Host: localhost

      {
        "type": "Dossier à enjeux ERP",
        "date": "16/06/2014 14:12",
        "emetteur": "John Doe",
        "dossier_instruction": "PD12R0001",
        "contenu": {
          "Dossier à enjeux ERP" : "oui"
        }
      }


