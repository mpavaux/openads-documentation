.. _sitadel:

################
L'export Sitadel
################


Il est proposé de décrire le traitement de transfert à la DREAL appellé SITADEL.

En effet les communes sont tenus de transmettre à la Cellule de la Direction
Régionale de l'environnement et du logement (DREAL) les informations des ADS
permettant la tenu des statistiques.

SITADEL (Système d’Information et de Traitement
Automatisé des Données Élémentaires sur les Logements et les locaux) est une base de
données de statistiques publiques permettant :

- la mesure de l activité de la construction

- le calcul de la taxe locale d equipement

- l'alimentation du RIL (répertoire des immeubles localisés) de l'INSEE

<Experience> ::

    Il y a effectivement une difference entre l instruction openFoncier et la
    demande SITADEL qui couvre les champs des CERFA de reference.
    La difficulté reste que les champs demandés ne sont pas des champs
    obligatoires à remplir pour le pétitionnaire.

    C'est pour cela que la version 3.0.0 a privilégié les tableaux des shons
    Il est possible dans l onglet statistique de dossier de rajouter des champs
    sitadel à paramétrer dans la table "parametre".
    
    La collectivité peut paramétrer ses propres paramétres de statistiques.


</experience>


Le programme SITADEL sera bientôt opérationnel et reprend pour l'instant les
champs existants dans openFoncier.

La procédure SITADEL a pour objet de suivre le cycle de vie du permis en enregistrant pour chaque dossier:

    le dépôt du permis 

    la décision

    la déclaration d'ouverture de chantier

    la déclaration d'ouverture de travaux

    les modificatifs

    les transferts


L'envoi des données s'effectue tous les mois pour les événements du mois précédent.

OpenFoncier prend en compte les données nécessaires à la gestion des délais et des courriers de
l'instruction d'un permis. Toutes les données des documents cerfa demande de permis,
déclaration d'ouverture de chantier, déclaration d'ouverture de chantier, déclaration d'achèvement des
travaux ne sont pas saisies. De ce fait de nombreuses données seront absentes dans l'export SITADEL.

Les paragraphes suivants font le point sur les données demandées par SITADEL existantes dans openFoncier.


Code mouvement DEPOT
====================

Pour chaque dépôt dans le mois précédent, il faut faire un transfert de l'enregistrement suivant. 

