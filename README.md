# Rediseño web · Ayuntamiento de Calicasas

Proyecto de rediseño del portal oficial del **Excmo. Ayuntamiento de Calicasas**
(Vega de Granada). Web informativa moderna, accesible y orientada a tareas, con la
agenda de eventos integrada con **Google Calendar** (sin backend propio).

## Estructura del repositorio

```
.
├── docs/                 # Documentación del rediseño (brief, IA, diseño, etc.)
│   ├── README.md         # Índice de la documentación
│   ├── especificaciones.md
│   └── 01..07-*.md
├── maqueta/              # Maquetas visuales para presentación (HTML/CSS)
│   ├── index.html        # Galería comparadora de propuestas
│   ├── v0-clasica.html   # Institucional sobria
│   ├── v1-aurora.html    # Premium, glassmorphism + animaciones
│   ├── v2-inmersivo-3d.html  # Hero 3D con Three.js
│   ├── v3-editorial.html # Minimalista, serif
│   ├── v4-calido.html    # Cálido andaluz, orgánico
│   ├── v5-heraldica.html # Colores oficiales del escudo de Calicasas
│   └── assets/           # Escudo oficial y recursos
├── package.json          # Proyecto Vite + React (fase de desarrollo)
└── vite.config.js
```

## Propuestas de diseño

Abre `maqueta/index.html` en el navegador para comparar las 6 direcciones visuales.
La **V5 (Heráldica)** usa los esmaltes oficiales del escudo municipal.

## Stack previsto

Vite · React · React Router. Eventos vía Google Calendar. Ver `docs/05` y `docs/07`.

## Estado

Fase de **definición y validación visual** (maquetas para presentación al alcalde).
