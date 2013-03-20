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

Pour depot dans le mois, il est envoyé un mouvement depot et un mouvement decision avec decision = 0 si
il n y en a pas.

Pour une décision dans le mois, il est envboyé un mouvement dépôt et un mouvement décision (groupe 1, si décision négative,
groupe 1 et 2 si décision positive).

Pour une ouverture de chantier ou déclaration d achevement de travaux dans le mois, il est envoyé une mouvement suivi.

Pour un modificatif, il est envoyé un mouvement dépôt et un mouvement modificatif.

Pouur un transfert, il est envoyé un mouvement transfert.


OpenFoncier prend en compte les données nécessaires à la gestion des délais et des courriers de
l'instruction d'un permis. Toutes les données des documents cerfa demande de permis,
déclaration d'ouverture de chantier, déclaration d'ouverture de chantier, déclaration d'achèvement des
travaux ne sont pas saisies. De ce fait de nombreuses données seront absentes dans l'export SITADEL.

Les paragraphes suivants font le point sur les données demandées par SITADEL existantes dans openFoncier.
Les données qui ne sont pas existantes sont à saisir dans l'onglet statistiques.


Code mouvement DEPOT
====================

Pour chaque dépôt dans le mois précédent, il faut faire un transfert de l'enregistrement suivant. 

Les difficultés sont liées à la non normalisation des adresses et au fait que le nom est saisi avec le prénom dans openFoncier::


    Nom de Zone     Descriptif          Zone openFoncier    valeur par defaut
    ----------------------------------------------------------------------------
    Mouv            DEPOT
    Typpermis       PC PA PD ou DP      Dossier.dossier     
    Equivalence                         Non renseigné       Vide
    Dep             '013                om_parametre        
    Commune         '004                om_parametre        
    Andep           Année               Dossier.annee       
    Numpc           Numéro de PC        Dossier.dossier     
    Indmod          Modificatif         Dossier.dossier     
    Codemo                              Dossier.categorie            
    Civpart         Madame monsieur     dossier.demandeur.civilite
    Prenompart      Prenom particulier  statistique         Le prenom avec le nom
    Nompart         Nom particulier     demandeur_nom       
    Denopm          personne morale     demandeur_societe   
    Rspm            Raisons sociale     statistique   
    Siret                               statistique
    Catjur          Categorie juridique statistique
    Civrep          Madame monsieur     demandeur_civilite
    prenomrep       Dans nom            statistique
    Nomrep                              demandeur_nom      
    Numvoiemo       Dans adresse        statistique         
    Typvoiemo       Dans adresse        statistique
    Libvoiemo                           Demandeur adresse   26 premier caracteres
    Lieuditmo                           Demandeur adresse   26 à 38
    Communemo       ville               demandeur_ville     
    Codeposmo       cp                  demandeur_cp        
    Bpmo            Boite postal        statistique
    Cedexmo         Cedex               statistique
    Paysmo          Pays                statistique
    Divtermo        Division pays etr   statistique
    Civtiers        Delegataire         delegataire_civilite    
    Prenomtiers                         statistique         saisie avec nom
    Nomtier                             delegataire_nom
    Numvoietier     Adresse normalisée  statistique         Saisie avec adresse
    Typvoietier                         statistique         Saisie avec adresse
    Libvoietier                         Delegataire_adresse 0 à 26
    Lieudittier                         Delegataire_adressé 26 à 38
    Communetier                         Delegataire ville
    Codpostier                          delegataire_cp
    Bptier                              statistique
    Cdextier                            statistique
    Paystier                            statistique
    divtertier                          statistique
    Telmo                               demandeur_telephone
    Melmo                               demandeur_email
    Suivi       electronique            delegataire                 
    Numvoiete   Numero voie du terrain  terrain_numero
    Typvoieie                           statistique         sisie avec adresse
    Libvoiete                           terrain_adresse caractères 0-26
    Lieuditte   Lieu dit du terrain     terrain_adresse caracteres 26-38
    Communete   Commune du terrain      terrain_ville
    Codposte    Cp du terrain           terrain_cp
    Bpte        Boite postale           statistique
    Cedexte     Cedex terrain           statistique
    Scadastre1  Section cadastrale      Dossier.parcelle    caractères 1,2
    Ncadastre1  Parcelle                Dossier.parcelle    caractères 3,4
    Scadastre2  Section cadastrale      statistique
    Ncadastre2  Parcelle                statistique
    Scadastre3  Section cadastrale      statistique
    Ncadastre3  Parcelle                statistique
    Contrat     contrat de maison indl  statistique
    Architecte  0= non  1= oui          Dossier.architecte  
    CNIL        0/1                     statistique         1 (interdit)

Code mouvement décision
=======================

