.. _portail_citoyen:

###############
Portail citoyen
###############

Si l'option d'accès au portail citoyen détaillée dans :ref:`cette rubrique <parametrage_parametre>`
est activée, les pétitionnaires ont la possibilité de suivre l'avancement de leur demande
en temps réel par le biais du portail citoyen.

.. _portail_citoyen_adresse:

Le lien vers le portail citoyen
###############################

Depuis les éditions, afin de renseigner les pétitionnaires sur la possibilité d'accéder à un portail citoyen, il est conseillé d'utiliser la variable de remplacement **acces_citoyen**.
Cette variable est interprétée seulement si l'option d'accès au portail citoyen est activée.
Elle pourrait contenir un texte d'explication sur la connexion, par exemple "Vous pouvez consulter directement votre dossier par internet à l'adresse &acces_citoyen_adresse et en saisissant votre numéro de dossier ainsi que la clé d'accès [cle_acces_citoyen]."

La variable de remplacement **acces_citoyen_adresse** définit le lien vers le portail citoyen.
Le portail citoyen est capable d'être intégré à un site internet.

Le champ de fusion **[cle_acces_citoyen]**, étant disponible sur toutes les éditions d'instruction, permet d'afficher la clé générée automatiquement à la création du dossier. Elle se compose de quatre groupes de quatre chiffres séparés par des tirets.
Exemple : "0000-1111-2222-3333".

.. _portail_citoyen_page_acces:

Le formulaire d'accès au suivi de dossier
#########################################

Depuis le formulaire d'accès du portail citoyen.

.. image:: portail_citoyen_formulaire_acces.png

Les informations à saisir sont :

* **Numéro de dossier** : Le numéro de dossier d'autorisation ou de dossier d'instruction,
  qui apparaît sur tous les documents: récépissés, arrêtés etc.

* **Clé d'accès** : La clé d'accès au portail citoyen qui est par défaut présente sur tous
  les récépissés, sur la lettre type "information d'accès citoyen", ou encore sur la fiche
  détaillée du dossier d'instruction, dans le champ pétitionnaire.

.. _portail_citoyen_fiche:

La fiche "Suivi de mon dossier"
###############################

La visualisation contient deux blocs d'informations :

.. image:: portail_citoyen_suivi_dossier.png

- **En cours de validité** : informations des dossiers d'instructions soumis à un arrété.

    * En noir : les informations importantes en cours de validité
    * En vert : la liste des lots et leurs petitionnaire principal en cours de validité
    * En rouge : la liste des décisions en cours de validité

- **En cours d'instruction** : données du dossier d'instruction en cours d'instruction.

    * En noir : les informations importantes en cours d'instruction
    * En vert : la liste des lots et leur pétitionnaire principal en cours d'instruction
