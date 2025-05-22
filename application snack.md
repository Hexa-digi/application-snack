# Guide de déploiement sur Netlify

## 📁 Structure des fichiers nécessaires

### 1. **package.json**
```json
{
  "name": "restaurant-tunisien",
  "version": "1.0.0",
  "private": true,
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0",
    "lucide-react": "^0.263.1"
  },
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  },
  "devDependencies": {
    "react-scripts": "5.0.1",
    "tailwindcss": "^3.3.0",
    "autoprefixer": "^10.4.14",
    "postcss": "^8.4.31"
  },
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
}
```

### 2. **tailwind.config.js**
```javascript
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

### 3. **postcss.config.js**
```javascript
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

### 4. **public/index.html**
```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#dc2626" />
    <meta
      name="description"
      content="Application de gestion pour restaurant tunisien"
    />
    <title>Restaurant Tunisien - Gestion</title>
  </head>
  <body>
    <noscript>Vous devez activer JavaScript pour utiliser cette application.</noscript>
    <div id="root"></div>
  </body>
</html>
```

### 5. **src/index.css**
```css
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```

### 6. **src/index.js**
```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

### 7. **src/App.js**
```javascript
// Copiez tout le code de l'artifact RestaurantApp ici
// (Le code complet de l'application que j'ai créé précédemment)
```

## 🚀 Étapes de déploiement

### Option 1 : Déploiement via GitHub (Recommandé)

1. **Créer un nouveau repository GitHub**
   - Allez sur github.com et créez un nouveau repository
   - Nommez-le "restaurant-tunisien" ou comme vous voulez

2. **Initialiser le projet localement**
   ```bash
   npx create-react-app restaurant-tunisien
   cd restaurant-tunisien
   ```

3. **Remplacer les fichiers**
   - Remplacez le contenu des fichiers avec ceux fournis ci-dessus
   - Copiez le code de l'application dans `src/App.js`

4. **Installer les dépendances**
   ```bash
   npm install lucide-react
   npm install -D tailwindcss postcss autoprefixer
   ```

5. **Pusher sur GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/VOTRE-USERNAME/restaurant-tunisien.git
   git push -u origin main
   ```

6. **Connecter à Netlify**
   - Allez sur [netlify.com](https://netlify.com)
   - Connectez-vous avec GitHub
   - Cliquez sur "New site from Git"
   - Choisissez votre repository
   - Build command: `npm run build`
   - Publish directory: `build`
   - Cliquez sur "Deploy site"

### Option 2 : Déploiement manuel (Plus rapide)

1. **Créer et builder le projet**
   ```bash
   npx create-react-app restaurant-tunisien
   cd restaurant-tunisien
   # Remplacez les fichiers
   npm install lucide-react
   npm install -D tailwindcss postcss autoprefixer
   npm run build
   ```

2. **Déployer sur Netlify**
   - Allez sur [app.netlify.com/drop](https://app.netlify.com/drop)
   - Glissez-déposez le dossier `build` sur la page
   - Votre site sera en ligne instantanément !

## 🔧 Configuration supplémentaire

### Nom de domaine personnalisé
- Dans Netlify, allez dans "Domain settings"
- Ajoutez votre domaine personnalisé
- Suivez les instructions DNS

### Variables d'environnement (si nécessaire)
- Dans Netlify, allez dans "Site settings" > "Environment variables"
- Ajoutez vos variables si besoin

## 📱 Optimisations recommandées

1. **Ajoutez un manifest.json** dans `public/` pour PWA :
```json
{
  "short_name": "Resto Tunisien",
  "name": "Restaurant Tunisien",
  "icons": [
    {
      "src": "favicon.ico",
      "sizes": "64x64 32x32 24x24 16x16",
      "type": "image/x-icon"
    }
  ],
  "start_url": ".",
  "display": "standalone",
  "theme_color": "#dc2626",
  "background_color": "#ffffff"
}
```

2. **Créez un _redirects** dans `public/` :
```
/* /index.html 200
```

## ✅ Votre site sera accessible à :
- URL temporaire : `https://VOTRE-SITE.netlify.app`
- URL personnalisée : Configurable dans les paramètres

L'application fonctionnera parfaitement sur tablette et mobile !