Les difficultés sont liées à la non normalisation des adresses ::


    Nom de Zone     Descriptif          Zone openFoncier    Observation
    ----------------------------------------------------------------------------
    Mouv            DEPOT
    Typpermis       PC PA PD ou DP      Dossier.dossier     Ok
    Equivalence     PA qui vaut PC
                    PA qui vaut PD      Non renseigné       Vide
    Dep             '013                '013                Ok
    Commune         '004                '004                Ok
    Andep           Année               Dossier.annee       Ok
    Numpc           Numéro de PC        Dossier.dossier     Ok
    Indmod          Modificatif         Dossier.dossier     Ok
    
    Codemo          1=particulier
                    2= personne morale  Dossier.            Ok traitement
    Civpart         Madame monsieur
                    si particulier      Dossier.demandeur_civilite
                    Si codemo =1
    Prenompart      Prenom particulier  Non renseigne       Le prenom avec le nom
    Nompart         Nom particulier     demandeur_nom       Ok
                                                            nom/prenom sur 30 car
    Denopm          Denomination
                    personne morale     demandeur_societe   ok
                    Si codemo =2
    Rspm            Raisons sociale      categorie_libelle   Ok
    Siret                               Non renseigne       Vide
    Catjur          Categorie juridique Non renseigne       Vide
    Civrep          Madame monsieur
                    personne morale     demandeur_civilite
                    Si codemo=2
    prenomrep       Dans nom            Vide
    Nomrep                              demandeur_nom
    Numvoiemo       Dans adresse        Vide
    Typvoiemo       Dans adresse        Vide
    Libvoiemo       Demandeur adresse   26 premier caracteres
    Lieuditmo       Demandeur adresse   26 à 38
    Communemo       Demandeur ville     demandeur_ville     ok
    Codeposmo       Demandeur cp        demandeur_cp        ok
    Bpmo            Boite postal        vide
    Cedexmo         Cedex               vide    
    Paysmo          Pays                vide
    Divtermo        Division pays etr   vide
    Civtiers        Delegataire         delegataire_civilite    Si delegataire = Oui
    Prenomtiers                         vide                saisie avec nom
    Nomtier                             delegataire_nom
    Numvoietier     Adresse normalisée  vide                Sasie avec adresse
    Typvoietier                         vide                Saisie avec adresse
    Libvoietier                         Delegataire_adresse 0 à 26
    Lieudittier                         Delegataire_adressé 26 à 38
    Communetier                         Delegataire ville
    Codpostier                          delegataire_cp
    Bptier                              vide
    Cdextier                            vide
    Paystier                            vide
    divtertier                          vide
    Telmo                               demandeur_telephone
    Melmo                               demandeur_email
    Suivi   Est ce que le tiers suit le dossier electroniquement ? 1/0  vide
    Numvoiete   Numero voie du terrain  terrain_numero
    Typvoieie                           vide                Avec terrain adresse
    Libvoiete                           terrain_adresse caractères 0-26
    Lieuditte   Lieu dit du terrain     terrain_adresse caracteres 26-38
    Communete   Commune du terrain      ARLES par défaut ***
    Codposte    Cp du terrain           terrain_cp
    Bpte        Boite postale           ARLES par défaut ***
    Cedexte     Cedex terrain           vide
    Scadastre1  Section cadastrale      Dossier.parcelle    caractères 1,2
    Ncadastre1  Parcelle                Dossier.parcelle    caractères 3,4
    Scadastre2  Section cadastrale      vide
    Ncadastre2  Parcelle                Vide
    Scadastre3  Section cadastrale      Vide
    Ncadastre3  Parcelle                Vide
    Contrat     contrat de maison individuel  vide              0/1
    Architecte  0= non  1= oui          Dossier.architecte  >0  oui
    CNIL        0= accord   1= interdit 1                   par défaut

Code mouvement décision
=======================

