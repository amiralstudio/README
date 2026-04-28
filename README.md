<div align="center">

# Amiral Studio

**Product Studio à Yaoundé, Cameroun.**
SaaS, applications mobiles, plateformes e-commerce et intégrations IA pour l'Afrique et l'international.

[🌍 amiral-studio.com](https://amiral-studio.com) · [📨 hello@amiral-studio.com](mailto:hello@amiral-studio.com) · [💼 LinkedIn](https://linkedin.com/company/amiralstudio) · [📷 Instagram](https://instagram.com/amiralstudio)

[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js&logoColor=white)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-3.4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![Supabase](https://img.shields.io/badge/Supabase-CMS-3ECF8E?logo=supabase&logoColor=white)](https://supabase.com)
[![Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-black?logo=vercel&logoColor=white)](https://vercel.com)
[![License](https://img.shields.io/badge/License-Proprietary-lightgrey)](#licence)

</div>

---

## ✨ À propos

Ce dépôt contient le code source du site vitrine officiel d'Amiral Studio. Il sert à présenter le studio, son expertise (SaaS, mobile, IA, e-commerce, design system), son portfolio de produits, ses témoignages clients, et héberge également un blog éditorial.

Le site est **mobile-first**, optimisé pour le SEO local camerounais, et pensé pour une lecture rapide même sur connexion 3G.

## 🧱 Stack technique

| Domaine | Technologie |
|---|---|
| Framework | [Next.js 14](https://nextjs.org) (App Router) |
| Langage | [TypeScript 5](https://www.typescriptlang.org) (`strict`) |
| Styling | [Tailwind CSS 3.4](https://tailwindcss.com) + variables CSS pour le theming |
| Animations | [GSAP](https://gsap.com) (ScrollTrigger) + [Lenis](https://lenis.studiofreight.com) (smooth scroll) |
| Theming | [next-themes](https://github.com/pacocoursey/next-themes) (light / dark) |
| Icônes | [react-icons](https://react-icons.github.io/react-icons) (Feather) |
| CMS / DB | [Supabase](https://supabase.com) (articles, produits, témoignages, contacts, newsletter) |
| Analytics | [Firebase Analytics](https://firebase.google.com/docs/analytics) + tracking custom Supabase |
| Polices | [Inter](https://rsms.me/inter/) (sans) + [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) (display) — `next/font/google` |
| Hébergement | [Vercel](https://vercel.com) — domaine `amiral-studio.com` |

## 🚀 Démarrage rapide

```bash
# 1. Cloner
git clone https://github.com/amiralstudio/amiral-studio-web.git
cd amiral-studio-web

# 2. Installer les dépendances
npm install

# 3. Configurer l'environnement
cp .env.example .env.local
# → remplir les variables Firebase + Supabase (voir section Variables)

# 4. Lancer en développement
npm run dev
# http://localhost:3000
```

## 📜 Scripts disponibles

| Commande | Description |
|---|---|
| `npm run dev` | Serveur de développement avec hot reload sur `localhost:3000` |
| `npm run build` | Build de production (Next.js avec ISR) |
| `npm start` | Servir le build de production en local |
| `npm run lint` | Lint ESLint (config `next/core-web-vitals` + `next/typescript`) |

## 🔑 Variables d'environnement

Toutes les clés sont publiques (préfixe `NEXT_PUBLIC_*`). La sécurité repose sur les *Row Level Security* policies de Supabase et les *Security Rules* de Firebase, **pas** sur le secret de ces clés.

```env
# Firebase (Hosting + Analytics) — projet "amiral-studio-web"
NEXT_PUBLIC_FIREBASE_API_KEY=
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=
NEXT_PUBLIC_FIREBASE_PROJECT_ID=
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=
NEXT_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=
NEXT_PUBLIC_FIREBASE_APP_ID=
NEXT_PUBLIC_FIREBASE_MEASUREMENT_ID=

# Supabase (CMS — partagé avec Amiral-studio-admin)
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
```

Voir [`.env.example`](./.env.example) pour le template complet.

## 🗂️ Structure du projet

```
amiral-studio-web/
├── public/                    # assets statiques (logos, favicon, og-image)
├── src/
│   ├── app/                   # routes Next.js (App Router)
│   │   ├── page.tsx           # home
│   │   ├── studio/            # à propos
│   │   ├── services/          # expertise
│   │   ├── products/          # portfolio
│   │   ├── blog/              # /blog + /blog/[slug] (ISR)
│   │   ├── testimonials/      # avis clients
│   │   ├── contact/           # formulaire de contact
│   │   ├── privacy/           # politique de confidentialité
│   │   ├── terms/             # conditions d'utilisation
│   │   ├── layout.tsx         # root layout (metadata, JSON-LD, providers)
│   │   ├── sitemap.ts         # sitemap.xml dynamique
│   │   ├── robots.ts          # robots.txt
│   │   ├── manifest.ts        # PWA manifest
│   │   ├── error.tsx          # error boundary global
│   │   └── not-found.tsx      # page 404 custom
│   ├── components/
│   │   ├── home/              # sections de la home (Hero, Stats, Process, FAQ…)
│   │   ├── Navbar.tsx
│   │   ├── Footer.tsx
│   │   ├── Logo.tsx
│   │   ├── Preloader.tsx
│   │   ├── Cursor.tsx
│   │   ├── SmoothScroll.tsx
│   │   ├── ThemeToggle.tsx
│   │   ├── Reveal.tsx         # composant d'apparition scroll-triggered
│   │   ├── MagneticLink.tsx   # boutons magnétiques
│   │   ├── ContactForm.tsx
│   │   ├── ArticleBody.tsx    # rendu markdown léger
│   │   ├── ArticleCover.tsx   # covers SVG génératives
│   │   ├── JsonLd.tsx         # helpers schema.org
│   │   └── …
│   ├── data/                  # fallbacks statiques (articles, produits, services, valeurs)
│   └── lib/                   # supabase, firebase, analytics, seo, format, cn
├── next.config.mjs            # config Next + headers de sécurité + cache
├── tailwind.config.ts         # design tokens (couleurs, fonts, animations)
├── tsconfig.json              # alias `@/*` → `src/*`
└── postcss.config.mjs
```

## 🎨 Design system

### Palette

| Token | Light | Dark |
|---|---|---|
| `--background` | `#E0E1DD` (mist) | `#0D1B2A` (ink) |
| `--foreground` | `#0D1B2A` | `#E0E1DD` |
| `--surface` | `#FFFFFF` | `#121F30` |
| `--accent` | `#415A77` (steel) | `#E0E1DD` |
| `--muted` | `rgba(13,27,42,.6)` | `rgba(224,225,221,.6)` |
| `--border` | `rgba(13,27,42,.08)` | `rgba(224,225,221,.1)` |

### Typographie

- **Display** : Space Grotesk — titres, navigation, accents
- **Sans** : Inter — corps de texte, UI
- Échelle responsive via `clamp()` (`text-hero`, `text-display`)

### Animations

- Easing principal : `cubic-bezier(.22, 1, .36, 1)`
- Reveal : 900 ms — Sections : 700 ms — Micro : 300 ms
- Smooth scroll **désactivé** sur mobile et `prefers-reduced-motion`

## 🔍 SEO & Performance

Le site est optimisé pour ranker sur la requête **"Amiral Studio"** et ses variantes :

- ✅ **Metadata complètes** par page (title, description, OG, Twitter Card, canonical)
- ✅ **Schema.org JSON-LD** : `Organization`, `WebSite`, `ProfessionalService`, `BlogPosting`, `BreadcrumbList`, `FAQPage`, `AboutPage`, `ContactPage`, `AggregateRating`, `SoftwareApplication`
- ✅ **Sitemap dynamique** (`/sitemap.xml`) — articles + routes statiques
- ✅ **Robots.txt** allow-list pour Googlebot, Bingbot, GPTBot
- ✅ **PWA Manifest** (`/manifest.webmanifest`)
- ✅ **Headers de sécurité** — HSTS, X-Frame-Options, Referrer-Policy, Permissions-Policy
- ✅ **Cache long** (1 an, immutable) sur les assets `_next/static` et images
- ✅ **Images** servies en AVIF/WebP via `next/image`
- ✅ **ISR** sur la home et le blog (`revalidate = 60`)
- ✅ **Smooth scroll**, animations GPU, lazy loading

> 📋 Voir [`SEO-CHECKLIST.md`](./SEO-CHECKLIST.md) (à venir) pour la roadmap off-page (Google Business Profile, backlinks, Wikidata).

## ♿ Accessibilité

- `lang="fr"` sur le `<html>`
- Skip-link "Aller au contenu" en début de page
- Aria-label sur le H1, les boutons icon-only et les liens externes
- Respect de `prefers-reduced-motion` (preloader, smooth scroll, Reveal)
- Contraste AA en light et dark mode

## 🧪 Qualité

```bash
npm run lint           # ESLint
npx tsc --noEmit       # type-check sans build
```

## 📦 Déploiement

Le site est déployé sur **Vercel** avec auto-deploy depuis la branche `main`.

| Branche | Environnement | URL |
|---|---|---|
| `main` | Production | https://amiral-studio.com |
| `*` | Preview | URL Vercel temporaire automatique |

La redirection `www.amiral-studio.com` → `amiral-studio.com` est gérée côté Vercel (domain settings — apex en primary).

## 🗺️ Roadmap

- [ ] Routes `/products/[slug]/` indexables (au lieu des anchors `#slug`)
- [ ] OG image PNG haute résolution avec branding (1200×630)
- [ ] Page Wikidata pour disambiguation Knowledge Graph
- [ ] Newsletter Resend / Brevo (au lieu du simple insert Supabase)
- [ ] i18n EN (Amiral sert aussi un public anglophone)

## 🤝 Contribuer

Ce dépôt est privé. Pour toute proposition (typo, bug, suggestion d'amélioration), ouvrir une issue ou contacter directement l'équipe à [hello@amiral-studio.com](mailto:hello@amiral-studio.com).

## 📄 Licence

© 2025 Amiral Studio. Tous droits réservés.

Le code source de ce site est **propriétaire** et n'est pas publié sous licence open-source. Il n'est pas autorisé de réutiliser, copier, modifier ou redistribuer tout ou partie de ce dépôt sans autorisation écrite préalable.

---

<div align="center">

**Amiral Studio**
Reflecting Excellence · Yaoundé, Cameroun 🇨🇲

</div>
