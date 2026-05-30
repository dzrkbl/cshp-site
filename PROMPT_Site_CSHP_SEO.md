# PROMPT MAÎTRE — Construire le site web CSHP optimisé SEO

> **Comment l'utiliser :** copie-colle TOUT ce document dans une IA agentique (Claude Code, Cursor, Windsurf, Antigravity…) où le skill `ui-ux-pro-max` est installé. Exécute d'abord la section 1 (installation + génération du design system), puis laisse l'IA construire le site selon les sections 2 à 13. Réponds en français québécois.

---

## 0. RÔLE & OBJECTIF

Tu es un développeur web + spécialiste SEO local senior. Tu construis le **site web complet** du **Centre Sportif de Haute-Performance (CSHP)**, un club d'arts martiaux à Montréal. Objectif principal : **dominer le SEO local** sur les requêtes « karaté / judo / arts martiaux enfants » dans Rosemont–La Petite-Patrie et environs, et **convertir** les visiteurs vers un essai gratuit.

Priorités, dans l'ordre :
1. SEO technique + local (Core Web Vitals, données structurées, NAP, pages de quartier).
2. Conversion (CTA essai gratuit visible partout, friction minimale).
3. Design pro, rassurant pour les parents, énergique pour le sport.

---

## 1. SKILL À UTILISER — UI UX Pro Max

Installe et utilise le skill `nextlevelbuilder/ui-ux-pro-max`.

```bash
# Installation (CLI recommandée)
npm install -g uipro-cli
uipro init --ai claude        # ou cursor / windsurf / etc.
```

**ÉTAPE 1 OBLIGATOIRE — génère le design system AVANT de coder :**

```bash
python3 .claude/skills/ui-ux-pro-max/scripts/search.py \
  "martial arts dojo karate judo kids family local fitness club trust booking" \
  --design-system -p "CSHP" --persist
```

Puis crée un override pour les pages programmes :

```bash
python3 .claude/skills/ui-ux-pro-max/scripts/search.py \
  "martial arts dojo karate judo kids family local fitness club trust booking" \
  --design-system --persist -p "CSHP" --page "programme"
```

Le design system généré (`design-system/MASTER.md`) est la **source de vérité visuelle**. Respecte sa palette, sa typo, ses effets et sa checklist anti-patterns.

**Garde-fous design (à imposer au skill) :**
- Public = **parents 32-45 ans** + énergie sportive. Doit inspirer **confiance et sérieux**, pas « startup tech ».
- **Photographie en avant** (vrais enfants/ados au tatami). Le site actuel a des photos — réutilise-les, optimisées WebP.
- Palette dojo : **rouge / noir / blanc** + une teinte chaude d'accent, contraste élevé.
- **INTERDIT** : dégradés violet/rose « IA », emojis en guise d'icônes (utilise Lucide ou Heroicons SVG), animations agressives.

---

## 2. STACK TECHNIQUE

- **Astro + Tailwind CSS** (statique, ultra-rapide, SEO/Core Web Vitals optimaux).
- Composants en `.astro`, contenu éditorial en **Content Collections (Markdown)** pour blog + pages de quartier.
- Génération auto de `sitemap.xml` (`@astrojs/sitemap`) et `robots.txt`.
- Déploiement : **Cloudflare Pages** ou Netlify (HTTPS, CDN, gratuit).
- **Édition par le propriétaire** : horaire + blog en **Markdown (Content Collections)**, édités directement via **Git / Google AI Studio**. Pas de CMS lourd requis.
- Formulaire essai gratuit : envoi vers **Meta Lead Form** OU webhook (n8n/Brevo) + courriel à `centrehp@outlook.com`. Pas de backend lourd.

> **Si tu utilises Google AI Studio (Build mode) :** il sort par défaut des apps **React**. Pour le SEO, EXIGE du **pré-rendu statique (SSG)** — une SPA client-side tue le référencement (pas de HTML crawlable, LCP lent). Utilise alors **Next.js (App Router, output `export`/SSG)** au lieu d'Astro, pré-rends chaque page, puis pousse vers GitHub depuis AI Studio.

---

## 3. FAITS D'ENTREPRISE — SOURCE DE VÉRITÉ (NAP)

> ⚠️ Le NAP (Name-Address-Phone) doit être **identique au caractère près** partout : footer, schema, Google Business Profile. C'est critique pour le SEO local.

