# Contribuer à ce projet

Ce document décrit le workflow de contribution retenu pour l'équipe (2 membres).

## Workflow de branches : GitHub Flow

Nous utilisons **GitHub Flow** : une branche par fonctionnalité ou correctif,
toujours créée depuis `main`, intégrée via une Pull Request.

### Pourquoi GitHub Flow plutôt que Git Flow ou trunk-based ?

- **Vs Git Flow** : Git Flow ajoute des branches `develop`, `release/*` et
  `hotfix/*` pensées pour des cycles de release planifiés et plusieurs versions
  maintenues en parallèle. Pour une équipe de 2 personnes sans gestion de
  versions multiples, c'est une complexité inutile qui ralentit l'intégration
  du travail.
- **Vs trunk-based development** : le trunk-based pousse à committer
  directement sur `main` (ou des branches très courtes) avec des feature flags
  et une CI/CD très mature. C'est efficace pour de grandes équipes avec une
  forte automatisation, mais trop exigeant à mettre en place ici et offre
  moins de garde-fous avant merge (pas de revue systématique obligatoire).
- **GitHub Flow** est le bon compromis : simple, une seule branche longue vivante
  (`main` toujours déployable), une revue obligatoire avant merge, adapté à une
  petite équipe avec un flux continu de petites fonctionnalités/correctifs.

## Convention de nommage des branches

Format : `type/numero-issue-description-courte`

Types autorisés :

- `feature/...` — nouvelle fonctionnalité
- `fix/...` — correction de bug
- `docs/...` — documentation uniquement

Exemples :

- `feature/12-ajout-page-profil`
- `fix/27-crash-login`
- `docs/31-maj-readme-install`

## Règles de commit : Conventional Commits

Chaque commit suit le format :

```
type(scope-optionnel): description courte au présent
```

Types principaux :

- `feat` — ajout d'une fonctionnalité
- `fix` — correction de bug
- `docs` — documentation
- `chore` — maintenance, config, dépendances
- `refactor` — refactorisation sans changement de comportement
- `test` — ajout ou modification de tests
- `ci` — changements liés à l'intégration continue

Exemples :

```
feat(auth): ajouter la connexion par email
fix(api): corriger le timeout sur /users
docs: mettre à jour le README d'installation
```

## Processus de Pull Request

1. **Issue** : toute tâche part d'une issue GitHub décrivant le besoin.
2. **Branche** : création d'une branche depuis `main`, nommée selon la
   convention ci-dessus, en référence à l'issue.
3. **Pull Request** : une fois le travail prêt, ouverture d'une PR vers
   `main`, avec description claire et référence à l'issue (`Closes #numero`).
4. **Revue** : au moins **1 approbation de l'autre membre de l'équipe** est
   obligatoire avant merge. Pas d'auto-approbation.
5. **Merge** : une fois approuvée (et la CI verte), la PR est mergée dans
   `main`.
6. **Suppression de la branche** : la branche est supprimée après le merge
   pour garder le dépôt propre.
