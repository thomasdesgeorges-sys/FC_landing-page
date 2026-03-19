# Design System — FoodChéri Landing Page

Ce document de référence rassemble l'ensemble des règles graphiques, règles de nommage et constantes CSS (Tailwind) utilisées dans la landing page B2B du Frigo Connecté FoodChéri (`hello.foodcheri.com`).

---

## 🎨 1. Couleurs (Brand Palette)

Les couleurs reflètent l'identité visuelle de la marque, à la fois premium (soft black) et chaleureuse / gourmande (terra, cream, beige).

| Nom | CSS / Tailwind Class | Code Hexadécimal | Usage Principal |
|---|---|---|---|
| **Noir (Brand Black)** | `.bg-brand-black` / `.text-brand-black` | `#2F2B2B` | Typographie principale, navbar, footer, background de la section Héros (masqué) et de la CTA mid-page. |
| **Blanc pur** | `.bg-white` / `.text-white` | `#ffffff` | Backgrounds de cartes (FAQ, Engagement), textes clairs (boutons, footer). |
| **Terracotta (Brand Terra)** | `.bg-brand-terra` / `.text-brand-terra` | `#7A3B00` | Accent principal : couleur d'action, boutons primaires CTA, accentuation sur les titres, liens au survol. |
| **Marron (Brand Brown)** | `.bg-brand-brown` | `#4A3B32` | Effet au survol (hover) des boutons primaires Terra. |
| **Crème (Brand Cream)** | `.bg-brand-cream` / `.border-brand-cream` | `#FAF5C7` | Background de certaines sections (Le Menu, Engagement), overlays, fond des icônes d'illustration. |
| **Beige (Brand Beige)** | `.bg-brand-beige` | `#F5F1EA` | Background alternatif pour les sections FAQ et encadrés images. |
| **Gris neutres (Gray)** | `.text-gray-400` / `.text-gray-500` / `.text-gray-600` | Tailwind UI Grays | Textes descriptifs (paragraphes), mentions légales dans le footer, sous-titres des menus. |

---

## 🖋 2. Typographie

### Polices de caractères
* **Titres (Heading)** : `LTC Globe Gothic` (Bold - Woff2 / OTF) — `font-heading`
* **Sous-titres & Interface** : `Roc Grotesk` (Regular / Medium - Woff2 / OTF) — `font-subheading` ou `font-roc-medium`
* **Corps de texte (Body)** : `Open Sans` (Regular / Bold - Woff2 / TTF) — `font-body`

### Échelle Typographique
La page a été construite de façon mathématique et symétrique sur les balises de titrailles :

| Élément | Classes Tailwind | Rendu Mobile (md) | Rendu Desktop (lg) |
|---|---|---|---|
| **H1 (Hero)** | `font-heading text-3xl md:text-5xl lg:text-6xl leading-[1.1]` | 3rem (48px) | 3.75rem (60px) |
| **H2 (Sections)** | `font-heading text-2xl md:text-3xl lg:text-4xl leading-tight` | 1.875rem (30px) | 2.25rem (36px) |
| **Surtitre (Overline)** | `font-subheading uppercase text-xs tracking-widest font-bold text-brand-terra` | 0.75rem (12px) | 0.75rem (12px) |
| **H3 (Cartes/Items)** | `font-subheading text-base font-bold` (ou text-xl pour certaines cartes) | 1rem (16px) | 1rem (16px) ou + |
| **Paragraphes** | `font-body text-sm md:text-base leading-relaxed text-gray-500 ou text-gray-600` | 0.875rem (14px) | 1rem (16px) |

*Toutes les balises H2 ont été spécifiquement harmonisées de bout en bout avec du `leading-tight` (1.25) pour offrir une régularité de proportions.*

---

## 📏 3. Layout et Grille (Spacing & Padding)

L'utilisation des paddings verticaux (sur l'axe Y) garantit le rythme régulier et respirant de la page en full-screen B2B.

### Structure Verticale des Sections
* **Padding standard de Section globale** : `py-24` (soit `96px` au-dessus et en-dessous de la zone du fond continu). Utilisé pour Comment ça marche, Le Menu, Avantages RH, Engagement, FAQ.
* **Padding spécifique d'interruption (CTA mid-page / Footer)** : `py-16` pour la bannière CTA et `py-12` pour le Footer final.
* **Conteneurs de section horizontaux** : `container mx-auto px-4 md:px-6` (largeur contrainte Tailwind automatique avec marges de sécurité latérales).
* **Grid typique des blocs texte + Image** : `grid lg:grid-cols-2 gap-16 lg:gap-20` pour aérer les colonnes gauches et droites sur Desktop.

### Espacement Interne (Marques de rythme)
* L'espacement entre un titre H2 et le paragraphe suivant est systématiquement `mb-6`.
* L'espacement après un en-tête de section avant le composant principal (la grille de cartes, l'accordéon FAQ) est fixé à `mb-12` ou `mb-14`.
* Les items et puces (<ul>) sont séparés par un espacement `space-y-4`.

---

## 🕹 4. Composants & Accessibilité

### Boutons CTA Primaires
Les boutons majeurs de la page et de fin de formulaire (ceux qui convertissent).
* **Structure** :  `bg-brand-terra text-white font-subheading font-bold tracking-widest uppercase` (ou équivalent text-xs).
* **Architecture d'Ombre** : `shadow-lg shadow-brand-terra/20`
* **Interaction Hover** : `hover:bg-brand-brown hover:-translate-y-1 transition-all duration-300`

### Composants Alternatifs (Bouton RH et Navbar)
* Les boutons secondaires et de Navbar utilisent le `bg-brand-black` avec un Hover vers `hover:bg-brand-terra`.

### Accents Visuels & UI
* **Coins Arrondis** : Les cartes complexes, images principales, sections isolées en blocs, et inputs ont un `rounded-2xl` classique pour adoucir le côté "Tech" de la landing page et le rendre plus naturel (organique). Les icônes individuelles de cartes ont un `rounded-xl`.
* **SVG Icons inline** : Tous les SVGs embarqués utilisent la classe formelle `w-4 h-4` (petits), `w-5 h-5` (moyens), ou `w-7 h-7` (illustratifs). Le `stroke-width` est aligné spécifiquement à `2` (sauf micro-icônes en `3`).

---

## 🛠 5. Optimisations Techniques Appliquées
* Assets Image WebP optimisés via Pillow en méthode 6 / 82% et SVG extraits pour réduire la charge.
* WOFF2 en Preload natif pour les headers cruciaux.
* Script JS compressé minifié externalisé (`assets/js/main.min.js`).
* CSS Extrait via compilateur JIT pour ne regrouper _qu'exactement_ les 269 classes invoquées dans la production (`assets/css/style.min.css`). Le fichier CSS comporte les polices, reset normalize Tailwind minimal et les media-queries précises, et ne pèse plus que 14 KB.
