# 🚀 Déploiement Firebase - Guide Rapide

## ✅ GitHub : Terminé !
Vos changements ont été pushés sur GitHub avec succès ! 🎉

## 🔥 Firebase Hosting : À faire

### Option 1 : Installation locale (recommandé, pas de sudo)

```bash
# Installer Firebase CLI localement dans le projet
npm install firebase-tools --save-dev

# Utiliser avec npx
npx firebase login
npx firebase init hosting
npx firebase deploy --only hosting
```

### Option 2 : Installation globale (nécessite sudo)

```bash
# Installer Firebase CLI globalement
sudo npm install -g firebase-tools

# Se connecter
firebase login

# Initialiser Firebase Hosting
firebase init hosting
```

## 📋 Étapes détaillées

### 1. Se connecter à Firebase

```bash
npx firebase login
# ou
firebase login
```

Cela ouvrira votre navigateur pour vous authentifier.

### 2. Initialiser Firebase Hosting

```bash
npx firebase init hosting
# ou
firebase init hosting
```

**Réponses aux questions :**
- ✅ **Use an existing project** → Sélectionnez `aliorunning`
- ✅ **What do you want to use as your public directory?** → `./` (appuyez sur Entrée)
- ✅ **Configure as a single-page app?** → `No` (ou `Yes` si vous préférez)
- ✅ **Set up automatic builds and deploys with GitHub?** → `No` (pour l'instant)
- ✅ **File index.html already exists. Overwrite?** → `No`

### 3. Vérifier la configuration

Un fichier `firebase.json` devrait être créé. Vérifiez qu'il ressemble à :

```json
{
  "hosting": {
    "public": "./",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
}
```

### 4. Déployer

```bash
npx firebase deploy --only hosting
# ou
firebase deploy --only hosting
```

### 5. Votre app sera disponible sur :

- 🌐 **https://aliorunning.web.app**
- 🌐 **https://aliorunning.firebaseapp.com**

## ✅ Vérification après déploiement

Testez ces fonctionnalités :
1. ✅ Connexion/Inscription
2. ✅ Création d'un objectif
3. ✅ Modification du profil
4. ✅ Validation d'une séance
5. ✅ Toasts de confirmation
6. ✅ Navigation avec tabs

## 🔄 Mises à jour futures

Pour déployer de nouvelles versions :

```bash
# 1. Commit et push sur GitHub
git add .
git commit -m "feat: nouvelle fonctionnalité"
git push origin main

# 2. Déployer sur Firebase
npx firebase deploy --only hosting
# ou
firebase deploy --only hosting
```

## 📝 Notes

- Les fichiers `firebase.json` et `.firebaserc` seront créés automatiquement
- Ne commitez pas `.firebaserc` si vous travaillez en équipe (déjà dans .gitignore)
- L'application est statique, donc le déploiement est très rapide
- Firebase Hosting offre un CDN global pour de meilleures performances

