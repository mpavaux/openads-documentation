#########
Ergonomie
#########

Tableau de bord
===============

Le tableau de bord est composé de plusieurs blocs d'informations appelés widget qui permettent à l'utilisateur de visualiser rapidement des informations transverses.

.. image:: tableau-de-bord-exemple.png

La disposition des widgets est propre à chaque profil et peut être modifiée très facilement par l'administrateur.


Widgets
-------

Widget "Dossiers limites"
#########################

.. image:: widget_dossiers_limites.png

Orienté Instruction.

L'objet de ce widget est de présenter un listing des dix dossiers d'instruction qui sont tacites dont la date limite est dans moins de X jours (le nombre de jours est paramétrable par l'administrateur). 

Trois filtres sont disponibles sur ce widget (le filtre est paramétrable par l'administrateur) :

- filtre par instructeur : on présente uniquement les dossiers dont il est spécifiquement instructeur.
- filtre par division : on présente tous les dossiers de la division de l'instructeur.
- aucun filtre : tous les dossiers auxquels l'utilisateurs a accès (si l'utilisateur appartient à une commune niveau mono, alors l'utilisateur n'a accès qu'aux dossiers de sa commune et si l'utilisateur appartient à une commune multi, alors l'utilisateur a accès à tous les dossiers).

Par défaut, tous les types de dossiers apparaissent dans ce listing (les types sont paramétrables par l'administrateur).

A tout moment, au survol de l'icône d'information du widget, une descrption permet d'indiquer quels sont les paramètres appliqués sur le widget.

Le listing présente les informations suivantes :

- le libellé du dossier d'instruction,
- le nom du pétitionnaire principal,
- la date limite,
- le caractère à enjeux du dossier.

Un lien sur chaque enregistrement permet d'accéder à la fiche de visualisation du dossier d'instruction.

Un lien "Voir +" permet d'accéder au listing des mêmes dossiers sans limite de nombre.


Widget "Recherche Dossier"
##########################

.. image:: widget_recherche_dossier.png

Orienté Instruction.

L'objet de ce widget est de présenter un champ de saisie de recherche de dossier d'instruction avec accès direct. C'est-à-dire que si le code du dossier est saisi dans son intégralité on accède directement à la fiche de visualisation du dossier d'instruction, par contre si le code du dossier n'est pas saisi dans son intégralité, alors si au moins un résultat correspond alors on accède à un listing de dossiers d'instructions avec l'élément saisi comme recherche pré-rempli (une recherche avancée permet alors de compléter la recherche).

