.. _migration:

#########
migration 
#########



Principes pour le Transfert des dossier

- creer une table temporaire avec des champs textes a la place des dates et sans integrite referentielle (exemple ci dessous)

- mettre a niveau les donnees à l aide des requêtes cidessous

    regler les problemes de cles secondaire    

    regler les problemes de date

- faire une sauvegarde de la table temporaire et intégrer dans openFoncier

- mettre à jour les sequences


scrpts sql migration ARLES  ::
    
    -- ----------------
    -- dossier
    -- ----------------

    CREATE TABLE dossier (
      dossier varchar(12),
      nature varchar(2),
      annee char(2)  NOT NULL default '',
      etat varchar(20),
      "types" varchar(12)  NOT NULL default '',
      objet_dossier varchar(20)  NOT NULL default '',
      instructeur  varchar(20) ,
      date_demande varchar(20) ,
      date_depot varchar(20) ,
      date_complet varchar(20) ,
      date_rejet varchar(20) ,
      date_notification_delai varchar(20) ,
      delai integer NOT NULL default '0',
      date_limite varchar(20) ,
      accord_tacite char(3)  NOT NULL default '',
      date_decision varchar(20) ,
      avis varchar(2),
      date_validite varchar(20) ,
      date_chantier varchar(20) ,
      date_achevement varchar(20) ,
      date_conformite varchar(20) ,
      demandeur_civilite varchar(10),
      demandeur_nom varchar(80)  NOT NULL default '',
      demandeur_societe varchar(80)  NOT NULL default '',
      demandeur_adresse varchar(80)  NOT NULL default '',
      demandeur_cp varchar(5)  NOT NULL default '',
      demandeur_ville varchar(30)  NOT NULL default '',
      demandeur_pays varchar(40)  NOT NULL default '',
      demandeur_telephone varchar(14)  NOT NULL default '',
      demandeur_email varchar(40)  NOT NULL default '',
      demandeur_categorie  varchar(20) ,
      delegataire char(3)  NOT NULL default '',
      delegataire_civilite varchar(10),
      delegataire_nom varchar(80)  NOT NULL default '',
      delegataire_societe varchar(80)  NOT NULL default '',
      delegataire_adresse varchar(80)  NOT NULL default '',
      delegataire_cp varchar(5)  NOT NULL default '',
      delegataire_ville varchar(30)  NOT NULL default '',
      delegataire_pays varchar(40)  NOT NULL default '',
      delegataire_telephone varchar(14)  NOT NULL default '',
      delegataire_email varchar(40)  NOT NULL default '',
      terrain_numero varchar(4)  NOT NULL default '',
      terrain_numero_complement varchar(5)  NOT NULL default '',
      terrain_adresse varchar(80)  NOT NULL default '',
      terrain_adresse_complement varchar(80)  NOT NULL default '',
      terrain_cp varchar(5)  NOT NULL default '',
      terrain_ville varchar(30)  NOT NULL default '',
      architecte  varchar(20),
      terrain_surface  varchar(20),
      terrain_surface_calcul  varchar(20),
      rivoli varchar(4) NOT NULL default '',
      travaux integer,
      parcelle varchar(20) NOT NULL default '',
      pos varchar(10) NOT NULL default '',
      sig varchar(3) NOT NULL default '',
      batiment_nombre varchar(20),
      logement_nombre varchar(20),
      shon varchar(20) ,
      shon_calcul varchar(20),
      shob varchar(20),
      lot varchar(20) ,
      hauteur varchar(20),
      piece_nombre varchar(20),
      amenagement varchar(12)  NOT NULL default '',
      parcelle_lot integer,
      parcelle_lot_lotissement varchar(60),
      temp1 varchar(100)  NOT NULL default '',
      temp2 varchar(100)  NOT NULL default '',
      temp3 varchar(100)  NOT NULL default '',
      temp4 varchar(100)  NOT NULL default '',
      temp5 varchar(100)  NOT NULL default '',
      servitude text,
      PRIMARY KEY  (dossier)
    )

    -- pb de longueur
    -- mise  a 90 les champs 80
    -- mise a 110 temp1 
    -- amenagement : mettre null


    Ajout de champs supplementaire :

    alter dossier add description text not null;
    -- cas particulier de description dans temp1
    update dossier set description  = temp1

    -- cle secondaire numerique = 0 a mettre a null
    update dossier set instructeur = null where instructeur = '0'; 
    update dossier set travaux = null where travaux = '0'; 
    update dossier set architecte = null where architecte = '0';
    -- cle secondaire alpha vide a mettre a null
    update dossier set demandeur_civilite = null where demandeur_civilite = '';
    update dossier set delegataire_civilite = null where delegataire_civilite = '';
    update dossier set amenagement = null where amenagement = '';
    update dossier set avis = null where avis = '';
    update dossier set demandeur_categorie = null where demandeur_categorie = '';
    update dossier set etat = null where etat = ' ';
    -- eliminer les dates 0000-00-00
    update dossier set date_demande = null where date_demande = '0000-00-00';
    update dossier set date_complet = null where date_complet = '0000-00-00';
    update dossier set date_rejet = null where date_rejet = '0000-00-00';
    update dossier set date_notification_delai = null where date_notification_delai = '0000-00-00';
    update dossier set date_limite = null where date_limite = '0000-00-00';
    update dossier set date_decision = null where date_decision = '0000-00-00';
    update dossier set date_validite = null where date_validite = '0000-00-00';
    update dossier set date_chantier = null where date_chantier = '0000-00-00';
    update dossier set date_achevement = null where date_achevement = '0000-00-00';
    update dossier set date_conformite = null where date_conformite = '0000-00-00';

    -- champs numerique vide
    update dossier set batiment_nombre = null where batiment_nombre = '';
    -- probleme de cle secondaire
    update dossier set instructeur = 5 where instructeur = 4;
    -- erreur de base sur etat vide
    update dossier set etat = 'initialiser' where dossier='PC10R0070'
    update dossier set nature = 'PC' where dossier = 'PC10R0070'

    -- =========
    -- terrain
    -- =========
    -- La clé (dossier)=(PC07R0001) DP11R0779 DP11R0780 n'est pas présente dans la table « dossier ».
    -- cle vide dans ligne 137 ('AB0044', 'SCHIAVETTI Hervé');

    -- =============================
    -- destination shon
    -- =============================
    -- pb de shon calcule -> quelle shon mettre en chiffre ? suivant quel critere ?

    -- ==============================
    -- consultation
    -- ==============================
    CREATE TABLE consultation (
      consultation integer,
      dossier varchar(12),
      service varchar(5),
      date_envoi varchar(20) ,
      date_retour varchar(20) ,
      avis varchar(2),
      date_limite varchar(20) ,
      PRIMARY KEY  (consultation)
    );
    -- date 0000-00-00
    update consultation set date_envoi = null where date_envoi = '0000-00-00';
    update consultation set date_envoi = null where date_envoi = '0000-01-00'; 
    update consultation set date_retour = null where date_retour = '0000-00-00';
    update consultation set date_limite = null where date_limite = '0000-00-00';
     update consultation set date_limite = null where date_limite = '0000-01-00';
    update consultation set date_limite = null where date_limite = '0000-04-00';
    update consultation set date_limite = null where date_limite = '0000-05-00';
    -- cle alpha vide
    update consultation set avis = null where avis = '';

    -- =============================
    -- instruction
    -- =============================

    CREATE TABLE instruction (
      instruction integer,
      destinataire varchar(30)  NOT NULL default '',
      datecourrier varchar(20) ,
      evenement integer,
      lettretype varchar(40)  NOT NULL default '',
      complement text NOT NULL,
      complement2 text  NOT NULL,
      dossier varchar(12),
      "action" varchar(20),
      delai integer,
      etat varchar(20),
      accord_tacite char(3)  NOT NULL default '',
      delai_notification integer NOT NULL default '0',
      avis varchar(2),
      archive_delai int8 NOT NULL default '0',
      archive_date_complet varchar(20) ,
      archive_date_rejet varchar(20) ,
      archive_date_limite varchar(20) ,
      archive_date_notification_delai varchar(20) ,
      archive_accord_tacite char(3)  NOT NULL default '',
      archive_etat varchar(20)  NOT NULL default '',
      archive_date_decision varchar(20) ,
      archive_avis varchar(20)  NOT NULL default '',
      archive_date_validite varchar(20) ,
      archive_date_achevement varchar(20) ,
      archive_date_chantier varchar(20) ,
      archive_date_conformite varchar(20) ,
      complement3 text,
      complement4 text,
      complement5 text,
      complement6 text,
      complement7 text,
      complement8 text,
      complement9 text,
      complement10 text,
      complement11 text,
      complement12 text,
      complement13 text,
      complement14 text,
      complement15 text,
      PRIMARY KEY  (instruction)
    );

    -- eliminer les dates 0000-00-00
    update instruction set archive_date_complet = null where archive_date_complet = '0000-00-00';
    update instruction set archive_date_rejet = null where archive_date_rejet = '0000-00-00';
    update instruction set archive_date_limite = null where archive_date_limite = '0000-00-00';
    update instruction set archive_date_notification_delai = null where archive_date_notification_delai = '0000-00-00';
    update instruction set archive_date_decision = null where archive_date_decision = '0000-00-00';
    update instruction set archive_date_validite = null where archive_date_validite = '0000-00-00';
    update instruction set archive_date_achevement = null where archive_date_achevement = '0000-00-00';
    update instruction set archive_date_chantier = null where archive_date_chantier = '0000-00-00';
    update instruction set archive_date_conformite = null where archive_date_conformite = '0000-00-00';

    -- cle secondaire
    update instruction set avis = null where avis = '';
    -- update instruction set action = null where action = ''; --0
    -- update instruction set dossier = null where dossier = ''; -- 00
    -- update instruction set evenement = null where evenement = ''; --0
    update instruction set etat = null where etat = '';
    -- pb utf8
    -- remplacer ? dans le texte
    
    -- ----------------------------------
    -- transferer en base reelle
    -- ----------------------------------
    
    -- mettre a jour les sequences (nombre a modifier)
    ALTER SEQUENCE dossier_dp_seq RESTART WITH 604;
    ALTER SEQUENCE dossier_pc_seq RESTART WITH 344;
    ALTER SEQUENCE dossier_pa_seq RESTART WITH 8;
    ALTER SEQUENCE dossier_pd_seq RESTART WITH 5;
    ALTER SEQUENCE blocnote_seq RESTART WITH 14;
    ALTER SEQUENCE consultation_seq RESTART WITH 13652;
    ALTER SEQUENCE destination_shon_seq RESTART WITH 1114;
    ALTER SEQUENCE instruction_seq RESTART WITH 17969;
    ALTER SEQUENCE terrain_seq RESTART WITH 5355;
    
    
    
    
    
    
    


