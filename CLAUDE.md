# Aapiti Studio — Charte graphique

## ⚠️ Logo — règle absolue

Le logo Aapiti est une **typographie personnalisée sur mesure**. Il ne doit **jamais** être reproduit en texte avec une autre police (pas Cormorant Garamond, pas Jost, pas aucune Google Font).

Utiliser **toujours** les fichiers image dans `/brand/` :

| Fichier | Usage | Format |
|---|---|---|
| `brand/logo-black.png` | Mode clair (fond ivory/blanc) | 700×220 RGBA, fond transparent |
| `brand/logo-gold.png` | Mode sombre (fond noir/sombre) | 700×220 RGBA, fond transparent |
| `brand/logo-ivory-sq.png` | Social media, icône carré — mode clair | 1000×1000 RGB |
| `brand/logo-gold-sq.png` | Social media, icône carré — mode sombre | 1000×1000 RGB |

### Patron CSS pour chaque document HTML

```html
<!-- Dans le header -->
<img src="[base64 ou URL de logo-black.png]" alt="Aapiti" class="logo-black" height="30">
<img src="[base64 ou URL de logo-gold.png]"  alt="Aapiti" class="logo-gold"  height="30">
```

```css
.logo-black { display: block; }
.logo-gold  { display: none; }

@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) .logo-black { display: none; }
  :root:not([data-theme="light"]) .logo-gold  { display: block; }
}
:root[data-theme="dark"] .logo-black { display: none; }
:root[data-theme="dark"] .logo-gold  { display: block; }
```

Pour embarquer en base64 dans un document autonome :
```bash
python3 -c "
import base64
with open('brand/logo-black.png','rb') as f: print('data:image/png;base64,'+base64.b64encode(f.read()).decode())
"
```

---

## Typographie

| Rôle | Police | Poids | Notes |
|---|---|---|---|
| Display / Titres | **Cormorant Garamond** | 300, 400 (italic disponible) | Titres de section, citations, grands numéros |
| Body / UI | **Jost** | 200, 300, 400, 500 | Corps de texte, labels, navigation |

```html
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500&family=Jost:wght@200;300;400;500&display=swap" rel="stylesheet">
```

---

## Palette de couleurs

```css
:root {
  /* Fond document */
  --iv: #FAF7F0;   /* ivory — fond principal mode clair */
  --cr: #F2EDE0;   /* cream — surfaces, cards */
  --sd: #E4D8BF;   /* sand — bordures */

  /* Accents */
  --go: #C8A348;   /* gold — accent primaire */
  --gl: #D4B96A;   /* gold light — dégradés */
  --br: #8B6914;   /* brown — labels, légendes */

  /* Texte */
  --mi: #4A3F32;   /* muted ink — corps de texte clair */
  --dk: #1C1814;   /* dark — titres mode clair */

  /* Mode sombre */
  --bg-dark: #16130F;
  --surface-dark: #1F1B14;
  --border-dark: #302818;
  --text-dark: #D4C9A8;
  --muted-dark: #7A6F5A;
}
```

---

## Patterns récurrents

### Bande or en haut de page
```html
<div style="height:3px; background: linear-gradient(90deg, #C8A348, #D4B96A 50%, #C8A348)"></div>
```

### Header sticky
- Hauteur : 52px
- Background : `var(--bg)` avec `border-bottom: 1px solid var(--border)`
- Logo à gauche (image), badge "Document confidentiel" à droite

### Card station / note
```css
border: 1px solid var(--border);
border-left: 3px solid var(--accent);
background: var(--surface);
border-radius: 0 3px 3px 0;
```

### Citations
```css
/* Filets or à gauche et à droite, texte italic Cormorant Garamond */
padding: 28px 60px;
position: relative;
text-align: center;
/* ::before et ::after : width 44px, height 1px, background: var(--accent) */
```

---

## Structure type d'un document

1. Bande or (3px)
2. Header sticky avec logo + badge
3. Cover : eyebrow → grand titre Cormorant → sous-titre italic → filet or → intro italic → note card
4. Sections numérotées 01 / 02 / 03...
5. Footer : `AAPITI® — Scénographie culinaire` | `Document confidentiel`

---

## Notes importantes

- Le ® fait partie du logo image — ne pas l'ajouter séparément quand on utilise le fichier PNG
- Mode sombre : utiliser `logo-gold.png` (fond transparent, texte doré)
- Mode clair : utiliser `logo-black.png` (fond transparent, texte noir)
- Ne jamais écrire "AAPITI®" ou "Aapiti" comme texte dans les headers de documents — toujours utiliser l'image