Pour chaque décision positive, transmission groupe 1 et 2
Pour les décisions négatives, uniquement le groupe 1.
Les difficultés sont liés à la description des travaux qui ne sont qu'en partie rempli.
Les modes de financement sont inexistants car inutiles dans le suivi d'un permis ::

    Nom de Zone Descriptif              Zone openFoncier    Observation
    ----------------------------------------------------------------------------
    Mouv        DECISION
    Typpermis   PC PA PD ou DP          Dossier.dossier
    Equivalence PA qui vaut PC
                PA qui vaut PD          vide
    Dep                                 '013    
    Commune                             '004
    Andep       Année                   Dossier.annee
    Numpc       Numéro de PC            Dossier.dossier
    Indmod      Modificatif             Dossier.dossier
    Collectivite commune           1                   2:etat, 3:epci
    Natdec              
        0 en cours
        1 rejet tacite
        2 octroi tacite
        4 octroi
        5 accord avec presc
        6 refus
        7 sursis a statuer
        8 annulation                    Avis.sitadel    codification des avis à faire
    Dateredec   Date de la décision     Dossier.date_decision
    motifannul
        1 retrait par le petitionnaire
        2 annulation juridique          Avis.stadelavis codification des avis à faire
                                        Ok si natdec=8
    *** correspondance avis / code ***
    GROUPE 2 si décision FAVORABLE   - avis sitadel  = 2 ou 4 ou 5
    Superficie  Terrain                 terrain_surface arrondi entier inferieur
    Lotissement                         Amenagement     si lié a un PA : Oui
    ZAC         O/1                     0
    Afu         0/1                     0
    Libnattrav  Texte libre de 1000 c   travaux_libelle
    Natpro      Nature du projet
                1 nouvelle construction
                2 travaux sur construction existante
                3 nouvelle construction et travaux sur construction
                                        Suivant code lascot     
                                        vide si lascot different de 1,2,3
    Natdp
                1e car : nouvelle construction
                2e car : travaux sur constr. Exist
                3e car ravalement
                4e car modifiant structure porteuse
                5e car cloture
                                        Suivant code lascot
                                        1 = 10000
                                        2 = 01000
                                        3 = 01000
                                        X = 00001       uniquement DP
                                        vide sinon
    Nattrav     Nature des travaux existants
                1 car  extension
                2 car surelevation
                3 car niveau supplémentaire
                4 car amenagement intérieur
                                        Suivant code lascot
                                        2 = 1000
                                        3 = 0100
    Annexe
                1 car piscine
                2 car garage
                3 car veranda
                4 car abris jardin
                5 car autres
                                        Par defaut 00000
    Nivmax      Nombre de niveaux       Vide
    Shionnant1 à 9  Shon avant travaux par destination  Vide
    Shondem 1 a 9   Shon demolie par destination        Destination.shon                                 
    Shonanttr1 à 9  Shon transforme de la destination   vide        si PD
                    anterieure 
    Shonnantprojtr1 à 9 Shon issu de la transformation
                        de la destination projettée     Destination.shon si lascot =4
    Shoncr1 à 9     Shon créée par destination          Destination.shon si lascot =1
    Shon2cr1        Shon créée par transformation
                    par destination                     Destination.shon si lascot =2
    Cpublic     1 car transport                         000000
                2 car enseignement
                3 car santé 
                4 car social
                5 ouvrage
                6 culture
    Nblogdem    Nombre de logement                      logement_nombre
    Nbmaison    Nombre de maison                        Vide
    Nblogcoll   Nombre de logement collectifs           Vide
    Nbtotlog    Nombre de logement total                logement_nombre
    Natres      1 car personne agées                    000000             
                2 car etudiants
                3 car tourisme
                4 car social
                5 car social 2
                6 car handicapée
                7 autres
    Libres      libelles de autres sur 1000 c           Vide
    Util        1 car : occ personnelle                 00000
                2 car : res principale
                3 car : res secondaire
                4 car : vente 
                5 car : location
    Chambres    Capacité accueil locaux d hebergement   vide
    Finis       Nb logement locatif sociaux             vide
    Finaa       Nb logement financement aidés           Vide
    Finptz      Nb logement prêt taux 0                 Vide
    Finaf       Nb logement autrement                   Vide
    Nbpiecemi   Nombre de pièces                        piece_nombre
    Piec1       Nombre de logement 1 pièce              vide
    Piec2       Nombre de logement 2 pièce              vide
    Piec3       Nombre de logement 3 pièce              vide
    Piec4       Nombre de logement 4 pièce              vide
    Piec5       Nombre de logement 5 pièce              vide
    Piec6       Nombre de logement 6 pièce              vide


code mouvement Suivi
====================

