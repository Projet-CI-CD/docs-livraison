# ✅ Check-list de validation manuelle – Projet Connecté

---

## 📁 Général
- [] Les trois dépôts (`iot`, `api`, `mobile`) sont accessibles
- [] Chaque dépôt contient un `README.md` clair
- [] Les instructions d'installation et d'exécution sont présentes
- [] Les dépendances sont listées (`package.json`, `pubspec.yaml`, etc.)
- [] Fichiers `.gitignore` bien configurés
- [] Les URL d'API sont facilement modifiables dans le code
- [] Le système peut être lancé et testé sur un même réseau local

---

## 🔧 API Backend – Express.js + SQLite (`api`)
- *[] `npm install` fonctionne sans erreur
- [] `npm start` lance bien le serveur sur le port 3000
- [] L’API répond bien sur `GET /iot` et/ou `POST /iot`
- [] Les données reçues sont affichées dans la console ou stockées
- [] Le backend gère les erreurs de manière propre
- [] La base SQLite est fonctionnelle et persistante

---

## 📡 Script IoT – Node.js (`iot`)
- [] `npm install` fonctionne sans erreur
- [] Le script se lance avec `node sendData.js`
- [] Le fichier `iot_devices.json` est utilisé pour simuler des données
- [] Les données envoyées sont bien au format JSON :
  ```json
  {
    "device_id": "env_001",                 // 🔢 string
    "temperature": 21.5,                    // 🔢 number (float)
    "humidity": 58,                         // 🔢 number (float)
    "timestamp": "2025-04-22T14:00:00Z",    // 🕒 string (format ISO 8601 / datetime)
    "type": "environmental"                 // 🔢 string
  }
