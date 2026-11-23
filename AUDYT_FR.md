# Revue de la localisation française (fr)

## Modifications de cette étape

- Ajout d’un pack français dédié aux textes de génération et d’export (`EXPORT_COPY`), couvrant les six couches, les avertissements juridiques et médicaux, les champs du modèle et le prompt système. L’export choisit le pack selon la langue active et retombe sur le texte de secours pour les clés absentes.
- Ajout des consignes françaises pour les profils « personnalité politique » et « persona » dans les règles de rôle.

## Vérifications et limites

- `node --check` sur le dernier script intégré : réussi.
- `git diff --check` : réussi.
- Il s’agit d’une revue ciblée des lacunes repérées, pas d’une validation native ni d’une relecture exhaustive de chaque chaîne française et de chaque parcours d’interface. Les options de style et plusieurs tables de tâches/canaux conservent des couvertures linguistiques inégales ; elles doivent faire l’objet d’un contrôle dédié avant de déclarer l’ensemble de la localisation française entièrement couvert.
- Aucun test interactif complet du navigateur ou de chaque format d’export n’a été réalisé.