A chaque DOC ou DAT du mois précédent.
Il y a peu de renseignements dans notre base sauf la date et la shon totale ::


    Nom de Zone     Descriptif      Zone openFoncier        Observation
    --------------------------------------------------------------------------------
    Mouv                            SUIVI
    Typpermis       PC PA PD ou DP  Dossier.dossier
    Equivalence     PA qui vaut PC  vide              
                    PA qui vaut PD
    Dep                             013
    Commune                         004
    Andep   Année                   Dossier.annee
    Numpc   Numéro de PC            Dossier.dossier
    Indmod  Modificatif             Dossier.dossier
    
    
    *** partie reservée a l' ouverture de chantier ***
    Datereoc Date ouverture chant.  date_chantier
    Nblogoc Nb de logt commencé     Vide
    Nbmaisoc Nb global de logt ind  vide
    Nbcolloc Nb de logts collectif  vide
    Shonoc  Shon commencé           Dossier.shon ?          enlever les décimales
    Finisoc Nb logt locatif com                     Vide
    Finaoc  Nb logt com hors prêt 0                 Vide
    Finptzoc Nb logt commencé à prêt 0              Vide
    Finfoc  Nb logt commencés financement différent vide
    Indoc   Indice de la tranche                    vide
    
    *** Partie réservée à la déclaration Achévement de travaux ***
    Datereat Date achevement        date_achevement
    Nblogat  Nb logt globalterminés vide
    Nbmaisat Nb logt individuels terminés   Vide
    Nbcollat Nb logt collectifs terminés    Vide
    Shonat   Shon                           Dossier.shon ?
    Finsat  Nb logt sociaux terminés        Vide
    Finaat  Nb logt terminés financés aidé hors taux 0 vide
    Finptzat Nb logt terminés financés aidé avec taux 0 vide
    Finafat Nb de logt financés autrement   Vide
    Indat   Indice de tranche
            1 avec tranche, 0 sinon         Vide
    Finchantier 1 dossier cloture
                0 sinon                     Dossier.etat
                                            1 si etat = cloturer
                                            0 sinon
    Origat  Info achevement travaux
            2 dgi
            1 déclaration                   1 par défaut ?




code mouvement Transfert 
========================

Le problème essentiel du transfert, c'est de ne pas avoir de date stockée,
donc de ne pas pouvoir être transmis au moment où il est effectué.
Sinon même remarque que DEPOT car les adresses ne sont pas normalisées ::


    Nom de Zone         Descriptif      Zone openFoncier        Observation
    --------------------------------------------------------------------------------
    Mouv                                TRANSFERT
    Typpermis   PC PA PD ou DP          Dossier.dossier
    Equivalence PA qui vaut PC          vide
                PA qui vaut PD
    Dep                                 013
    Commune                             004
    Andep        Année                  Dossier.annee
    Numpc       Numéro de PC            Dossier.dossier
    Indmod      Modificatif             Dossier.dossier
    Codemo      1=particulier
                2= personne morale      Dossier.                traitement
    Civpart     Madame monsieur         Dossier.demandeur_civilite
                                        Si codemo =1
    Prenompart  Prenom particulier      vide        Le prenom est sasie avec le nom
    Nompart     Nom particulier         demandeur_nom   nom et prenom sur 30 caractères
    Denopm      personne morale         demandeur_societe
                                        Si codemo =2
    Rspm        Raisons ociale          categorie_libelle
    Siret                               Vide
    Catjur      Categorie juridique     Vide
    Civrep      Madame monsieur         demandeur_civilite
                                        Si codemo=2
    prenomrep                           Vide
    Nomrep                              demandeur_nom
    Numvoiemo                           vide                    Dans adresse
    Typvoiemo                           vide                    Dans adresse
    Libvoiemo                           Demandeur adresse   26 premier caracteres
    Lieuditmo                           Demandeur adresse   26 à 38
    Communemo                           Demandeur ville
    Codeposmo                           Demandeur cp
    Bpmo        Boite postale           Vide
    Cedexmo     Cedex                   vide
    Paysmo      Pays                    vide
    Melmo                               demandeur_email
    Suivi   Est ce que le tiers suit
        le dossier electroniquement ? 1/0   Vide    Specifique sitadel

Suppression des lignes adresses tiers

code mouvement Modificatif
==========================

