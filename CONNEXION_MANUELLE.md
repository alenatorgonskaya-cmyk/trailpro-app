# 🔐 Connexion Firebase - Guide Manuel

## ⚠️ Problème avec la commande interactive

La commande `firebase login` nécessite une interaction dans votre terminal. Voici comment procéder :

## ✅ Solution : Exécuter dans votre terminal

### Étape 1 : Ouvrir votre terminal

Ouvrez votre terminal dans le dossier du projet :
```bash
cd /Users/torgonskayaa/Documents/PERSO/CursorProjects/trailpro-app
```

### Étape 2 : Exécuter la commande

```bash
npm run firebase:login
```

### Étape 3 : Répondre aux questions

1. **Enable Gemini in Firebase features? (Y/n)**
   - Tapez `n` et appuyez sur Entrée (ou `Y` si vous voulez activer Gemini)

2. **Votre navigateur s'ouvrira automatiquement**
   - Connectez-vous avec votre compte Google (celui utilisé pour Firebase)
   - Autorisez Firebase CLI

3. **Retournez dans le terminal**
   - Vous verrez "✔ Success! Logged in as [votre-email]"

## 🔄 Alternative : Utiliser le chemin direct

Si `npm run` ne fonctionne pas, utilisez directement :

```bash
node node_modules/firebase-tools/lib/bin/firebase.js login
```

## ✅ Vérifier la connexion

Après la connexion, vérifiez :

```bash
npm run firebase -- projects:list
```

Vous devriez voir votre projet `aliorunning` dans la liste.

## 📝 Note

Si vous avez des problèmes, vous pouvez aussi :
1. Aller sur https://console.firebase.google.com
2. Vérifier que vous êtes connecté avec le bon compte
3. Réessayer la commande `npm run firebase:login`

