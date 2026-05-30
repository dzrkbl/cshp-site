# AGENTS.md — Règles persistantes du projet CSHP

> Ce fichier est lu automatiquement par l'agent (Antigravity) à chaque session. Il est la **loi du projet**. Respecte-le en tout temps.

## OBJECTIF
Construire le **site web complet du Centre Sportif de Haute-Performance (CSHP)**, club d'arts martiaux à Montréal, **optimisé pour le SEO local** (Rosemont–La Petite-Patrie) et la **conversion** vers un essai gratuit.

Priorités, dans l'ordre : 1) SEO technique + local · 2) Conversion · 3) Design pro et rassurant.

## STACK
- **Astro + Tailwind CSS** (statique, SSG). Pré-rendu de TOUTES les pages (jamais de SPA client-side).
- Contenu éditorial (blog, horaire) en **Content Collections Markdown** (éditable via Git).
- `@astrojs/sitemap` pour `sitemap.xml` + `robots.txt`.
- Déploiement : **Cloudflare Pages** (auto-deploy sur push GitHub).

## SOURCES DE VÉRITÉ À CONSULTER AVANT DE CODER
1. **Design** : `design-system/cshp/MASTER.md` (couleurs, typo, pattern, effets). Pour une page donnée, vérifie d'abord `design-system/cshp/pages/[page].md` ; si présent, il prime.
2. **SEO + schema** : utilise le skill `skills/claude-seo` pour TOUT le SEO (balises, JSON-LD, E-E-A-T, SEO local, GBP, cohérence NAP).
3. **Qualité de code** : suis les principes de `skills/karpathy` (pas de sur-ingénierie, code lisible, pas d'hallucination d'API).
4. **Brief complet** : le prompt maître `PROMPT_Site_CSHP_SEO.md` (architecture, mots-clés, contenu).

## FAITS ENTREPRISE — NAP IDENTIQUE PARTOUT (ne jamais dévier)
- Nom : Centre Sportif de Haute-Performance (CSHP)
- Adresse : 6498 rue Beaubien Est, Montréal, QC, H1M 1A9, Canada
- Quartier : Rosemont–La Petite-Patrie
- Téléphone : +1 514-747-5865
- Courriel : centrehp@outlook.com
- Géo : lat 45.5876306, lng -73.5604992
- Avis : 4,8 ★ (76 avis) → `AggregateRating` dans le schema
- Facebook : facebook.com/centrehp · Instagram : instagram.com/centresportif_hp
- Fondé en 2019, entreprise familiale, ~3 400 pi²
- Horaire : Lun–Ven 16h30–21h00 · Sam 9h00–15h00 · Dim 10h00–11h30

## TARIFS (page /tarifs/) — identiques pour tous
- 3 mois : 250 $ (taxes incluses)
- 12 mois : 790 $ (taxes incluses)
- Rabais famille : -10 % dès le 2e enfant
- Essai gratuit = offre d'appel principale (CTA partout)

## USP (mettre en avant partout)
Seul club dans 5 km dont le **head coach est actif aux sélections de Karaté Québec**. Filière compétitive structurée + approche familiale.

## RÈGLES STRICTES
- Langue : **français québécois**. `<html lang="fr-CA">`, `og:locale=fr_CA`.
- **Pas de Taekwondo** (programme retiré). Programmes : Karaté, Judo, U8 Combiné, Cardio Kickboxing (femmes), Entraînement privé, Camp de jour.
- **Ne jamais écrire « Saint-Léonard »** : le club est à Rosemont (Beaubien Est).
- Icônes en SVG (Lucide/Heroicons), jamais d'emoji-icône.
- Chaque page : H1 unique, title ≤ 60 car., meta description unique 140-160 car., canonical, JSON-LD approprié.
- **NE PAS toucher au site WordPress en ligne** (centresportifhp.com reste live jusqu'au cutover).
- Avant chaque PR : passe la checklist du prompt maître (section 11) + Lighthouse (SEO 100, Perf ≥ 90, A11y ≥ 95).

## WORKFLOW
1. Scaffolder Astro + Tailwind + sitemap.
2. Composants partagés : header sticky avec CTA « Essai gratuit », footer NAP, schema global injecté sur toutes les pages.
3. Construire : accueil → pages programmes → pages de quartier → blog → légal.
4. Tester le rendu via le navigateur intégré (mobile 375px + desktop).
5. Commit + push GitHub. Cloudflare Pages déploie.
