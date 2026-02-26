# Portfolio Dev — Project Memory

## Project Overview
- **Type**: Astro portfolio website
- **Owner**: Emanuel Marroquín — .NET Developer + Security Informatics student
- **Profile**: Female .NET developer, banking experience, Maestría en Seguridad Informática (UMG, in progress)
- **Target**: International recruiters, fintech, digital banking

## Tech Stack
- Astro (framework), Tailwind CSS, TypeScript
- Dark/light mode via ThemeToggle.astro
- View Transitions (astro:transitions)
- Font: Onest Variable

## Key File Paths
- `src/pages/index.astro` — main page, all section wiring
- `src/components/Hero.astro` — hero with profile badges (.NET, Security, Cloud)
- `src/components/Skills.astro` — 6-category badge-based skills grid (no progress bars)
- `src/components/Projects.astro` — 8 projects total; supports no-image placeholder + badge label
- `src/components/EnterpriseValue.astro` — "Lo que aporto" section (new, 6 value props)
- `src/components/Certifications.astro` — supports no-image entries with gradient placeholder
- `src/components/Experience.astro` — work timeline
- `src/layouts/Layout.astro` — html shell, viewport fixed to include initial-scale=1

## Sections Order (index.astro)
1. Hero → Stats → Experiencia → Proyectos → Skills → Valor (EnterpriseValue) → Sobre mí → Certificaciones → CTA

## Nav Items (Header.astro)
Experiencia | Proyectos | Skills | Mi Valor | Sobre mí | Contacto

## Design Patterns
- Skills: badge/tag grid, 6 categories with color themes (violet=.NET, blue=frontend, cyan=cloud, red=security, green=DB, amber=methodology)
- Projects: `image || placeholderGradient` pattern — academic projects use gradient + SVG icon
- Project badges: amber pill with 🎓 emoji for academic projects
- All tags in Projects.astro support `icon: null` (renders text-only tag)
- Certifications: `image || (icon + placeholderBg)` pattern

## i18n System (CSS class-based, no route duplication)
- Anti-flash inline script in Layout.astro `<head>` sets `html.lang-en` class from localStorage before paint
- Global CSS: `.i18n-en{display:none}` + `html.lang-en .i18n-es{display:none}` etc.
- Inline spans: `<span class="i18n-es">texto</span><span class="i18n-en">text</span>`
- Block elements: `<p class="i18n-es-block">...</p><p class="i18n-en-block">...</p>`
- `window.toggleLang()` defined in Layout.astro, called by `LanguageToggle.astro`
- Language stored in `localStorage['portfolio-lang']` ('es' or 'en')
- CV download: `data-cv-es="/CV-Emanuel-Marroquin.pdf"` + `data-cv-en="/CV-Emanuel-Marroquin-EN.pdf"` on `<a>` tag — toggled by `toggleLang()`
- **TODO**: Add `/public/CV-Emanuel-Marroquin-EN.pdf` for English CV

## Project Tabs (Projects.astro)
- Each project has `categories: string[]` (e.g. ["seguridad", "devops"])
- Tab buttons have `.project-tab-btn` class + `data-filter` attribute
- Project cards have `.project-card` class + `data-categories` attribute
- Script in Projects.astro initializes tabs on `astro:page-load`
- Categories: todos | seguridad | web | dotnet | ia | devops

## Important Notes
- GitHub URL placeholder: https://github.com/Carlosmarroquin20 (update with real repo URLs)
- Stats card: 2-col mobile, 4-col desktop (grid-cols-2 md:grid-cols-4)
- Header nav: scrollable on mobile (no-scrollbar + overflow-x-auto), text-[10px] on xs screens
- LanguageToggle placed in Header.astro between nav links and ThemeToggle
