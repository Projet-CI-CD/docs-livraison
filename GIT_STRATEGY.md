# 📘 GIT_STRATEGY.md

## 🎯 Objectif
Ce document définit la stratégie Git adoptée dans ce projet afin de garantir une collaboration efficace, lisible et structurée autour de GitFlow et des **Conventional Commits**.

---

## 🧑‍🤝‍🧑 Rôles des contributeurs

| Rôle          | Description                                              |
|---------------|----------------------------------------------------------|
| Développeur   | Crée des branches de features, soumet des PR             |
| Relecteur     | Relit et valide les PR, propose des améliorations        |
| Mainteneur    | Merge les PR validées, gère les releases et hotfix       |

---
## 🌱 Branches

| Branche        | Description                                      |
|----------------|--------------------------------------------------|
| `main`         | Branche de production. Protégée. Release uniquement. |
| `dev`          | Intégration continue. Merge des features.        |
| `feature/*`    | Nouvelles fonctionnalités                        |
| `bugfix/*`     | Correctifs spécifiques                           |
| `hotfix/*`     | Patches urgents à merger directement sur `main` |
| `release/*`    | Préparation d’une nouvelle version               |

## 🌱 Création de feature

1. **Créer une branche à partir de `dev` :**
   ```bash
   git checkout dev
   git pull origin dev
   git checkout -b feature/nom-feature
   ```
   ou
   ```bash
   git flow feature start nom-feature
   git flow feature finish nom-feature
   ```

2. Travail de développement
- Commits en respectant les conventionnal commits

3. Création d'une PR vers `dev`
- Ajout d'un titre clair et d'une description
- Disscussions et validations par 2 relecteurs
## 📦 Convention de commits (Conventional Commits)

Chaque commit doit suivre ce format :

### Exemples :

- `feat(auth): ajout de l’authentification JWT`
- `fix(api): correction d’une erreur 500 sur /login`
- `docs(ci): ajout de la documentation pour le pipeline`
- `refactor(core): simplification de la logique de validation`
- `test(api): ajout de tests sur l’authentification`

### Types courants :

- `feat`: ajout de fonctionnalité
- `fix`: correction de bug
- `docs`: documentation uniquement
- `style`: formatage (indentation, espace, etc.)
- `refactor`: refactoring sans ajout de feature ou fix
- `test`: ajout/modif de tests
- `chore`: tâches sans impact direct (build, outils, etc.)

---

## 🌱 Release
1. À la fin d’un sprint ou avant une mise en production :
```bash
    git checkout dev
    git pull
    git checkout -b release/x.y.z
```

## 🚀 Release & Changelog

Géré automatiquement via [semantic-release](https://semantic-release.gitbook.io/semantic-release/) :

- Génère un tag `vX.Y.Z`
- Crée la release GitHub avec changelog basé sur les commits
- Met à jour `CHANGELOG.md`
- Publie sur `main` uniquement

---

## 🔐 Branche `main` protégée

- Merge uniquement depuis `release/*` ou `hotfix/*`
- Revue obligatoire + CI
- Aucun commit direct autorisé

---

## ✅ Bonnes pratiques

- Petits commits fréquents > gros commits rares
- Commits atomiques : une idée par commit
- Pas de merge sans review
- Toujours rebaser les branches (`git pull --rebase`)

---

## 🔧 Outils recommandés

- [`commitizen`](https://github.com/commitizen/cz-cli) pour générer facilement des commits conventionnels :
  ```bash
  npx cz
  ```
  - semantic-release pour les releases automatiques
  - GitHub Actions pour CI/CD

## 📬 Contacts

- **DevOps référent** : [COSTON Lenny]
- **Dev Mobile** : [Maxence COEUR]
- **Dev API** : [Loan FRANCOIS]
- **Dev API** : [Gaël PIDOUX]
- **Dev IoT** : [Adelia FATHIPOUR]

