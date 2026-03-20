# 🌟 JoJo's Bizarre Adventure — Personal Viewer

Application PWA personnelle pour regarder JoJo's Bizarre Adventure depuis Google Drive.

---

## 🚀 Installation rapide

### Option 1 — Hébergement local (le plus simple)
1. Mets tous les fichiers dans un dossier (ex: `jojo-viewer/`)
2. Lance un serveur local :
   ```bash
   # Python 3
   python3 -m http.server 8080
   
   # Node.js (npx)
   npx serve .
   
   # PHP
   php -S localhost:8080
   ```
3. Ouvre `http://localhost:8080` dans Chrome ou Safari
4. Sur mobile : connecte-toi au même WiFi, remplace `localhost` par l'IP de ton PC

### Option 2 — Hébergement sur GitHub Pages (accès depuis n'importe où)
1. Crée un repo GitHub (privé recommandé)
2. Upload les 3 fichiers (`index.html`, `manifest.json`, `sw.js`)
3. Active GitHub Pages dans les Settings → Pages
4. Ton app sera disponible sur `https://ton-username.github.io/repo-name`

### Option 3 — Netlify Drop (ultra simple)
1. Va sur [netlify.com/drop](https://app.netlify.com/drop)
2. Glisse le dossier complet
3. L'app est en ligne en 30 secondes (URL aléatoire)

---

## 📱 Installation sur mobile (PWA)

### Android (Chrome)
1. Ouvre l'app dans Chrome
2. Menu (⋮) → "Ajouter à l'écran d'accueil"
3. L'app apparaît comme une vraie app native !

### iPhone (Safari)
1. Ouvre l'app dans Safari
2. Bouton de partage (□↑) → "Sur l'écran d'accueil"

---

## ☁️ Configuration Google Drive

### Étape 1 — Prépare tes dossiers Drive
Structure recommandée sur Google Drive :
```
📁 JoJo's Bizarre Adventure/
├── 📁 Part 1 - Phantom Blood/
│   ├── 🎬 ep01.mp4
│   ├── 🎬 ep02.mp4
│   └── ...
├── 📁 Part 2 - Battle Tendency/
│   └── ...
└── ...
```

### Étape 2 — Récupère les IDs de dossiers
1. Ouvre un dossier sur Google Drive
2. Copie l'ID dans l'URL : `drive.google.com/drive/folders/`**`CECI_EST_L_ID`**

### Étape 3 — Configure l'app
1. Dans l'app : ⚙️ Réglages → Google Drive
2. Colle l'ID pour chaque Partie
3. Sauvegarde

### Étape 4 — Ajouter les IDs de fichiers vidéo (pour le streaming direct)
Dans `index.html`, trouve la variable `state.driveFiles` et ajoute les IDs :

```javascript
driveFiles: {
  "1-0": "ID_FICHIER_PART1_EP01",  // Part 1, épisode 1
  "1-1": "ID_FICHIER_PART1_EP02",  // Part 1, épisode 2
  "2-0": "ID_FICHIER_PART2_EP01",  // Part 2, épisode 1
  // ...
}
```

**Pour trouver l'ID d'un fichier vidéo :**
- Clic droit sur la vidéo → "Partager" → copier le lien
- L'ID est dans : `drive.google.com/file/d/`**`CECI_EST_L_ID`**`/view`

### Étape 5 — Permissions Drive
Pour que l'embed fonctionne, les vidéos doivent être partagées :
- Clic droit sur le fichier → Partager → "Toute personne avec le lien peut voir"

---

## 🎨 Personnalisation

### Modifier les titres d'épisodes
Dans `index.html`, trouve le tableau `PARTS` et modifie `epTitles` :
```javascript
{
  id: 1, name: "Phantom Blood",
  epTitles: [
    "Mon vrai titre EP1",
    "Mon vrai titre EP2",
    // ...
  ]
}
```

### Changer le thème de couleurs
Modifie les variables CSS dans `:root` :
```css
:root {
  --c-purple: #7b00ff;  /* Couleur principale */
  --c-pink:   #ff00aa;  /* Accent */
  --c-yellow: #ffe600;  /* Titre */
}
```

---

## 🧱 Structure des fichiers

```
jojo-viewer/
├── index.html      # Application complète
├── manifest.json   # Configuration PWA
├── sw.js           # Service Worker (cache offline)
├── icon-192.png    # Icône app (à ajouter)
└── icon-512.png    # Icône app large (à ajouter)
```

### Ajouter des icônes (optionnel)
Pour une vraie icône d'app sur l'écran d'accueil :
1. Crée une image carrée 512×512px avec le logo JoJo
2. Sauvegarde-la comme `icon-512.png` et une version 192×192 comme `icon-192.png`

---

## ✨ Fonctionnalités

| Fonctionnalité | Status |
|---|---|
| 6 Parties JoJo organisées | ✅ |
| Liste d'épisodes avec titres | ✅ |
| Lecteur Google Drive intégré | ✅ |
| Marquage vu / non vu | ✅ |
| Favoris | ✅ |
| Historique de visionnage | ✅ |
| "Continuer à regarder" | ✅ |
| Progression par partie | ✅ |
| Animation ORA ORA au lancement | ✅ |
| PWA installable | ✅ |
| Cache offline | ✅ |
| Export / Import de sauvegarde | ✅ |
| Écran splash animé | ✅ |

---

## 🔧 Dépannage

**La vidéo ne se charge pas :**
- Vérifie que le fichier est partagé "Toute personne avec le lien"
- Certains fichiers Drive bloquent l'embed — essaie depuis l'app Drive directement

**L'app ne s'installe pas en PWA :**
- Il faut HTTPS (GitHub Pages, Netlify fournissent ça automatiquement)
- En local, ça fonctionne quand même sans installation PWA

**Les données sont perdues :**
- Utilise Export / Import dans les Réglages pour faire des sauvegardes

---

*"Your next line is: This app is incredible!"*  
*— Dio Brando, probablement*
