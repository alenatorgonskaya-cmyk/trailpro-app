# 🚀 Comment lancer l'application TrailPro

## Option 1 : Avec Node.js (Recommandé)

### Prérequis
- Node.js installé sur votre machine ([télécharger ici](https://nodejs.org/))

### Étapes

1. **Ouvrir un terminal** dans le dossier du projet
   ```bash
   cd /Users/torgonskayaa/Documents/PERSO/CursorProjects/trailpro-app
   ```

2. **Lancer le serveur**
   ```bash
   node server.js
   ```
   
   Ou si vous avez npm installé :
   ```bash
   npm start
   ```

3. **Ouvrir votre navigateur**
   - Allez sur : `http://localhost:3000`
   - L'application devrait se charger correctement

4. **Arrêter le serveur**
   - Appuyez sur `Ctrl + C` dans le terminal

---

## Option 2 : Avec Python (si Node.js n'est pas installé)

### Python 3

1. **Ouvrir un terminal** dans le dossier du projet
   ```bash
   cd /Users/torgonskayaa/Documents/PERSO/CursorProjects/trailpro-app
   ```

2. **Lancer le serveur**
   ```bash
   python3 -m http.server 3000
   ```

3. **Ouvrir votre navigateur**
   - Allez sur : `http://localhost:3000`

---

## Option 3 : Avec PHP (si installé)

1. **Ouvrir un terminal** dans le dossier du projet
   ```bash
   cd /Users/torgonskayaa/Documents/PERSO/CursorProjects/trailpro-app
   ```

2. **Lancer le serveur**
   ```bash
   php -S localhost:3000
   ```

3. **Ouvrir votre navigateur**
   - Allez sur : `http://localhost:3000`

---

## Option 4 : Extension VS Code / Cursor

Si vous utilisez VS Code ou Cursor :

1. **Installer l'extension "Live Server"**
   - Recherchez "Live Server" dans les extensions
   - Installez-la

2. **Lancer le serveur**
   - Clic droit sur `index.html`
   - Sélectionnez "Open with Live Server"

---

## ⚠️ Pourquoi utiliser un serveur local ?

Ouvrir directement `index.html` dans le navigateur (double-clic) peut causer des problèmes :

- ❌ Les modules ES6 peuvent ne pas fonctionner
- ❌ Firebase peut avoir des problèmes avec les CORS
- ❌ Certaines fonctionnalités JavaScript peuvent être bloquées
- ❌ Les requêtes HTTP peuvent échouer

Avec un serveur local :
- ✅ Tout fonctionne correctement
- ✅ Firebase se charge sans problème
- ✅ Pas de problèmes de CORS
- ✅ Environnement de développement optimal

---

## 🐛 Dépannage

### "Port 3000 déjà utilisé"
Changez le port dans `server.js` :
```javascript
const PORT = 3001; // ou un autre port
```

### "node: command not found"
Installez Node.js depuis [nodejs.org](https://nodejs.org/)

### "Erreur lors du chargement de Firebase"
1. Vérifiez votre connexion internet
2. Ouvrez la console du navigateur (F12)
3. Vérifiez les erreurs dans l'onglet "Console"
4. Vérifiez que la configuration Firebase est correcte

### L'application ne se charge pas
1. Vérifiez que le serveur est bien lancé
2. Vérifiez l'URL dans le navigateur (`http://localhost:3000`)
3. Ouvrez la console du navigateur (F12) pour voir les erreurs
4. Vérifiez que `index.html` est bien dans le même dossier que `server.js`

---

## ✅ Vérification que tout fonctionne

1. **Le serveur démarre sans erreur**
   - Vous devriez voir : `🚀 Serveur lancé sur http://localhost:3000`

2. **L'application se charge dans le navigateur**
   - Vous devriez voir l'écran de connexion
   - Pas d'erreurs dans la console (F12)

3. **Firebase se connecte**
   - Ouvrez la console (F12)
   - Pas d'erreurs liées à Firebase
   - Vous pouvez créer un compte

---

## 📝 Notes

- Le serveur doit rester ouvert pendant que vous utilisez l'application
- Si vous modifiez le code, rafraîchissez simplement la page (F5)
- Pour arrêter le serveur, appuyez sur `Ctrl + C` dans le terminal

