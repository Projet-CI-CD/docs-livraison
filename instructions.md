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

# 🧪 Test bout-à-bout – Projet Connecté

Ce document décrit la procédure de test manuelle du projet connecté, en intégrant les trois composants du système :  
📡 Script IoT → 🔧 Backend API → 📱 Application mobile.

---

## 🛠️ Pré-requis

- Node.js (v18+ recommandé)
- Flutter SDK installé
- SQLite (inclus par défaut avec Node)
- Les trois dépôts clonés :
  - `mobile`
  - `iot`
  - `api`

---

## 🗂️ Étape 1 – Lancer l'API

### 🔧 `api`

1. Ouvre un terminal dans le dossier `api`
2. Installe les dépendances :
    ```bash
    npm install
    ````
3. Lance l'API :
    ```bash
    npm start
    ```
4. Vérifiez que l'API est accessible via `http://0.0.0.0:3000` (ou l'IP locale)

## 🗂️ Étape 2 – Lancer le script IoT

### 📡 `iot`

1. Dans sendData.js, modifie l'URL si besoin :
   ```bash
   const API_URL = "http://X.X.X.X:3000/iot";
   ```
2. Ouvre un terminal dans le dossier iot : 
   ```bash
   npm install
   node sendData.js
   ```
3. Vérifiez que : 
- Les données simulées depuis iot_devices.json sont envoyées
- L’API Express reçoit bien ces données (affichées en console ou enregistrées)

## 🗂️ Étape 3 – Lancer l'application mobile

### 📱 `mobile`

1. Dans `mobile`
    ```bash
    flutter pub get
    ```
2. Modifie l'URL de l'API dans lib/Service/api_sevrice.dart:
    ```dart	
    final String baseUrl ="http://X.X.X.X:3000";
    ```
3. Lance l'application mobile:
    ```bash
    flutter run 
    ```
4. Vérifiez que:
- Les données apparaissent dans l’application
- L’interface réagit correctement même en cas d’erreur

# ✅ Check-list de validation manuelle – Projet Connecté

---

## 📁 Général
- [x] Les trois dépôts (`iot`, `api`, `mobile`) sont accessibles
- [x] Chaque dépôt contient un `README.md` clair
- [x] Les instructions d'installation et d'exécution sont présentes
- [x] Les dépendances sont listées (`package.json`, `pubspec.yaml`, etc.)
- [x] Fichiers `.gitignore` bien configurés
- [x] Les URL d'API sont facilement modifiables dans le code
- [x] Le système peut être lancé et testé sur un même réseau local

---

## 🔧 API Backend – Express.js + SQLite (`api`)
- [x] `npm install` fonctionne sans erreur
- [x] `npm start` lance bien le serveur sur le port 3000
- [x] L’API répond bien sur `GET /iot` et/ou `POST /iot`
- [x] Les données reçues sont affichées dans la console ou stockées
- [x] Le backend gère les erreurs de manière propre
- [x] La base SQLite est fonctionnelle et persistante

---

## 📡 Script IoT – Node.js (`iot`)
- [x] `npm install` fonctionne sans erreur
- [x] Le script se lance avec `node sendData.js`
- [x] Le fichier `iot_devices.json` est utilisé pour simuler des données
- [x] Les données envoyées sont bien au format JSON :
  ```json
  {
    "device_id": "env_001",                 // 🔢 string
    "temperature": 21.5,                    // 🔢 number (float)
    "humidity": 58,                         // 🔢 number (float)
    "timestamp": "2025-04-22T14:00:00Z",    // 🕒 string (format ISO 8601 / datetime)
    "type": "environmental"                 // 🔢 string
  }
  
## 👨‍💻 Auteurs

**Lenny COSTON**  
DevOps – Coordination, tests et documentation  
lenny.coston@ynov.com


