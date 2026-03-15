# Guide Complet : Intégration de Vidéos dans votre Portfolio

## ✅ Ce qui a été fait

### 1. **Modifications du système**
- Mise à jour du JavaScript de `elyad-marketing.html` pour supporter les vidéos
- Ajout du CSS pour afficher correctement les vidéos dans la lightbox
- Création d'une page dédiée `videos-demo.html` pour les montages vidéo
- Ajout d'une carte "Montages Vidéo" dans votre page d'accueil

### 2. **Page de démonstration créée**
- Fichier: `videos-demo.html`
- Contient: 4 vidéos de démonstration avec contrôles HTML5
- Design: Cohérent avec votre portfolio
- Responsive: S'adapte à tous les appareils

---

## 🎬 Comment ajouter vos propres vidéos

### **Option 1 : Vidéos en ligne (YouTube, Vimeo, etc.)**

```html
<!-- Avec contrôles HTML5 -->
<video controls width="100%" height="400">
  <source src="votre-video.mp4" type="video/mp4">
  <source src="votre-video.webm" type="video/webm">
  Votre navigateur ne supporte pas la vidéo.
</video>

<!-- Sans contrôles (autoplay) -->
<video autoplay muted loop width="100%">
  <source src="votre-video.mp4" type="video/mp4">
</video>
```

### **Option 2 : Intégrer dans votre galerie**

#### Étape 1 : Mettre à jour le fichier `elyad-marketing.html`

Ajoutez une nouvelle ligne dans votre tableau `items`:

```javascript
{s:'chemin/vers/votre-video.mp4', t:'Titre', d:'Description', cat:'categorie', type:'video'}
```

#### Étape 2 : Ajouter une carte vidéo HTML

```html
<div class="card categorie" onclick="openLb(12)">
  <video style="width:100%;height:400px;object-fit:cover;" muted playsinline>
    <source src="chemin/vers/video.mp4" type="video/mp4">
  </video>
  <div class="ov"></div>
  <div class="info">
    <div class="icat">Montage Vidéo</div>
    <div class="ititle">Titre de la vidéo</div>
    <div class="idesc">Description courte</div>
  </div>
</div>
```

### **Option 3 : Intégrer via iframe (YouTube, Vimeo)**

```html
<iframe width="100%" height="400" 
  src="https://www.youtube.com/embed/VIDEO_ID" 
  frameborder="0" allowfullscreen>
</iframe>
```

---

## 📁 Structure des fichiers recommandée

```
Portfolio/
├── index.html
├── elyad-marketing.html
├── videos-demo.html          ← Page vidéos (créée)
├── videos/                   ← Dossier pour vos vidéos
│   ├── campagne-yodi.mp4
│   ├── ice-i-bon.mp4
│   └── ... (autres vidéos)
└── [autres fichiers]
```

---

## 🎥 Formats vidéo recommandés

| Format | Extension | Avantages | Inconvénients |
|--------|-----------|-----------|---------------|
| **MP4** | .mp4 | Compatible universelle | Taille fichier grande |
| **WebM** | .webm | Optimisé web, petite taille | Chrome/Firefox seulement |
| **OGV** | .ogv | Format ouvert | Moins courant |

**Conseil**: Utilisez MP4 comme format principal et WebM comme seconde source.

---

## 🎯 Attributs vidéo HTML5 utiles

```html
<video 
  controls           <!-- Affiche les contrôles -->
  autoplay           <!-- Lance automatiquement -->
  muted              <!-- Son désactivé (nécessaire pour autoplay) -->
  loop               <!-- Boucle infinie -->
  playsinline        <!-- Lecture inline sur mobile -->
  poster="image.jpg" <!-- Image de prévisualisation -->
  style="width:100%; height:auto;"
>
  <source src="video.mp4" type="video/mp4">
  <source src="video.webm" type="video/webm">
  Votre navigateur ne supporte pas la vidéo HTML5.
</video>
```

---

## 🔧 Optimisation des vidéos

### **Réduire la taille des fichiers**

```bash
# Avec FFmpeg (ligne de commande)
ffmpeg -i video.mp4 -b:v 1000k -b:a 128k video-compressed.mp4
```

### **Créer plusieurs formats**
```bash
# MP4
ffmpeg -i video.mp4 -c:v libx264 -preset slow output.mp4

# WebM
ffmpeg -i video.mp4 -c:v libvpx -b:v 1000k output.webm

# OGV
ffmpeg -i video.mp4 -c:v libtheora output.ogv
```

---

## ✨ Améliorations possibles

1. **Ajouter des miniatures personnalisées**
   ```html
   <video poster="thumbnail.jpg">
     ...
   </video>
   ```

2. **Lazy loading pour performance**
   ```html
   <video loading="lazy">
     ...
   </video>
   ```

3. **Sous-titres**
   ```html
   <video>
     <source src="video.mp4" type="video/mp4">
     <track kind="subtitles" src="subtitles.vtt" srclang="fr">
   </video>
   ```

4. **Analytics (suivi des lectures)**
   Utiliser Google Analytics ou Vimeo pour tracker les vues

---

## 🚀 Maintenant, vous pouvez:

✅ Accéder à `videos-demo.html` depuis votre portfolio  
✅ Remplacer les vidéos de démonstration par les vôtres  
✅ Ajouter des vidéos à vos pages de projets  
✅ Utiliser les vidéos dans la lightbox de `elyad-marketing.html`  

---

## 📞 Besoin d'aide?

- Pour convertir vos vidéos → Utilisez [HandBrake](https://handbrake.fr/) ou [FFmpeg](https://ffmpeg.org/)
- Pour compresser → [TinyWow](https://tinywow.com/) ou [CloudConvert](https://cloudconvert.com/)
- Pour héberger → [Bunny CDN](https://bunnycdn.com/), [AWS S3](https://aws.amazon.com/fr/s3/), ou votre serveur

Bon montage! 🎬
