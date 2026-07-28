# On part où en septembre ?

Site de coordination pour le week-end à 9 : trois destinations, votes en direct, sondage de dates, idées d'activités.

- **Front** : page statique servie par GitHub Pages (`index.html`, zéro build).
- **Données partagées** : un bin JSON (extendsclass.com), lu/écrit directement depuis le navigateur. Chaque personne n'écrit que sa propre "urne" (clé membre), fusionnée côté client avant chaque sauvegarde, avec re-push automatique si un vote se fait écraser.
- **Sauvegarde** : une GitHub Action snapshotte le bin toutes les 6 h dans `backups/latest.json` (sert aussi de garde-fou si le bin expire : il suffit de recréer un bin et d'y remettre le JSON).

Les votes sont accessibles à quiconque connaît l'URL du bin : ne rien y mettre de sensible (prénoms et votes uniquement).
