# Guide des nouvelles fonctionnalités

## ✅ Modifications apportées

### 1. Écran de connexion/inscription

**Où le trouver :**
- Si vous n'êtes **pas connecté**, l'écran de connexion s'affiche automatiquement
- Vous verrez un formulaire avec :
  - Titre "TrailPro"
  - Champ Email
  - Champ Mot de passe
  - Bouton "Se connecter" ou "Créer mon compte"
  - Lien pour basculer entre connexion et inscription

**Comment tester :**
1. Ouvrez `index.html` dans votre navigateur
2. Si vous êtes déjà connecté, déconnectez-vous (bouton "Déconnexion" en haut à droite)
3. L'écran de connexion devrait apparaître automatiquement
4. Cliquez sur "Pas encore de compte ? S'inscrire" pour créer un compte
5. Ou connectez-vous avec un compte existant

**Fonctionnalités :**
- ✅ Messages d'erreur en français
- ✅ Validation des champs
- ✅ Bascule entre connexion/inscription

---

### 2. Section "Paramètres du compte" dans le profil

**Où le trouver :**
1. Connectez-vous à l'application
2. Cliquez sur "Profil" dans le menu de navigation (en haut)
3. Faites défiler jusqu'en bas de la page
4. Vous verrez une nouvelle carte **"Paramètres du compte"** après la carte "VMA estimée"

**Ce que vous verrez :**
- **Email** : Votre adresse email (non modifiable)
- **Compte créé le** : Date et heure de création de votre compte
- **Bouton "Changer le mot de passe"** : Pour modifier votre mot de passe

**Comment changer votre mot de passe :**
1. Dans la section "Paramètres du compte"
2. Cliquez sur "Changer le mot de passe"
3. Remplissez le formulaire :
   - Mot de passe actuel
   - Nouveau mot de passe (min. 6 caractères)
   - Confirmer le nouveau mot de passe
4. Cliquez sur "Modifier"

---

## 🔍 Vérification que tout fonctionne

### Si vous ne voyez pas les changements :

1. **Rafraîchir le navigateur :**
   - Appuyez sur `Ctrl + F5` (Windows/Linux) ou `Cmd + Shift + R` (Mac)
   - Ou videz le cache du navigateur

2. **Vérifier que le fichier est bien sauvegardé :**
   - Dans votre éditeur, vérifiez que le fichier `index.html` est bien sauvegardé
   - Les modifications sont aux lignes :
     - Ligne ~1153 : État pour le changement de mot de passe
     - Ligne ~1246 : Fonction `handlePasswordChange`
     - Ligne ~2259 : Section "Paramètres du compte"

3. **Vérifier la console du navigateur :**
   - Appuyez sur `F12` pour ouvrir les outils développeur
   - Allez dans l'onglet "Console"
   - Vérifiez s'il y a des erreurs JavaScript

4. **Tester l'authentification :**
   - Déconnectez-vous si vous êtes connecté
   - Vous devriez voir l'écran de connexion
   - Créez un nouveau compte ou connectez-vous

---

## 📍 Emplacements dans le code

### Écran de connexion
- **Ligne ~1317-1375** : Code de l'écran de connexion/inscription
- **Ligne ~1195-1237** : Fonction `handleAuth` pour gérer la connexion

### Paramètres du compte
- **Ligne ~2259-2370** : Section "Paramètres du compte" dans le profil
- **Ligne ~1246-1306** : Fonction `handlePasswordChange` pour changer le mot de passe
- **Ligne ~1153-1159** : États pour le formulaire de changement de mot de passe

### Hook useAuth
- **Ligne ~964-995** : Hook `useAuth` avec fonctions `signIn`, `signUp`, `signOut`, `updatePassword`, `reauthenticate`

---

## 🧪 Test complet

1. **Test de connexion :**
   - Ouvrez `index.html`
   - Vous devriez voir l'écran de connexion
   - Créez un compte avec email/password
   - Vous devriez être redirigé vers l'application

2. **Test du profil :**
   - Cliquez sur "Profil" dans le menu
   - Faites défiler jusqu'en bas
   - Vous devriez voir "Paramètres du compte"
   - Votre email devrait être affiché

3. **Test du changement de mot de passe :**
   - Cliquez sur "Changer le mot de passe"
   - Remplissez le formulaire
   - Testez avec un mauvais mot de passe actuel (devrait afficher une erreur)
   - Testez avec le bon mot de passe (devrait fonctionner)

---

## ❓ Problèmes courants

### "Je ne vois pas l'écran de connexion"
- Vérifiez que vous êtes bien déconnecté
- Videz le cache du navigateur
- Vérifiez la console pour les erreurs

### "Je ne vois pas la section Paramètres du compte"
- Assurez-vous d'être connecté
- Allez dans "Profil" (pas "Objectif")
- Faites défiler jusqu'en bas de la page
- La section est après "VMA estimée"

### "Le changement de mot de passe ne fonctionne pas"
- Vérifiez que vous avez bien rempli tous les champs
- Le mot de passe actuel doit être correct
- Le nouveau mot de passe doit faire au moins 6 caractères
- Les deux nouveaux mots de passe doivent correspondre

