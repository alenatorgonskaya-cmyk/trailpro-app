# Vérification de la configuration Firebase

## ✅ Checklist de configuration

### 1. Authentication activée
- [ ] Aller dans Firebase Console > **Authentication**
- [ ] Vérifier que **Email/Password** est activé dans "Sign-in method"
- [ ] Si ce n'est pas fait, activer "Email/Password" et enregistrer

### 2. Firestore Database créée
- [ ] Aller dans Firebase Console > **Firestore Database**
- [ ] Vérifier qu'une base de données existe
- [ ] Si ce n'est pas fait, créer une base de données (mode Test ou Production)

### 3. Règles de sécurité Firestore
- [ ] Aller dans Firestore Database > **Règles**
- [ ] Vérifier que les règles suivantes sont configurées :

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Profils utilisateurs
    match /profiles/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
    
    // Objectifs
    match /goals/{goalId} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.userId;
      allow create: if request.auth != null && request.auth.uid == request.resource.data.userId;
    }
    
    // Programmes hebdomadaires
    match /weeklyPlans/{planId} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.userId;
      allow create: if request.auth != null && request.auth.uid == request.resource.data.userId;
    }
    
    // Historique des séances
    match /workouts/{workoutId} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.userId;
      allow create: if request.auth != null && request.auth.uid == request.resource.data.userId;
    }
  }
}
```

- [ ] Cliquer sur **Publier** pour sauvegarder les règles

### 4. Index Firestore (création automatique)
Les index seront créés automatiquement lors de la première utilisation. Si vous voyez une erreur dans la console du navigateur avec un lien, cliquez dessus pour créer l'index.

Sinon, créez-les manuellement dans **Firestore Database > Index** :

**Index 1 - goals**
- Collection: `goals`
- Champs: `userId` (Ascendant), `createdAt` (Descendant)

**Index 2 - weeklyPlans**
- Collection: `weeklyPlans`
- Champs: `userId` (Ascendant), `createdAt` (Descendant)

**Index 3 - workouts**
- Collection: `workouts`
- Champs: `userId` (Ascendant), `date` (Descendant)

## 🧪 Test de l'application

1. **Ouvrir l'application**
   - Ouvrez `index.html` dans votre navigateur
   - Ouvrez la console développeur (F12)

2. **Créer un compte**
   - Cliquez sur "S'inscrire"
   - Entrez un email et un mot de passe (min. 6 caractères)
   - Cliquez sur "Créer mon compte"

3. **Vérifier dans Firebase Console**
   - Allez dans **Authentication > Users**
   - Vous devriez voir votre utilisateur créé

4. **Tester la sauvegarde**
   - Créez un objectif dans l'application
   - Allez dans **Firestore Database > Data**
   - Vérifiez que les collections `goals`, `profiles`, etc. sont créées

## 🐛 Dépannage

### Erreur "Missing or insufficient permissions"
- Vérifiez que les règles de sécurité Firestore sont bien publiées
- Vérifiez que vous êtes bien connecté dans l'application

### Erreur "The query requires an index"
- Cliquez sur le lien dans l'erreur pour créer l'index automatiquement
- Ou créez l'index manuellement dans Firestore Database > Index

### L'application ne se charge pas
- Vérifiez la console du navigateur pour les erreurs
- Vérifiez que les scripts Firebase se chargent correctement
- Vérifiez que la configuration Firebase est correcte dans `index.html`

### Les données ne se sauvegardent pas
- Vérifiez que vous êtes connecté (l'email devrait apparaître dans le header)
- Vérifiez les règles de sécurité Firestore
- Vérifiez la console du navigateur pour les erreurs

## 📊 Structure des données attendue

Après utilisation, vous devriez voir dans Firestore :

- **profiles/{userId}** : Document avec le profil utilisateur
- **goals/{goalId}** : Documents avec les objectifs (champ `userId`)
- **weeklyPlans/{planId}** : Documents avec les programmes (champ `userId`)
- **workouts/{workoutId}** : Documents avec les séances (champ `userId`)

