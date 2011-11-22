.. _migration:

#########
migration 
#########



Principes





Requetes

Ajout de champs supplementaire ::


    alter dossier add description text not null;
    -- cas particulier de description dans temp1
    update dossier set description  = temp1






