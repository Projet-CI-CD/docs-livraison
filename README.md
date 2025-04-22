# docs-livraison
Documentation de livraison du projet connecté : tests manuels des composants (mobile, backend, IoT), procédure de validation, architecture et checklist finale.

# 📦 Documentation de Livraison – Projet Connecté

Bienvenue dans le dépôt de documentation centralisée du projet connecté.  
Ce projet est composé de trois composants indépendants, chacun maintenu dans un dépôt Git distinct.

Ce dépôt `docs` fournit :
- Une vue d’ensemble du système
- Les instructions de test bout-à-bout
- Les checklists de validation manuelle

---

## 🧩 Composants du projet

### 1. 📱 Application Mobile (`mobile`)
- **Langage/Technologie** : Flutter
- **Fonction** : Affiche les dernières données reçues depuis le backend Express (température, humidité).
- **Actions** : L'utilisateur visualise les données en temps réel simulées par le module IoT.
- **Lien** : [github.com/Projet-CI-CD/mobile](https://github.com/Projet-CI-CD/mobile)

---

### 2. 📡 IoT (`iot`)
- **Langage/Technologie** : JavaScript (Node.js)
- **Fonction** : Simule un capteur connecté qui lit un fichier `iot_devices.json` et envoie périodiquement des données en POST au backend.
- **Actions** : Envoie des données de température et d'humidité toutes les X secondes.
- **Lien** : [github.com/Projet-CI-CD/IoT](https://github.com/Projet-CI-CD/IoT)

---

### 3. 🔧 Backend API (`api`)
- **Langage/Technologie** : JavaScript (Node.js avec Express.js) + SQLite
- **Fonction** : Reçoit les données JSON envoyées par le script IoT, les stocke dans une base SQLite, et les rend disponibles à l’application mobile.
- **Endpoint principal** : `POST /iot` (pour recevoir), `GET /iot` (pour consulter les 20 derniers) et `GET /iot?last_id=60` (pour consulter les 20 precedents le last_id donc du 59 au 40)
- **Lien** : [github.com/Projet-CI-CD/API](https://github.com/Projet-CI-CD/API)

---

## 🧪 Procédure de test globale

Consultez le fichier [`test-end-to-end.md`](./test-end-to-end.md) pour une procédure pas à pas afin de tester le système dans son ensemble.

## ✅ Validation

Consultez la checklist DevOps dans [`checklist.md`](./checklist.md) pour suivre les étapes de vérification manuelle des composants et de l’intégration.

---

## 👨‍💻 Auteurs

**Lenny COSTON**  
DevOps – Coordination, tests et documentation  
lenny.coston@ynov.com

