# TicketApp

# TicketApp 🎫

Application mobile de gestion de tickets développée avec React Native (Expo) et Firebase.

## 📱 Aperçu

TicketApp est une solution complète de support client permettant aux utilisateurs de créer des tickets d'assistance et aux administrateurs de les gérer efficacement.

### Fonctionnalités principales

#### Pour les utilisateurs :
- 🔐 **Authentification sécurisée** (inscription/connexion)
- ✨ **Dashboard élégant** avec statistiques personnelles
- 📝 **Création de tickets** avec priorités et descriptions détaillées
- 📋 **Gestion de ses tickets** (consultation, suivi du statut)
- 🎨 **Interface moderne** et sobre

#### Pour les administrateurs :
- 👨‍💼 **Dashboard administrateur** dédié
- 📊 **Vue d'ensemble globale** de tous les tickets
- 🔍 **Filtrage avancé** par statut (Ouverts, En cours, Fermés)
- 💬 **Système de réponses** aux tickets utilisateurs
- ⚡ **Gestion des statuts** (Mettre en cours, Résoudre)
- 📈 **Statistiques temps réel** (total, urgents, etc.)

## 🛠 Technologies utilisées

- **Frontend** : React Native avec Expo
- **Backend** : Firebase (Authentication + Firestore)
- **Langage** : TypeScript
- **Navigation** : Navigation par états (App.tsx)
- **UI/UX** : Design system cohérent et moderne

## 🚀 Installation

### Prérequis
- Node.js (v16 ou supérieur)
- npm ou yarn
- Expo CLI (`npm install -g @expo/cli`)
- Application Expo Go sur votre téléphone

### Configuration

1. **Cloner le projet**
   ```bash
   git clone TicketApp
   cd TicketApp
   ```

2. **Installer les dépendances**
   ```bash
   npm install
   ```

3. **Configuration Firebase**
   - Créez un projet sur [Firebase Console](https://console.firebase.google.com)
   - Activez Authentication (Email/Password)
   - Activez Firestore Database
   - Récupérez votre configuration et mettez à jour `firebaseConfig.ts`

4. **Lancer l'application**
   ```bash
   npx expo start
   ```

5. **Scanner le QR code** avec Expo Go

## 📁 Structure du projet

```
TicketApp/
├── components/           # Composants réutilisables
│   └── AuthScreen.tsx   # Écran d'authentification
├── screens/             # Écrans principaux
│   ├── HomeScreen.tsx           # Dashboard utilisateur
│   ├── AdminDashboard.tsx       # Dashboard administrateur
│   ├── CreateTicketScreen.tsx   # Création de tickets
│   └── TicketListScreen.tsx     # Liste des tickets
├── hooks/               # Hooks personnalisés
│   └── useUserRole.ts   # Gestion des rôles utilisateurs
├── firebaseConfig.ts    # Configuration Firebase
├── App.tsx             # Point d'entrée et navigation
└── metro.config.js     # Configuration Metro (Expo Go)
```

## 🔐 Système d'authentification

### Utilisateurs normaux
Tout nouvel utilisateur s'inscrivant via l'app a automatiquement le rôle `user`.

### Administrateurs
L'email `yanis.ms@icloud.com` muni du mot de passe "22112003" est automatiquement reconnu comme administrateur.

Pour ajouter d'autres administrateurs, modifiez le tableau `ADMIN_EMAILS` dans le hook `useUserRole`.

## 🎨 Design System

### Palette de couleurs
- **Primary** : `#1E293B` (Slate 800)
- **Secondary** : `#64748B` (Slate 500)
- **Success** : `#10B981` (Emerald 500)
- **Warning** : `#F59E0B` (Amber 500)
- **Error** : `#EF4444` (Red 500)
- **Background** : `#F8FAFC` (Slate 50)

### Composants
- **Cards** : Bordures arrondies (12px), ombres subtiles
- **Boutons** : Styles cohérents avec états hover/disabled
- **Typography** : Hiérarchie claire et lisible

## 📊 Base de données (Firestore)

### Collections principales

#### `users`
```typescript
{
  firstName: string
  lastName: string
  email: string
  role: 'user' | 'admin'
  createdAt: timestamp
  updatedAt: timestamp
}
```

#### `tickets`
```typescript
{
  title: string
  description: string
  priority: 'Low' | 'Medium' | 'High' | 'Urgent'
  status: 'Open' | 'In Progress' | 'Closed'
  userId: string
  userEmail: string
  createdAt: timestamp
  updatedAt: timestamp
}
```

#### `tickets/{ticketId}/responses` (sous-collection)
```typescript
{
  message: string
  isAdmin: boolean
  authorEmail: string
  createdAt: timestamp
}
```

## 🔧 Configuration Metro

Pour la compatibilité avec Expo Go, le fichier `metro.config.js` inclut :
```javascript
defaultConfig.resolver.sourceExts.push('cjs');
defaultConfig.resolver.unstable_enablePackageExports = false;
```

## 📱 Captures d'écran

### Interface utilisateur
- Écran d'authentification élégant
- Dashboard avec statistiques personnelles
- Création de tickets intuitive
- Liste des tickets avec filtres

### Interface administrateur
- Badge ADMIN visible
- Vue globale de tous les tickets
- Filtres par statut
- Modal de gestion des tickets
- Système de réponses intégré

## 🚀 Déploiement

### Expo Go (Développement)
L'application fonctionne parfaitement avec Expo Go pour le développement et les tests.

### Build Production
Pour une version de production :
```bash
expo build:android
expo build:ios
```

## 🤝 Contribution

1. Fork le projet
2. Créez votre branche (`git checkout -b feature/amazing-feature`)
3. Commit vos changements (`git commit -m 'Add amazing feature'`)
4. Push sur la branche (`git push origin feature/amazing-feature`)
5. Ouvrez une Pull Request


## 👨‍💻 Auteur

Développé avec ❤️ par [ShawLiiath]

## 🆘 Support

Pour toute question ou problème :
- Ouvrez une issue sur GitHub
- Contactez l'équipe de développement

---

**TicketApp** - Solution moderne de gestion de tickets pour un support client efficace.
