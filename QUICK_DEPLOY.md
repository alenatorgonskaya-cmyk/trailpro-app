# ⚡ Déploiement Rapide

## 🚀 Push sur GitHub

```bash
# 1. Commit les changements
git commit -m "feat: Transform app to multi-user with Firebase

- Add Firebase Auth & Firestore
- Merge Profile/Goals with tabs
- Add toast notifications
- Auto-update planning
- Add avatar in header"

# 2. Push sur GitHub
git push origin main
```

## 🔥 Déployer sur Firebase Hosting

### Installation Firebase CLI (si pas déjà fait)
```bash
npm install -g firebase-tools
```

### Connexion à Firebase
```bash
firebase login
```

### Initialiser Firebase Hosting (première fois)
```bash
firebase init hosting
```
**Réponses :**
- Use existing project → `aliorunning`
- Public directory → `./` (appuyez sur Entrée)
- Single-page app → `No`
- GitHub deploys → `No`
- Overwrite index.html → `No`

### Déployer
```bash
firebase deploy --only hosting
```

### Votre app sera disponible sur :
- https://aliorunning.web.app
- https://aliorunning.firebaseapp.com

## ✅ Vérification

Après le déploiement, testez :
1. ✅ Connexion/Inscription
2. ✅ Création d'un objectif
3. ✅ Modification du profil
4. ✅ Validation d'une séance
5. ✅ Toasts de confirmation

