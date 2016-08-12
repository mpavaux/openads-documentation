.. _gestion_des_logs:

###########################
Gestion des fichiers de log
###########################

Les fichiers de log permettent d'avoir un historique des événements du fonctionnement d'openADS. Plusieurs fichiers
de logs sont présents dans l'application, chacun ayant un usage différent.

var/log/services.log
####################

Ce fichier contient tous les accès aux web services openADS, qu'ils soient entrants ou sortants. Dans ce log vont apparaître toutes les requêtes entrantes sur les fichiers rest_entry.php, la méthode interrogée avec ses paramètres et le retour renvoyé par cette méthode. Vont aussi apparaître chaque requête sortante envoyée via les classes MessagesSender* et les valeurs retournées.

var/log/error.log
#################

Ce fichier ne contient que des erreurs importantes qui ne doivent pas se produire et être corrigées. Ces erreurs affichent la plupart du temps un message d'erreur en rouge 'contactez votre administrateur' à l'utilisateur.

Log des appels aux plugins
##########################

Les connecteurs externes à openADS (SIG, GED...) gèrent eux-même leur propre fichier de log.