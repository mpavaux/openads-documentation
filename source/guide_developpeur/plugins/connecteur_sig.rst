.. _connecteur_sig:

###################
les connecteurs SIG
###################

Les connecteurs SIG permettent de faire le lien entre openads et différents SIG.

Description de la configuration des connecteurs
###############################################

La configuration du plugin est définie dans dyn/sig.inc.php.

Exemple :

.. code:: php
    
    $conf["sig-default"] = array (
        "2" => array(
            'connector' => 'generic',
            'path' => '../obj/',
        ),
    );

.. important:: Le paramètre "option_sig" doit être positionnée à la valeur "sig_externe"

.. important:: La clé sig-default doit être ajoutée au script database sig.inc.php.
               La clé du tabeau de configuration du SIG correspond à l'identifiant
               de la collectivité pour laquelle le connecteur est disponible
               (si collectivité multi, les collectivités mono auront accès
               au connecteur SIG)

.. important:: Les paramètres "connector" et "path" sont obligatoires quelque
                soit le connecteur. D'autres paramètres spécifiques aux connecteurs
                pourront y être ajoutés.

Dans cet exemple, le connecteur geoads_generic.class.php contenu dans le dossier
"obj" sera instancié.


Description du script
#####################

Le script obj/geoads.class.php permet d'instancier les connecteurs spécifiques.

Liste des classes implémentées dans le script :

* geoads
* geoads_base
* geoads_bdd_exception
* geoads_configuration_exception
* geoads_connector_4XX_exception
* geoads_connector_5XX_exception
* geoads_connector_exception
* geoads_connector_method_not_implemented_exception
* geoads_exception
* geoads_parameter_exception


******
geoads
******

La classe 'geoads' est une classe d'abstraction, spécifique à openADS,
permettant de gérer les requêtes vers divers webservices SIG et ainsi
proposer aux utilisateurs des informations géographiques.
Cette classe est instanciée et utilisée par d'autres scripts pour
gérer notamment la vérification de parcelles et ce peu importe le SIG utilisé.
Son objectif est d'instancier les classes spécifiques aux SIG aussi appelées
connecteurs correspondant au paramétrage de la collectivité.

Ces connecteurs héritent de la classe 'geoads_base' qui leur sert de modèle.

Enfin la classe 'geoads_exception' permet de gérer les erreurs.
Plusieurs classes en héritent afin de spécifier le type d'exception.

***********
geoads_base
***********

Classe parente de tous les connecteurs SIG

    .. important:: Les classes des connecteurs SIG doivent étendre de geoads_base.

****************
geoads_exception
****************

Classe gérant les erreurs (une exception est levée pour chacune).


********************
geoads_bdd_exception
********************

Classe d'exceptions utilisée lors d'une erreur de base de données.

******************************
geoads_configuration_exception
******************************

Classe d'exceptions utilisée lors d'une erreur dans le paramétrage du connecteur.


**************************
geoads_parameter_exception
**************************

Classe d'exceptions utilisée lors de la vérification des paramètres
passés au méthode de l'abstracteur.


******************************
geoads_connector_4XX_exception
******************************

Classe de gestion des exceptions retournée lors d'un code http 4XX.

    .. important:: Cette exception correspond à un problème inhérent à openADS.


******************************
geoads_connector_5XX_exception
******************************

Classe de gestion des exceptions retournée lors d'un code http 5XX.

    .. important:: Cette exception correspond à un problème inhérent au SIG.


**************************
geoads_connector_exception
**************************

Classe de gestion des exceptions génériques remontées par le connecteur.


*************************************************
geoads_connector_method_not_implemented_exception
*************************************************

Classe de gestion des exceptions sur les methodes du connecteur qui ne sont pas
implémentées.


Méthodes à implémenter
######################


* `$messageSender`_
* `$sig_parameters`_
* `$collectivite_parameters`_
* `__construct()`_
* `init_message_sender()`_
* `verif_parcelle()`_
* `calcul_emprise()`_
* `calcul_centroide()`_
* `recup_contrainte_dossier()`_
* `recup_toutes_contraintes()`_
* `redirection_web_emprise()`_
* `redirection_web()`_

*********
Attributs
*********

$messageSender
**************

::

    $messageSender : null


*Handler d'envoi de messages REST ou SOAP.*


$sig_parameters
***************

::

    $sig_parameters : array


*Paramètres de connexion au sig*


$collectivite_parameters
************************


::

    $collectivite_parameters : array


*Paramètres de la collectivite*


********
Méthodes
********


__construct()
*************


::

    __construct(array  $collectivite) 


*Le constructeur instancie le connecteur SIG selon la configuration*


Parameters
``````````
array $collectivite
Configuration du connecteur.


init_message_sender()
*********************


::

    init_message_sender()

*Permet d'initialiser la classe d'envoi de message*


verif_parcelle()
****************


::

    verif_parcelle(  $parcelles) 


