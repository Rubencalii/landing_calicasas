# 05 · Plan técnico y fases

## Stack propuesto

| Capa | Elección | Por qué |
|---|---|---|
| Build | **Vite** | Rápido, estándar moderno, cero configuración pesada |
| UI | **React 18** | Componentes reutilizables, ecosistema amplio |
| Routing | **React Router 6** | Multipágina SPA con rutas anidadas por sección |
| Estilos | **CSS con custom properties** (tokens del doc 03) | Sin dependencias, control total, accesible |
| Iconos | **Lucide React** | Set de trazo coherente y ligero |
| Tipografía | **@fontsource** (autohospedada) | Mejor para RGPD que el CDN de Google Fonts |
| Datos | `src/data/*.js` (fase 1) → CMS headless (fase 2) | Empezar simple, escalar después |
| Hosting | Estático (Vercel / Netlify / hosting del consistorio) | Barato, rápido, seguro |

> Alternativa a valorar si se prioriza SEO/SSR desde el día 1: **Next.js**. Para una web
> municipal mayormente informativa, Vite + React + prerender es suficiente y más simple.

## Estructura de carpetas prevista

```
src/
├─ main.jsx
├─ App.jsx                 # rutas
├─ index.css              # tokens + base + utilidades
├─ data/
│  ├─ site.js             # contacto, nav, enlaces externos
│  ├─ eventos.js
│  ├─ anuncios.js
│  └─ servicios.js
├─ components/
│  ├─ layout/  (Header, Footer, SkipLink, Layout, Breadcrumbs)
│  ├─ home/    (Hero, QuickAccess, AlertBanner)
│  └─ ui/      (Button, EventCard, AnnouncementCard, ServiceCard, Tag, SectionHeading)
└─ pages/
   ├─ Home.jsx
   ├─ Ayuntamiento.jsx
   ├─ Pueblo.jsx
   ├─ Servicios.jsx
   ├─ ServicioDetalle.jsx
   ├─ Agenda.jsx
   ├─ Contacto.jsx
   └─ NotFound.jsx
```

## Fases de ejecución

### Fase 0 — Documentación ✅ (en curso)
Brief, IA, sistema de diseño, modelo de contenidos, plan, accesibilidad.

### Fase 1 — Esqueleto y sistema de diseño
- Scaffold Vite + React + Router (ya hay `package.json` y `vite.config.js`).
- `index.css` con todos los tokens del doc 03.
- Layout base: Header, Footer, SkipLink, contenedor, rutas vacías.

### Fase 2 — Home
- Hero funcional + buscador + accesos directos.
- AlertBanner condicional.
- Agenda (EventCard), Anuncios (AnnouncementCard), Servicios destacados.
- Datos de ejemplo en `src/data/`.

### Fase 3 — Páginas internas
- Plantillas SectionIndex, Article, ServiceDetail, Agenda completa, Contacto, 404.
- Migas de pan y navegación coherente.

### Fase 4 — Accesibilidad y pulido
- Auditoría WCAG (ver doc 06), foco, teclado, contraste, lectores de pantalla.
- Rendimiento (imágenes optimizadas, lazy-loading, Lighthouse).
- SEO básico (títulos, metas, datos estructurados, sitemap.xml).

### Fase 5 — Contenidos reales y despliegue
- Carga de contenidos reales (transcribir carteles a entidades).
- Decisión e integración de CMS si hace falta edición no técnica.
- Redirecciones 301 desde URLs antiguas. Despliegue + declaración de accesibilidad.

## Comandos

```bash
npm install      # instalar dependencias
npm run dev      # desarrollo (http://localhost:5173)
npm run build    # build de producción
npm run preview  # previsualizar el build
```

## Decisiones técnicas abiertas

- **¿CMS sí o no?** Depende de quién mantenga los contenidos (ver doc 01 y 04).
- **¿SPA o SSR/SSG?** SPA con prerender para empezar; migrar a Next.js si el SEO lo exige.
- **Hosting final:** ¿servidores del consistorio, IONOS, o un estático en Vercel/Netlify?
