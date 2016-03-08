.. _installation_parametrage:

############################################
Installation et paramétrage de l'application
############################################

.. _document_numerise:

===========================================
Documents numérisés ou reprise de l'arriéré
===========================================

Pour utiliser la fonctionnalité de récupération automatique de document numérisé, il est nécessaire d'activer l'option **option_digitalization_folder**, pour ce faire il suffit d'ajouter l'option dans le fichier **dyn/config.inc.php**.

L'emplacement des documents doit être, également, spécifié dans le fichier **dyn/config.inc.php** avec le paramètre **digitalization_folder_path**. Ce répertoire devra obligatoirement contenir deux sous-répertoires **Todo** et **Done**, le premier permettant de stocker les documents à traiter et le second qui permet de consulter les documents traités.

.. code-block:: php

    $config['option_digitalization_folder'] = true;
    $config['digitalization_folder_path'] = '../var/digitalization/';

L'opérateur qui numérise les documents devra donc déposer les documents dans le répertoire **Todo** qui possédera un sous-répertoire nommé de la même façon que le dossier d'instruction lié. Par exemple, pour le dossier d'instruction **AT 013055 12 00001P0**, on aura un dossier nommé **AT0130551200001.P0**.

Exemple d'arborescence :

.. code-block:: bash

    var
    └── digitalization
        ├── Done
        │   └── CU0000001600011.P0
        └── Todo
            ├── AT0000001600013.P0
            │   ├── 20160101AUTPCP-1.pdf
            │   └── 20160101AUTPCP.pdf
            └── PC0000001600020.M02
                └── 20160206DGPA01.pdf

Un service automatique (CRON) se chargera de traiter ces documents : les enregistrer dans le système de stockage prédéfini ainsi que les lier au dossier d'instruction dans openADS.

Les répertoires des documents traités sont ensuite déplacés dans le répertoire **Done** pour être supprimés par un autre service automatique.
