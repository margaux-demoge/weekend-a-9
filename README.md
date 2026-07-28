# On part où en septembre ?

Site de coordination pour le week-end à 9 : trois destinations, votes en direct, sondage de dates, idées d'activités.

- **Front** : page statique servie par GitHub Pages (`index.html`, zéro build).
- **Données partagées** : un blob JSON (jsonblob.com), lu/écrit directement depuis le navigateur, avec ETag/If-Match pour que deux sauvegardes simultanées ne s'écrasent pas. Chaque personne n'écrit que sa propre "urne" (clé membre), re-poussée automatiquement si elle disparaît.
- **Rotation + sauvegarde** : jsonblob expire un blob 24 h après sa création, donc une GitHub Action recrée un blob neuf toutes les 6 h, met à jour le pointeur `bin.json` (relu par les clients à chaque sync) et versionne un snapshot dans `backups/latest.json`. Si le blob meurt quand même, relancer le workflow à la main le restaure depuis le dernier snapshot.

Les votes sont accessibles à quiconque connaît l'URL du blob : ne rien y mettre de sensible (prénoms et votes uniquement).
