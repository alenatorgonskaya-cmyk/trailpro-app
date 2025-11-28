[README.md](https://github.com/user-attachments/files/23825934/README.md)
# 🏃‍♀️ TrailPro - Application d'Entraînement Course & Trail

Application web progressive pour générer des programmes d'entraînement personnalisés adaptés aux courses sur route et en trail.

![Version](https://img.shields.io/badge/version-1.0.0-orange)
![License](https://img.shields.io/badge/license-MIT-blue)

## ✨ Fonctionnalités

### 🎯 Gestion d'objectifs
- Définir un objectif de course (distance, dénivelé, date)
- 3 types de préparation :
  - 🏃 **Route/Piste** - Focus VMA et fractionnés courts
  - 🌲 **Trail mixte** - Équilibre fractionné et côtes
  - ⛰️ **Trail montagne** - Focus dénivelé

### 👤 Profil personnalisé
- 4 niveaux : Débutant / Intermédiaire / Avancé / Expert
- Stats personnelles (meilleur 5K, 10K, VMA)
- Volume d'entraînement : Léger / Moyen / Élevé
- Mode Challenge pour intensifier
- Option course en salle avec calcul d'inclinaison tapis

### 📅 Programme adaptatif
- Génération automatique sur plusieurs semaines
- 6 types de séances :
  - Endurance (70-75% FC max)
  - Fractionné VMA court (90-95% FC max)
  - Fractionné tempo moyen (85-90% FC max)
  - Tempo run (82-87% FC max)
  - Côtes (80-88% FC max)
  - Sortie longue (65-72% FC max)
- **Algorithme TRIMP** pour calibrer la charge
- Séances minimum 20 minutes
- Mix intelligent plat/dénivelé

### 📊 Suivi de progression
- Validation de séances avec données réelles
- Note de difficulté (1-5) pour adaptation
- Historique complet avec statistiques
- Progression vers objectif (distance, dénivelé, assiduité)
- Calendrier d'activité sur 28 jours
- Recalcul automatique du programme selon performances

### 🏋️ Flexibilité d'entraînement
- **Séances hebdomadaires libres** : pas de dates fixes
- Valide les séances quand tu veux dans la semaine
- Semaines futures verrouillées 🔒
- Séances validées non modifiables

## 🚀 Installation

### Utilisation simple
1. Télécharge `index.html`
2. Ouvre-le dans ton navigateur
3. C'est tout ! Aucune installation nécessaire

### Déploiement web
```bash
# GitHub Pages
git init
git add .
git commit -m "Deploy TrailPro"
git branch -M main
git remote add origin [votre-repo]
git push -u origin main
# Activer GitHub Pages dans Settings

# Netlify / Vercel
# Drag & drop le dossier dans l'interface
```

## 💻 Technologies

- **Frontend** : React 18 (standalone, pas de build)
- **Styling** : CSS moderne (Shadcn/UI inspired)
- **Storage** : localStorage (données locales)
- **Fonts** : DM Sans (Google Fonts)

## 🧮 Algorithme TRIMP

L'application utilise l'algorithme **TRIMP (Training Impulse)** pour calculer la charge d'entraînement :

```
TRIMP = Durée (min) × Facteur de zone FC

Zones FC et facteurs :
- Zone 1 (50-60% FC max) : facteur 1
- Zone 2 (60-70% FC max) : facteur 2
- Zone 3 (70-80% FC max) : facteur 3
- Zone 4 (80-90% FC max) : facteur 4
- Zone 5 (90-100% FC max) : facteur 5
```

Le TRIMP hebdomadaire cible est adapté selon :
- Niveau de l'utilisateur (200-500 TRIMP/semaine)
- Volume d'entraînement (±15%)
- Mode challenge (+5%)

## 📱 Responsive

✅ Desktop  
✅ Tablette  
✅ Mobile  

## 🗂️ Structure des données

### localStorage Keys
- `userProfile` - Profil utilisateur
- `trainingGoal` - Objectif actuel
- `weeklyPlan` - Programme généré
- `trainingHistory` - Historique des séances

### Format Workout
```json
{
  "id": "w1-1",
  "name": "Endurance",
  "type": "endurance",
  "distance": 8.5,
  "elevation": 150,
  "estimatedTime": 50,
  "description": "Allure confortable, 70-75% FC max",
  "fcPercent": 72,
  "trimp": 150,
  "includeFlat": false
}
```

## 🎨 Design System

### Couleurs
- **Primary** : `#FC4C02` (Orange Strava)
- **Grays** : `#fafafa` → `#171717`
- **Success** : `#10B981`
- **Warning** : `#F59E0B`

### Typography
- **Font** : DM Sans
- **Weights** : 400, 500, 600, 700

## 🛣️ Roadmap

### Version actuelle (1.0)
- [x] Profil utilisateur complet
- [x] Génération programme adaptatif
- [x] Validation séances avec difficulté
- [x] Algorithme TRIMP
- [x] Séances min 20 min
- [x] Mix plat/dénivelé
- [x] Volume d'entraînement
- [x] Mode challenge
- [x] Option course en salle

### Futures versions
- [ ] Backend (Flask + PostgreSQL)
- [ ] Authentification multi-utilisateurs
- [ ] Export PDF du programme
- [ ] Intégration Strava API
- [ ] Stats avancées (VO2max, temps de récupération)
- [ ] Notifications push
- [ ] Mode coach avec ajustements manuels
- [ ] Graphiques de progression
- [ ] Recommandations nutritionnelles

## 🤝 Contribution

Les contributions sont les bienvenues ! N'hésite pas à :
1. Fork le projet
2. Créer une branche (`git checkout -b feature/AmazingFeature`)
3. Commit (`git commit -m 'Add AmazingFeature'`)
4. Push (`git push origin feature/AmazingFeature`)
5. Ouvrir une Pull Request

## 📄 License

MIT License - voir LICENSE pour plus de détails

## 👏 Crédits

- Design inspiré de [Shadcn/UI](https://ui.shadcn.com/)
- Palette orange inspirée de [Strava](https://www.strava.com/)
- Algorithme TRIMP basé sur les recherches de Banister et al.

## 📧 Contact

Pour questions ou suggestions : ouvre une issue sur GitHub

---

**Fait avec ❤️ pour les coureurs qui aiment les défis** 🏃‍♀️⛰️
