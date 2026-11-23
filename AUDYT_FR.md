# Revue de localisation française (fr)

## Portée de la passe

Revue statique des ressources françaises de l’application et des textes exportés. Les changements cumulés couvrent :

- le pack `EXPORT_COPY.fr` pour les six couches, les champs, les avertissements médicaux/juridiques et le prompt système ;
- les consignes françaises de rôle et les fiches `ROLE_PLAYBOOK` ;
- les tâches professionnelles (`ROLE_TASKS.fr`) avec vérification de parité des identifiants par rapport aux tâches anglaises ;
- les règles de format/canal, les presets de modèle et de ton, les stratégies et les consignes anti-clichés d’IA ;
- les neuf groupes d’options rédactionnelles (`s1` à `s9`), les libellés de parcours, les libellés de sections et les métadonnées de sections ;
- les textes français des règles de départ des presets et quelques libellés d’interface auparavant fournis en anglais.

## Contrôles réalisés

- `node --check` sur le dernier script intégré : réussi.
- `git diff --check` : réussi.
- Analyse AST : aucun objet de dictionnaire contenant une version `en` sans entrée `fr`.
- Parité des identifiants de tâches : les tâches françaises présentes correspondent aux identifiants anglais pour les rôles contrôlés.

## Limites

Relecture statique uniquement : pas de validation par un locuteur natif ni de test interactif complet dans un navigateur. Le contrôle AST vérifie les entrées structurelles, pas la qualité éditoriale de chaque phrase ni tous les cas d’exécution. L’export suit le pack de langue sélectionné et dispose de textes français dédiés ; chaque combinaison d’options n’a pas été testée manuellement.
