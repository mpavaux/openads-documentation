.. _regles:

#####################
Les règles et travaux
#####################


openFoncier propose une liste de travaux qui correspond à la réglementation.
A cette liste sont associées des règles qui permettent de donner des
messages d'avertissement à l'utilisateur si la règle n'est pas respectée


Les travaux
===========

Les travaux sont associés à une nature (PC, DT ...) ou à toutes les natures (T = Tous)

Ces travaux sont associé à un code lascot (voir traitement / lascot)
Le code lascot est utilisé dans l'application lascot du service cadastre des impôts pour
identifier les constructions imposables

Il est important d'utiliser ce paramètre pour identifier les constructions
par rapport à l'impôt.

La case solde permet de supprimer à l'affichage les travaux non utilisés

<Experience> ::

    Lors de la mise en oeuvre, il vaut mieux eviter de multiplier les travaux et
    ainsi compliquer la codification LASCOT
    exemple  : extension shon + terrasse
    Il vaut mieux s'orienter vers une zone texte ou sont decrits succintement les travaux

</experience>


Les règles :
============

Les règles permettent de vérifier la saisie des dossiers par rapport à la
saisie d'un champ :

Exemple : la shob doit être supérieure ou égale à 20 M2


Pour cela il faut définir :

- le sens de la règle : plus ou moins (ET ou OU)

- l'ordre d'execution de la règle (si il en a plusieurs), important dans le cas ou il y a OU et ET

- la table concernée : pour l instant il n'y a que "travaux"

- l'id du travaux concerné

- le champ de la table "dossier" concerné

- l'opérateur de comparaison  : <, >, =, <=, =>

- la valeur de comparaison

- le message qui apparaitra à la saisie

Les règles ne sont pas bloquantes et affichent uniquement le message.



<developpement> ::

    les règles sont appliquées dans la méthode vérifier de dossier.class.php
    Il est possible de bloquer la saisie en initialisant $this->correct à false
    si la règle n'est pas respectée.

</developpement>
