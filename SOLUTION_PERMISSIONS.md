# ✅ Solution : Erreur de permissions Firebase CLI

## 🎯 Bonne nouvelle !

**Firebase CLI est déjà installé localement** dans votre projet ! Vous n'avez **PAS besoin** de l'installer globalement.

## ✅ Utilisation

Au lieu d'utiliser `firebase` directement, utilisez `npx firebase` :

```bash
# ❌ Ne fonctionne pas (besoin de sudo)
firebase login

# ✅ Fonctionne (utilise la version locale)
npx firebase login
```

## 🚀 Commandes pour déployer

### 1. Se connecter à Firebase
```bash
npx firebase login
```

### 2. Initialiser Firebase Hosting (première fois)
```bash
npx firebase init hosting
```

**Réponses :**
- Use existing project → `aliorunning`
- Public directory → `./` (appuyez sur Entrée)
- Single-page app → `No`
- GitHub deploys → `No`
- Overwrite index.html → `No`

### 3. Déployer
```bash
npx firebase deploy --only hosting
```

## 📦 Ou utiliser les scripts npm

J'ai ajouté des scripts dans `package.json` pour simplifier :

```bash
# Se connecter
npm run firebase:login

# Initialiser (première fois)
npm run firebase:init

# Déployer
npm run deploy
# ou
npm run firebase:deploy
```

## 🔍 Vérification

Vérifiez que Firebase CLI fonctionne :
```bash
npx firebase --version
# Devrait afficher : 14.26.0
```

## 💡 Pourquoi cette erreur ?

L'erreur `EACCES: permission denied` apparaît quand vous essayez d'installer un package globalement (`-g`) sans les permissions administrateur. 

**Solution :** Utilisez l'installation locale (déjà faite) avec `npx` au lieu de l'installation globale.

## ✅ Avantages de l'installation locale

- ✅ Pas besoin de sudo
- ✅ Version spécifique par projet
- ✅ Pas de conflits entre projets
- ✅ Fonctionne sur tous les systèmes

