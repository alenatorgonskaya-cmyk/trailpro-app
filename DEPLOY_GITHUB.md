# 📦 Push sur GitHub

## Étapes pour merger sur GitHub

### 1. Vérifier les changements

```bash
git status
```

### 2. Ajouter les fichiers

```bash
# Ajouter tous les fichiers modifiés et nouveaux
git add .

# Ou ajouter spécifiquement :
git add index.html
git add *.md
git add package.json
git add server.js
git add .gitignore
```

### 3. Créer un commit

```bash
git commit -m "feat: Transform app to multi-user with Firebase Auth and Firestore

- Add Firebase Authentication (email/password)
- Replace localStorage with Firestore (profiles, goals, workouts, weeklyPlans)
- Add useAuth hook for session management
- Protect routes with authentication
- Merge Profile and Goals views with tabs
- Add avatar in header (Shadcn style)
- Move logout button to account settings
- Add toast notifications (Sonner inspired)
- Auto-update planning when profile/goal changes
- Keep Shadcn/UI orange Strava design"
```

### 4. Push sur GitHub

```bash
git push origin main
```

## Si vous avez des conflits

```bash
# Récupérer les dernières modifications
git pull origin main

# Résoudre les conflits si nécessaire
# Puis :
git add .
git commit -m "Merge: resolve conflicts"
git push origin main
```

## Créer une Pull Request (si vous travaillez sur une branche)

```bash
# Créer une nouvelle branche
git checkout -b feature/firebase-integration

# Faire vos commits
git add .
git commit -m "feat: Add Firebase integration"

# Push la branche
git push origin feature/firebase-integration

# Ensuite créer une PR sur GitHub
```

## Vérifier que tout est bien commité

```bash
git log --oneline -5
git status
```