| Champ | Valeur |
|---|---|
| Nom | Centre Sportif de Haute-Performance (CSHP) |
| Adresse | 6498 rue Beaubien Est, Montréal, QC, H1M 1A9, Canada |
| Quartier | Rosemont–La Petite-Patrie |
| Téléphone | +1 514-747-5865 |
| Courriel | centrehp@outlook.com |
| Facebook | facebook.com/centrehp |
| Instagram | instagram.com/centresportif_hp |
| Fondé | 2019 (entreprise familiale) |
| Superficie | ~3 400 pi² |
| Géo | lat 45.5876306, lng -73.5604992 |
| Avis Google | 4,8 ★ (76 avis) |

**Horaire :**
- Lun–Ven : 16 h 30 – 21 h 00
- Samedi : 9 h 00 – 15 h 00
- Dimanche : 10 h 00 – 11 h 30

**Tarifs (à afficher sur `/tarifs/`) — identiques pour tous :**
- 3 mois : **250 $** (taxes incluses)
- 12 mois : **790 $** (taxes incluses)
- Rabais famille : **-10 %** dès le 2e enfant (et suivants)
- **Essai gratuit** = offre d'appel principale (CTA partout)

> **CORRIGER l'erreur du site actuel** : ne JAMAIS écrire « Saint-Léonard ». Le club est à **Rosemont** (Beaubien Est).

---

## 4. POSITIONNEMENT & USP

**USP #1 (à mettre en avant partout) :** Le SEUL club dans un rayon de 5 km dont le **head coach est actif aux sélections de Karaté Québec**. Filière compétitive karaté structurée + approche familiale.

**Voie double :**
- **Voie Loisir** (volume principal) : enfants 5-13 ans, parents du quartier, discipline/confiance/dépense d'énergie, sans contrat rigide.
- **Voie Compétition** (premium) : athlètes 8-15 ans sélectionnés, sélections provinciales, Karaté Québec, Sportdata, Complexe Claude-Robillard.

Affiliation : **Karaté Québec**. Mentionne la participation aux compétitions (ex. Open de Montréal) comme preuve sociale.

---

## 5. MOTS-CLÉS SEO CIBLES (par intention)

Intègre-les **naturellement** dans titles, H1/H2, contenu, alt d'images, URLs. Français Québécois.

**Marque / général**
- arts martiaux Montréal, arts martiaux enfants Montréal, club d'arts martiaux Rosemont

**Karaté**
- cours de karaté Montréal, karaté enfant Montréal, karaté Rosemont, karaté Beaubien, club de karaté compétitif Montréal, karaté Québec

**Judo**
- cours de judo Montréal, judo enfant Rosemont, club de judo Montréal

**Autres programmes**
- cardio kickboxing femmes Montréal, camp de jour arts martiaux Montréal, programme parascolaire arts martiaux, cours arts martiaux 4-8 ans (U8)

**Conversion / longue traîne**
- cours d'essai gratuit karaté Montréal, inscription karaté enfant Rosemont, arts martiaux près de moi

**Quartiers (pages dédiées)**
- karaté Rosemont, karaté La Petite-Patrie, arts martiaux Villeray, arts martiaux Mercier-Ouest

---

## 6. ARCHITECTURE DU SITE

URLs propres, en français, sans `/index.php/`. Chaque page a UN objectif SEO + UN H1 unique.

```
/                         Accueil (hub conversion + USP + aperçu programmes)
/karate/                  Programme Karaté (loisir + mention compétition)
/judo/                    Programme Judo
/u8-combine/              Programme U8 Combiné (4-8 ans)
/cardio-kickboxing/       Cardio Kickboxing femmes
/entrainement-prive/      Entraînement privé / personal training
/camp-de-jour/            Camp de jour (saisonnier)
/voie-competition/        ⭐ Filière compétitive (USP, E-E-A-T fort)
/horaire/                 Horaire des cours (tableau + schema)
/tarifs/                  Abonnements & tarifs + essai gratuit 19$
/a-propos/                À propos (histoire, mission, installations)
/equipe/                  Notre équipe / le coach (crédibilité Karaté Québec)
/contact/                 Contact + carte + formulaire
/essai-gratuit/           Landing dédiée conversion (formulaire)
/blog/                    Index blog (moteur de contenu SEO)
/blog/[article]/          Articles
# Pages de quartier (SEO local longue traîne) :
/arts-martiaux/rosemont/
/arts-martiaux/petite-patrie/
/arts-martiaux/villeray/
/arts-martiaux/mercier-ouest/
# Légal :
/politique-confidentialite/
/termes-conditions/
```