Pour chaque décision positive, transmission groupe 1 et 2
Pour les décisions négatives, uniquement le groupe 1.
Les difficultés sont liés à la description des travaux qui ne sont qu'en partie rempli.
Les modes de financement sont inexistants car inutiles dans le suivi d'un permis ::

    Nom de Zone Descriptif              Zone openFoncier    valeur par defaut
    ----------------------------------------------------------------------------
    Mouv        DECISION
    Typpermis   PC PA PD ou DP          Dossier.dossier
    Equivalence                         vide
    Dep                                 om_parametre
    Commune                             om_parametre
    Andep       Année                   Dossier.annee
    Numpc       Numéro de PC            Dossier.dossier
    Indmod      Modificatif             Dossier.dossier
    Collectivite                        commune=1
    Natdec                              Avis.sitadel   
    Dateredec   Date                    Dossier.date_decision
    motifannul                          Avis.stadelavis 
    GROUPE 2 si décision FAVORABLE      avis sitadel  = 2 ou 4 ou 5
    Superficie  Terrain                 terrain_surface 
    Lotissement                         dossier.Amenagement     
    ZAC         O/1                     statistique         0
    Afu         0/1                     statistique         0    
    Libnattrav  Texte libre de 1000 c   travaux.libelle
    Natpro      Nature du projet        vide si lascot different de 1,2,3
    Natdp       Suivant code lascot DP  1 = 10000 /2 = 01000 /3 = 01000 / X = 00001      
    Nattrav     Nature des travaux      travaux.lascot 2 = 1000 / 3 = 0100
    Annexe                              statistique         00000
    Nivmax                              statistique
    Shionnant1 à 9                      destination_shon  
    Shondem 1 a 9                       destination_shon                                        
    Shonanttr1 à 9                      destination_shon   
    Shonnantprojtr1 à 9                 destination_shon     
    Shoncr1 à 9                         destination_shon   
    Shon2cr1                            destination_shon                        
    Cpublic                             statistique         000000
    Nblogdem                            dossier.logement_nombre
    Nbmaison                            statistique
    Nblogcoll                           statistique
    Nbtotlog                            logement_nombre     calcul ?
    Natres                              satistique          00000     
    Libres      libelles                statistique         
    Util                                statistique         00000    
    Chambres    Capacité accueil        statistique
    Finis       Nb log loc sociaux      statistique
    Finaa       Nb log financt aidés    statistique
    Finptz      Nb log prêt taux 0      statistique
    Finaf       Nb log autrement        statistique
    Nbpiecemi   Nombre de pièces        dossier.piece_nombre
    Piec1       Nombre de log 1 p       statistique       
    Piec2       Nombre de log 2 p       statistique
    Piec3       Nombre de log 3 p       statistique
    Piec4       Nombre de log 4 p       statistique
    Piec5       Nombre de log 5 p       statistique
    Piec6       Nombre de log 6 p       statistique


code mouvement Suivi
====================

A chaque DOC ou DAT du mois précédent ::


    Nom de Zone     Descriptif      Zone openFoncier        Observation
    --------------------------------------------------------------------------------
    Mouv                            SUIVI
    Typpermis                       Dossier.dossier
    Equivalence                     vide    
    Dep                             om_parametre
    Commune                         om_parametre
    Andep           année           Dossier.annee
    Numpc           Numéro de PC    Dossier.dossier
    Indmod          Modificatif     Dossier.dossier
    
    *** partie reservée a l' ouverture de chantier ***
    Datereoc   Date ouv chant.      date_chantier
    Nblogoc    Nb de logt commencé  statistique   
    Nbmaisoc   Nb gl de logt ind    statistique
    Nbcolloc   Nb logts collectif   statistique
    Shonoc  Shon commencé           Dossier.shon 
    Finisoc Nb logt locatif com     statistique
    Finaoc  Nb logt hors prêt 0     statistique
    Finptzoc Nb logt à prêt 0       statistique
    Finfoc  Nb logt dif             statistique
    Indoc   Indice de la tranche    statistique
    
    *** Partie réservée à la déclaration Achévement de travaux ***
    Datereat Date achevement        date_achevement
    Nblogat  Nb logt gl lterminés   statistique
    Nbmaisat Nb logt ind terminés   statistique
    Nbcollat Nb logt col terminés   statistique
    Shonat   Shon                   Dossier.shon
    Finsat  Nb logt sociaux term    statistique
    Finaat  Nb logt term  hors tx 0 statistique
    Finptzat Nb logt term fin tx 0  statistique
    Finafat Nb de logt finautr      statistique
    Indat   Indice de tranche       statistique
    Finchantier 1/0                 dossier.etat
    Origat  Info achevt travaux     statistique




code mouvement Transfert 
========================

