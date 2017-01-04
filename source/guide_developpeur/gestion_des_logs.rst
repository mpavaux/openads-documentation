.. _gestion_des_logs:

#############################
Gestion des fichiers journaux
#############################

Les fichiers journaux permettent d'avoir un historique des événements du fonctionnement d'openADS. Plusieurs fichiers
de logs sont présents dans l'application, chacun ayant un usage différent. 

Fichier journal des erreurs de l'application
############################################

Le fichier **var/log/error.log** contient les erreurs importantes liées à l'utilisation d'openADS, telles que les erreurs de base de données, les erreurs lors de l'enregistrement d'un fichier sur le disque, les erreurs lors d'une synchronisation des contraintes avec un SIG, etc.

Fichier journal des web services
################################

Le fichier **var/log/services.log** contient une trace de toutes les requêtes entrantes et sortantes des web services openADS. Pour chaque requête est détaillé le nom de la fonction utilisée, les paramètres en entrée et le retour de la requête.

Fichier journal des plugins
###########################

Les connecteurs externes à openADS gèrent eux-même leur propre fichier de log.

Modification des fichiers journaux
##################################

Les logs sont en premier lieu destinés aux administrateurs techniques. Bien souvent ces derniers disposent de scripts analysant automatiquement les informations qui y sont présentes.
C'est pourquoi leur formatage a un sens : une seule ligne par action, présence de caractères séparateurs entre les données, ... La modification de ces logs nécessite l'accord de la 
communauté puis, le cas échéant, doit être documentée.