Descriptif du mouvement ::


    Nom de Zone     descriptif          Zone openFoncier        Observation
    -----------------------------------------------------------------------
    Mouv                                TRANSFERT
    Typpermis       PC PA PD ou DP      Dossier.dossier
    Equivalence     PA qui vaut PC      vide
                    PA qui vaut PD
    Dep                                 013
    Commune                             004
    Andep           Année               Dossier.annee
    Numpc           Numéro de PC        Dossier.dossier
    Indmod          Modificatif         Dossier.dossier
    Collectivite    1 commune           1               
                    2 etat
                    3 epci
        Natdec      0 en cours          avis.sitadel            
                    1 rejet tacite
                    2 octroi tacite
                    4 octroi
                    5 accord avec presc
                    6 refus
                    7 sursis a statuer
                    8 annulation
    Dateredec   Date de la décision     Dossier.date_decision
    motifannul  1 retrait petitionnaire Avis.stadelavis         si natdec=8
                2 annulation juridique         
    
    
    *** GROUPE 2 *** 
    Numvoiete  Numero dans la voie du terrain   terrain_numero
    Typvoieie                                   vide
    Libvoiete                                   terrain_adresse caractères 0-26
    Lieuditte   Lieu dit du terrain             terrain_adresse caracteres 26-38
    Communete   Commune du terrain              ARLES par défaut ***
    Codposte    Cp du terrain                   terrain_cp
    Bpte        Boite postale du terrain        ARLES par défaut ***
    Cedexte     Ceqex dex terrain               Vide
    Scadastre1  Section cadastrale              Dossier.parcelle    caractères 1,2
    Ncadastre1  Parcelle                        Dossier.parcelle    caractères 3,4
    Scadastre2  Section cadastrale              Vide
    Ncadastre2  Parcelle                        Vide
    Scadastre3  Section cadastrale              Vide
    Ncadastre3  Parcelle                        Vide
    Terrain     Superficie                      Dossier.surface
    Libmootif   Texte decrivant la modif        Vide
    Nattrav Nature des travaux existants        Suivant code lascot
                1 car  extension                2 = 1000
                2 car surelevation              3 = 0100
                3 car niveau supplémentaire
                4 car amenagement intérieur      
    Annexe      1 car piscine                   Par defaut 00000
                2 car garage
                3 car veranda
                4 car abris jardin
                5 car autres                                   
    Nvmax       Nombre de niveaux                   vide
    Shionnant1 à 9  avant travx                 Vide
    Shondem1 a 9    demolie                     Destination.shon   Si  PD
    Shonanttr1 à 9  Shon transforme             Vide
    Shonnantprojtr1 à 9 transformation          Destination.shon si lascot =4
    Shoncr1 à 9     créée par destination       Destination.shon si lascot =1
    Shon2cr1 à 9    créée par transformation    Destination.shon si lascot =2
    Cpublic     1 car transport                 000000
                2 car enseignement
                3 car santé 
                4 car social
                5 ouvrage
                6 culture                                        
    Nbmaison    Nombre de maison                Vide
    Nblogcoll   Nombre de logement collectifs   Vide
    Nbtotlog    Nombre de logement total        logement_nombre
    Natres      1 car personne agées            000000
                2 car etudiants
                3 car tourisme
                4 car social
                5 car social 2
                6 car handicapée
                7 autres
                                                
    Libres      Libelles de autres sur 1000 c   Vide
    Util        1 car : occ personnelle         00000
                2 car : res principale
                3 car : res secondaire
                4 car : vente 
                5 car : location                                                
    Chambre     Capacité accuei hebergement     Vide
    Finis       Nb logement locatif sociaux     Vide
    Finaa       Nb logement financement aidés   Vide
    Finptz      Nb logement prêt taux 0         Vide
    Finaf       Nb logement autrement           Vide
    Piec1       Nombre de logement 1 pièce      vide
    Piec2       Nombre de logement 2 pièce      vide
    Piec3       Nombre de logement 3 pièce      vide
    Piec4       Nombre de logement 4 pièce      vide
    Piec5       Nombre de logement 5 pièce      vide
    Piec6       Nombre de logement 6 pièce      vide




