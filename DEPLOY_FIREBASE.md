# 🚀 Déploiement sur Firebase Hosting

## Prérequis

1. **Firebase CLI installé**
   ```bash
   npm install -g firebase-tools
   ```

2. **Connecté à Firebase**
   ```bash
   firebase login
   ```

## Étapes de déploiement

### 1. Initialiser Firebase Hosting (première fois uniquement)

```bash
firebase init hosting
```

**Réponses aux questions :**
- ✅ Use an existing project → Sélectionnez `aliorunning`
- ✅ What do you want to use as your public directory? → `./` (racine du projet)
- ✅ Configure as a single-page app? → `No` (ou `Yes` si vous voulez)
- ✅ Set up automatic builds and deploys with GitHub? → `No` (pour l'instant)
- ✅ File index.html already exists. Overwrite? → `No`

### 2. Vérifier la configuration

Un fichier `firebase.json` devrait être créé. Vérifiez qu'il contient :

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

### 3. Déployer

```bash
firebase deploy --only hosting
```

### 4. Vérifier le déploiement

Une fois le déploiement terminé, vous verrez une URL comme :
```
✔ Deploy complete!

Project Console: https://console.firebase.google.com/project/aliorunning/overview
Hosting URL: https://aliorunning.web.app
```

## Commandes utiles

### Déployer uniquement le hosting
```bash
firebase deploy --only hosting
```

### Voir les déploiements
```bash
firebase hosting:channel:list
```

### Créer un preview channel
```bash
firebase hosting:channel:deploy preview
```

### Ouvrir la console Firebase
```bash
firebase open hosting:site
```

## Configuration automatique avec GitHub (optionnel)

Si vous voulez déployer automatiquement à chaque push sur GitHub :

1. Dans Firebase Console → Hosting → Connect GitHub
2. Suivez les instructions pour connecter votre repo
3. Configurez les branches à déployer (ex: `main`)

## Dépannage

### Erreur "Firebase CLI not found"
```bash
npm install -g firebase-tools
```

### Erreur "Not logged in"
```bash
firebase login
```

### Erreur "Project not found"
Vérifiez que vous êtes dans le bon projet :
```bash
firebase use aliorunning
```

### Vérifier le projet actuel
```bash
firebase projects:list
firebase use
```

## Structure recommandée

```
trailpro-app/
├── index.html          # Application principale
├── firebase.json       # Configuration Firebase Hosting
├── .firebaserc        # Configuration du projet Firebase
├── .gitignore
└── package.json
```

## Notes importantes

- ⚠️ **Ne pas commiter** les credentials Firebase dans `index.html` si vous utilisez un repo public
- ✅ Les credentials sont déjà configurés dans votre `index.html`
- ✅ Firebase Hosting sert les fichiers statiques, parfait pour votre application React standalone
- ✅ L'application fonctionnera sur `https://aliorunning.web.app` ou `https://aliorunning.firebaseapp.com`