*GET- Vérification d'existence de parcelles et récupération de leurs
adresses.*

openADS fournit une liste de parcelles. Le SIG renvoie une collection,
en mentionnant pour chaque parcelle si elle existe, et le cas échéant
l'adresse qui y est rattachée.


Parameters
``````````
(array) $parcelles : Tableau de parcelles à interroger.

Exemple de structure du tableau d'entrée pour une seule parcelle :

.. code:: php

    array(
        array(
            'prefixe' => string,
            'quartier' => string,
            'section' => string,
            'parcelle' => string
        ),
    )



Returns
```````
(array) Tableau de résultats (un sous-tableau par parcelle)

.. code:: php

    array(
        array(
            "parcelle"=> "1312158980H0126",
            "existe"=> true,
            "adresse"=> array(
                "numero_voie"=> "666",
                "type_voie"=> "RUE",
                "nom_voie"=> "DE LA LIBERTE",
                "arrondissement"=> "11"
            ),
        ),
    )

Si la parcelle n'existe pas :

.. code:: php

    array(
        array(
            "parcelle"=> "1312158980H0126",
            "existe"=> false,
        ),
    )



calcul_emprise()
****************


::

    calcul_emprise(  $parcelles,   $dossier) 


*POST -Déclenche sur le SIG le calcul de l'emprise des parcelles d'un dossier.*

openADS fournit une liste de parcelles et le numéro de dossier
correspondant. Le SIG renvoie un statut, spécifiant si le calcul été
effectué correctement ou non.



Parameters
``````````

(array) $parcelles : Tableau de parcelles.
Exemple de structure du tableau d'entrée pour une seule parcelle :

.. code:: php

    array(
        array(
            'prefixe' => string,
            'quartier' => string,
            'section' => string,
            'parcelle' => string
        ),
    )

(string) $dossier : Numéro du dossier.
Ex. : PC1305515J0045P0.



Returns
```````
(boolean) true si le calcul est OK, false sinon.


calcul_centroide()
******************


::

    calcul_centroide(  $dossier) 


*POST - Déclenche sur le SIG le calcul du centroïde d'un dossier.*

openADS appelle la méthode centroide sur la ressource du dossier
souhaité. Si le calcul du centroïde est conduit avec succès, le SIG
renvoie un statut positif, accompagné des coordonnées du centroïde.
Dans le cas contraire, le SIG renvoie un statut négatif.


Parameters
``````````
(string) $dossier : Numéro du dossier. Ex. : PC1305515J0045P0.


Returns
```````
(array) Coordonnées du centroïde :

.. code:: php

    array(
        "statut_calcul_centroide" => true,
        "x" => "1888778.84",
        "y" => "3131268.88"
    )

Ou false si le calcul a échoué.


recup_contrainte_dossier()
**************************


::

    recup_contrainte_dossier(  $dossier) 


*GET - Récupération des contraintes applicables sur un dossier.*

openADS appelle la méthode contrainte sur la ressource du dossier
souhaité. Le SIG renvoie une collection de contraintes qui s'y
appliquent.


Parameters
``````````
(string) $dossier : Numéro du dossier. Ex. : PC1305515J0045P0.


Returns
```````
(array) Tableau de contraintes :

.. code:: php

    array(
        array(
            "contrainte" => "26",
            "groupe_contrainte" => "ZONES DU PLU",
            "sous_groupe_contrainte" => "protection",
            "libelle" => "Une seconde contrainte du PLU",
        ),
    )


recup_toutes_contraintes()
**************************


::

    recup_toutes_contraintes(  $code_insee) 


*GET - Récupération de toutes les contraintes existantes pour une
commune.*

OpenADS appelle le SIG en précisant seulement le code INSEE de la
commune. Il renvoie une collection de l'intégralité des contraintes
existantes.



Returns
```````
(array) Tableau de toutes les contraintes existantes.

.. code:: php

    array(
        array(
            "groupe_contrainte" => "ZONES DU PLU",
            "contrainte" => "26",
            "libelle" => "Une seconde contrainte du PLU",
            "sous_groupe_contrainte" => "protection",
        )
    )



redirection_web_emprise()
*************************


::

    redirection_web_emprise(  $parcelles,   $dossier) 


*Redirection vers le SIG dans le contexte de dessin d'emprise pour un
dossier.*



Parameters
``````````
(array) $parcelles : Tableau de parcelles.

(string) $dossier : L'identifiant du dossier.



Returns
```````
(string) L'url du SIG


redirection_web()
*****************


::

    redirection_web(  $parcelles = null,   $dossier = null) 

*Redirection vers le SIG dans le contexte de visualisation du
dossier.*

Si les deux arguments sont nuls, c'est l'url par défaut du sig qui
doit être retourné.



Parameters
``````````
(array) $parcelles : Tableau de parcelles.

(string) $dossier : L'identifiant du dossier.



Returns
```````
(string) L'url du SIG

