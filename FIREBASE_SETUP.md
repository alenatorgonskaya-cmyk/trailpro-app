# Configuration Firebase pour TrailPro

## 1. Créer un projet Firebase

1. Allez sur [Firebase Console](https://console.firebase.google.com/)
2. Cliquez sur "Ajouter un projet"
3. Suivez les étapes pour créer votre projet

## 2. Activer Authentication

1. Dans la console Firebase, allez dans **Authentication**
2. Cliquez sur "Commencer"
3. Activez **Email/Password** dans les méthodes de connexion

## 3. Créer une base de données Firestore

1. Dans la console Firebase, allez dans **Firestore Database**
2. Cliquez sur "Créer une base de données"
3. Choisissez le mode **Production** ou **Test** (pour le développement)
4. Sélectionnez une région (ex: `europe-west`)

## 4. Configurer les règles de sécurité Firestore

Dans l'onglet **Règles** de Firestore, ajoutez ces règles :

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

## 5. Créer les index Firestore

Pour que les requêtes fonctionnent correctement, vous devez créer des index composites dans Firestore :

1. Allez dans **Firestore Database** > **Index**
2. Cliquez sur "Créer un index"
3. Créez ces index :

### Index 1 : goals
- Collection: `goals`
- Champs à indexer:
  - `userId` (Ascendant)
  - `createdAt` (Descendant)
- Mode: Collection

### Index 2 : weeklyPlans
- Collection: `weeklyPlans`
- Champs à indexer:
  - `userId` (Ascendant)
  - `createdAt` (Descendant)
- Mode: Collection

### Index 3 : workouts
- Collection: `workouts`
- Champs à indexer:
  - `userId` (Ascendant)
  - `date` (Descendant)
- Mode: Collection

**Note:** Firebase vous proposera automatiquement de créer ces index lorsque vous exécuterez l'application pour la première fois. Cliquez sur le lien dans la console du navigateur pour les créer.

## 6. Obtenir les credentials Firebase

1. Dans la console Firebase, allez dans **Paramètres du projet** (icône ⚙️)
2. Dans la section "Vos applications", cliquez sur l'icône Web (</>)
3. Enregistrez l'application avec un nom (ex: "TrailPro Web")
4. Copiez la configuration Firebase

## 7. Configurer l'application

Ouvrez `index.html` et remplacez la configuration Firebase dans le script (lignes ~12-19) :

```javascript
const firebaseConfig = {
    apiKey: "VOTRE_API_KEY",
    authDomain: "VOTRE_PROJECT_ID.firebaseapp.com",
    projectId: "VOTRE_PROJECT_ID",
    storageBucket: "VOTRE_PROJECT_ID.appspot.com",
    messagingSenderId: "VOTRE_MESSAGING_SENDER_ID",
    appId: "VOTRE_APP_ID"
};
```

## 8. Structure des collections Firestore

L'application utilise 4 collections :

- **profiles** : Profils utilisateurs (1 document par utilisateur, ID = userId)
- **goals** : Objectifs d'entraînement (plusieurs documents par utilisateur)
- **weeklyPlans** : Programmes hebdomadaires (1 document par utilisateur)
- **workouts** : Historique des séances (plusieurs documents par utilisateur)

Tous les documents incluent un champ `userId` pour associer les données à l'utilisateur.

## 9. Tester l'application

1. Ouvrez `index.html` dans votre navigateur
2. Créez un compte avec email/password
3. Les données seront automatiquement sauvegardées dans Firestore

## Dépannage

- **Erreur "Missing or insufficient permissions"** : Vérifiez les règles de sécurité Firestore
- **Erreur "The query requires an index"** : Créez les index manquants (Firebase vous donnera un lien)
- **Les données ne se chargent pas** : Vérifiez que l'utilisateur est bien connecté et que les règles de sécurité sont correctes

