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

## Important Notes
- GitHub URL placeholder: https://github.com/Carlosmarroquin20 (update with real repo URLs)
- No i18n implemented (was requested but out of scope)
- Stats card: 2-col mobile, 4-col desktop (grid-cols-2 md:grid-cols-4)
- Header nav: scrollable on mobile (overflow-x-auto), text-[11px] on xs screens
