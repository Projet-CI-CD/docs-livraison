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
    npm instrall
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

## 👨‍💻 Auteurs

**Lenny COSTON**  
DevOps – Coordination, tests et documentation  
lenny.coston@ynov.com