**Pages de quartier** : même structure, contenu RÉÉCRIT (pas dupliqué) — mentionne le quartier, la distance/accès depuis ce quartier, les programmes, un témoignage local, CTA. Évite le *thin/duplicate content* (Google pénalise).

---

## 7. SPÉCIFICATIONS SEO TECHNIQUES (OBLIGATOIRE)

### 7.1 Données structurées JSON-LD
Sur **chaque page**, injecte le schema approprié :

- **Global (toutes pages)** : `SportsActivityLocation` (sous-type de `LocalBusiness`) avec `name`, `address` (PostalAddress complet), `geo`, `telephone`, `openingHoursSpecification`, `priceRange`, `sameAs` (FB/IG), `url`, `image`, `areaServed` (les 4 quartiers).
- **Accueil + /a-propos/** : `Organization`.
- **Pages programmes** : `Course` (name, description, provider = l'organisation) + `Offer` (prix).
- **Toutes pages** : `BreadcrumbList`.
- **Pages avec FAQ** : `FAQPage`.
- **Si avis Google disponibles** : `AggregateRating` (ne jamais inventer de notes).

Exemple minimal (à compléter, une fois en global) :

```json
{
  "@context": "https://schema.org",
  "@type": "SportsActivityLocation",
  "name": "Centre Sportif de Haute-Performance",
  "image": "https://centresportifhp.com/og.jpg",
  "url": "https://centresportifhp.com",
  "telephone": "+15147475865",
  "email": "centrehp@outlook.com",
  "priceRange": "$$",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "6498 rue Beaubien Est",
    "addressLocality": "Montréal",
    "addressRegion": "QC",
    "postalCode": "H1M 1A9",
    "addressCountry": "CA"
  },
  "geo": { "@type": "GeoCoordinates", "latitude": 45.5876306, "longitude": -73.5604992 },
  "areaServed": ["Rosemont", "La Petite-Patrie", "Villeray", "Mercier-Ouest"],
  "sameAs": [
    "https://www.facebook.com/centrehp",
    "https://www.instagram.com/centresportif_hp"
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.8",
    "reviewCount": "76"
  },
  "openingHoursSpecification": [
    {"@type":"OpeningHoursSpecification","dayOfWeek":["Monday","Tuesday","Wednesday","Thursday","Friday"],"opens":"16:30","closes":"21:00"},
    {"@type":"OpeningHoursSpecification","dayOfWeek":"Saturday","opens":"09:00","closes":"15:00"},
    {"@type":"OpeningHoursSpecification","dayOfWeek":"Sunday","opens":"10:00","closes":"11:30"}
  ]
}
```

### 7.2 Balises meta & langue
- `<html lang="fr-CA">` sur toutes les pages.
- `og:locale = fr_CA` (corriger l'erreur `en_US` du site actuel).
- **Title** unique par page, ≤ 60 caractères, mot-clé en premier. Format : `Mot-clé principal | CSHP Montréal`.
- **Meta description** unique par page, 140-160 car., avec CTA (« Essai gratuit »).
- `<link rel="canonical">` auto sur chaque page.
- Open Graph + Twitter Card complets (image 1200×630).

### 7.3 Templates title/description (exemples)
| Page | Title | Meta description |
|---|---|---|
| Accueil | Arts martiaux à Montréal – Karaté & Judo \| CSHP | Club familial d'arts martiaux à Rosemont. Karaté, judo, U8. Coach actif aux sélections Karaté Québec. Réserve ton essai gratuit. |
| Karaté | Cours de karaté à Montréal (Rosemont) \| CSHP | Cours de karaté enfants et ados à Beaubien Est. Discipline, confiance, filière compétitive Karaté Québec. Essai gratuit. |
| Judo | Cours de judo à Montréal – Rosemont \| CSHP | Initie ton enfant au judo dans un club familial de Rosemont. Encadrement de haut niveau. Réserve un essai gratuit. |

### 7.4 Performance / Core Web Vitals (cibles)
- LCP < 2,5 s · CLS < 0,1 · INP < 200 ms.
- Images : **WebP/AVIF**, `width`/`height` explicites, `loading="lazy"` (sauf hero), `<picture>` responsive.
- **Alt text descriptif + mot-clé** sur chaque image (ex. « enfant en cours de karaté à Rosemont »).
- Fonts en `font-display: swap`, préchargées. CSS critique inline. Zéro JS bloquant.
- Pas de carrousel lourd ni de plugin superflu.

### 7.5 Indexation
- `sitemap.xml` auto + soumis à Google Search Console.
- `robots.txt` propre (autorise tout sauf pages légales si voulu).
- **Redirections 301** depuis les anciennes URLs WordPress (`/index.php/judo/` → `/judo/`, `/home-2/` → `/entrainement-prive/`, etc.) pour ne pas perdre le jus SEO.
- Maillage interne : chaque page programme lie vers `/horaire/`, `/tarifs/`, `/essai-gratuit/` et 2-3 pages de quartier pertinentes.

---

## 8. CONTENU & TON

- **Français québécois**, chaleureux mais pro. Parle aux **parents** (Persona « parent débordé » : écrans, manque de discipline/temps, recherche un co-éducateur, proximité, pas de contrat rigide).
- Chaque page programme : H1 mot-clé + intro (problème du parent → solution), bénéfices (puces), à qui ça s'adresse + âges, déroulé d'un cours, encadré USP coach, CTA essai gratuit, mini-FAQ (3-5 Q/R = schema FAQPage).
- **E-E-A-T** sur `/equipe/` et `/voie-competition/** : crédentials du coach, affiliation Karaté Québec, résultats/compétitions, photos réelles. C'est ce qui te démarque.
- Réutilise/réécris le contenu fort du site actuel (mission, approche pédagogique) en l'enrichissant de mots-clés et en supprimant les incohérences.

---

## 9. CONVERSION

- **CTA « Essai gratuit » sticky** (header + bouton flottant mobile) sur toutes les pages.
- Offre d'appel mise en avant : **essai gratuit**. Forfaits : **250 $/3 mois** ou **790 $/12 mois** (taxes incl.), **-10 % dès le 2e enfant**.
- Formulaire **court** (friction minimale) : Prénom, Téléphone, Âge de l'enfant, Programme souhaité. 4 champs max.
- Clic-to-call sur mobile (`tel:+15147475865`).
- Bloc « pourquoi nous » avec l'USP + preuve sociale (avis, logos Karaté Québec).
- Message de remerciement clair après soumission.

---

## 10. ACCESSIBILITÉ (WCAG AA)

- Contraste texte ≥ 4,5:1. Focus visible clavier. `prefers-reduced-motion` respecté.
- `cursor-pointer` sur tout cliquable. Hover 150-300 ms.
- Responsive testé à **375 / 768 / 1024 / 1440 px**. Mobile-first.
- Icônes en SVG (Lucide/Heroicons), jamais d'emoji-icône.

---

## 11. CHECKLIST DE PRÉ-LIVRAISON

- [ ] Design system généré par le skill et respecté (palette/typo/anti-patterns).
- [ ] Toutes les pages de la section 6 créées, H1 uniques, NAP identique partout.
- [ ] JSON-LD valide sur chaque page (tester via Rich Results Test).
- [ ] `lang="fr-CA"`, `og:locale=fr_CA`, titles/metas uniques.
- [ ] Aucune mention « Saint-Léonard ». Adresse = Beaubien Est / Rosemont.
- [ ] Images WebP + alt avec mots-clés + dimensions explicites.
- [ ] Lighthouse : Performance ≥ 90, SEO = 100, Accessibilité ≥ 95.
- [ ] sitemap.xml + robots.txt présents.
- [ ] Redirections 301 des anciennes URLs documentées.
- [ ] Formulaire essai gratuit fonctionnel (test faux lead).
- [ ] Responsive 375/768/1024/1440 OK.

---

## 12. LIVRABLES ATTENDUS

1. Code source complet du site (Astro + Tailwind), prêt à déployer.
2. `design-system/MASTER.md` (du skill).
3. Fichier `redirections.md` listant les 301 ancienne → nouvelle URL.
4. `README.md` : comment éditer le contenu, ajouter un article de blog, déployer.
5. Liste des actions SEO post-lancement (Google Business Profile, Search Console, soumission sitemap).

---

## 13. ORDRE D'EXÉCUTION

1. Générer le design system (section 1).
2. Scaffolder le projet Astro + Tailwind + sitemap.
3. Construire les composants partagés (header sticky avec CTA, footer NAP, schema global).
4. Construire l'accueil, puis les pages programmes, puis quartiers, puis blog, puis légal.
5. Injecter tous les JSON-LD + metas.
6. Optimiser images + perf.
7. Passer la checklist section 11.
8. Livrer + README + redirections.

**Commence maintenant par la section 1.**