Le problème essentiel du transfert, 
Sinon même remarque que DEPOT car les adresses ne sont pas normalisées ::


    Nom de Zone         Descriptif      Zone openFoncier        Observation
    --------------------------------------------------------------------------------
    Mouv                                TRANSFERT
    Typpermis   PC PA PD ou DP          Dossier.dossier
    Equivalence 
    Dep                                 om_parametre
    Commune                             om_parametre
    Andep       Année                    Dossier.annee
    Numpc       Numéro de PC            Dossier.dossier
    Indmod      Modificatif             Dossier.dossier
    Codemo      1=part 2= pers morale   dossier.demandeur_categorie
    Civpart     Madame monsieur         Dossier.demandeur_civilite
    Prenompart  Prenom particulier      statistique        Le prenom est saisie avec le nom
    Nompart     Nom particulier         demandeur_nom      nom et prenom sur 30 caractères
    Denopm      personne morale         demandeur_societe
    Rspm        Raisons ociale          categorie_libelle
    Siret                               statistique
    Catjur      Categorie juridique     statistique
    Civrep      Madame monsieur         demandeur_civilite
    prenomrep                           statistique         le prenom est saisi avec le nom
    Nomrep                              demandeur_nom
    Numvoiemo                           statistique         Dans adresse
    Typvoiemo                           statistique         Dans adresse
    Libvoiemo                           Demandeur adresse   26 premier caracteres
    Lieuditmo                           Demandeur adresse   26 à 38
    Communemo                           Demandeur ville
    Codeposmo                           Demandeur cp
    Bpmo        Boite postale           statistique
    Cedexmo     Cedex                   statistique
    Paysmo      Pays                    statistique
    Melmo                               demandeur_email
    Suivi   dossier electroniquement    delegataire


code mouvement Modificatif
==========================

Descriptif du mouvement ::


    Nom de Zone     descriptif          Zone openFoncier        Par defaut
    -----------------------------------------------------------------------
    Mouv                                TRANSFERT
    Typpermis       PC PA PD ou DP      Dossier.dossier
    Equivalence                         vide
    Dep                                 om_parametre
    Commune                             om_parametre
    Andep           Année               Dossier.annee
    Numpc           Numéro de PC        Dossier.dossier
    Indmod          Modificatif         Dossier.dossier
    Collectivite    1 commune           commune                 1                    
    Natdec          0 en cours          avis.sitadel            
    Dateredec       Date  décision      Dossier.date_decision
    motifannul                          Avis.stadelavis         
    
    *** GROUPE 2 *** 
    Numvoiete  Numero                   terrain_numero
    Typvoieie                           statistique
    Libvoiete                           terrain_adresse caractères 0-26
    Lieuditte   Lieu dit du terrain     terrain_adresse caracteres 26-38
    Communete   Commune du terrain      terrain_ville
    Codposte    Cp du terrain           terrain_cp
    Bpte        Boite post du terrain   statistique
    Cedexte     Ceqex dex terrain       statistique
    Scadastre1  Section cadastrale      Dossier.parcelle    caractères 1,2
    Ncadastre1  Parcelle                Dossier.parcelle    caractères 3,4
    Scadastre2  Section cadastrale      statistique
    Ncadastre2  Parcelle                statistique
    Scadastre3  Section cadastrale      statistique
    Ncadastre3  Parcelle                statistique
    Terrain     Superficie              Dossier.surface
    Libmootif   Texte decrivant modif   dossier.travaux_libelle
    Nattrav     Nat des travaux exist   code lascot  
    Annexe                              statistique         00000       
    Nvmax       Nombre de niveaux       statistique
    Shionnant1 à 9                      destination_shon  
    Shondem 1 a 9                       destination_shon                                        
    Shonanttr1 à 9                      destination_shon   
    Shonnantprojtr1 à 9                 destination_shon     
    Shoncr1 à 9                         destination_shon   
    Shon2cr1                            destination_shon
    Cpublic                             statistique         000000
    Nbmaison    Nombre de maison        statistique
    Nblogcoll   Nombre de logement col  statistique 
    Nbtotlog    Nombre  total           logement_nombre
    Natres                              statistique         000000
    Libres      Libelles de autres      statistique
    Util                                statistique         00000                                               
    Chambres    Capacité accueil        statistique
    Finis       Nb log loc sociaux      statistique
    Finaa       Nb log financt aidés    statistique
    Finptz      Nb log prêt taux 0      statistique
    Finaf       Nb log autrement        statistique
    Piec1       Nombre de log 1 p       statistique       
    Piec2       Nombre de log 2 p       statistique
    Piec3       Nombre de log 3 p       statistique
    Piec4       Nombre de log 4 p       statistique
    Piec5       Nombre de log 5 p       statistique
    Piec6       Nombre de log 6 p       statistique




