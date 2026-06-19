# 03 · Sistema de diseño

Dirección visual: **institucional moderno con calidez andaluza**. Sobrio y fiable como
corresponde a una administración, con un acento cálido que evoque el pueblo (Granada).

## Principios visuales

- Mucho espacio en blanco y jerarquía clara.
- Color con propósito (no decorativo): el acento marca acciones.
- Contraste siempre ≥ 4.5:1 para texto (WCAG AA).
- Componentes simples y reutilizables.

## Paleta de color (design tokens)

```css
:root {
  /* Marca — verde pino institucional */
  --color-primary-900: #143a2c;
  --color-primary-700: #1f5641;   /* principal */
  --color-primary-500: #2f7a5e;
  --color-primary-100: #dfeee8;
  --color-primary-50:  #eef6f2;

  /* Acento — terracota / arcilla andaluza (acciones, destacados) */
  --color-accent-700: #a8462a;
  --color-accent-500: #c85a3a;    /* principal */
  --color-accent-100: #f6e3da;

  /* Neutros */
  --color-ink:        #1c2420;   /* texto principal */
  --color-muted:      #5a655f;   /* texto secundario */
  --color-line:       #e2e0d8;   /* bordes/separadores */
  --color-surface:    #ffffff;   /* tarjetas */
  --color-bg:         #faf7f2;   /* fondo cálido (cream) */

  /* Estados / semánticos */
  --color-info:    #1f5641;
  --color-success: #2f7a5e;
  --color-warning: #b8860b;
  --color-danger:  #b3261e;      /* avisos urgentes */
}
```

**Comprobación de contraste (texto sobre fondo):**
- Tinta `#1c2420` sobre cream `#faf7f2` → ✅ AAA
- Blanco sobre primary-700 `#1f5641` → ✅ AA
- Blanco sobre accent-500 `#c85a3a` → ✅ AA (usar para botones, no para texto pequeño largo)

## Tipografía

- **Títulos:** una serif humanista con carácter institucional (ej. *Lora* o *Source Serif 4*).
- **Cuerpo e interfaz:** una sans legible y neutra (ej. *Inter* o *Source Sans 3*).
- Cargar vía `@fontsource` (autohospedadas, mejor para RGPD que Google Fonts CDN).

```css
:root {
  --font-serif: 'Lora', Georgia, 'Times New Roman', serif;
  --font-sans:  'Inter', system-ui, -apple-system, 'Segoe UI', sans-serif;
}
```

### Escala tipográfica (modular, base 16px / 1.25)

| Token | Tamaño | Uso |
|---|---|---|
| `--fs-xs`  | 0.8rem  | etiquetas, pies |
| `--fs-sm`  | 0.9rem  | texto secundario |
| `--fs-base`| 1rem    | cuerpo |
| `--fs-md`  | 1.25rem | entradillas |
| `--fs-lg`  | 1.6rem  | títulos de sección |
| `--fs-xl`  | 2rem    | títulos de página |
| `--fs-2xl` | 2.6rem  | título del hero |

Interlineado: 1.6 en cuerpo, 1.2 en títulos.

## Espaciado (escala base 4px)

```
--space-1: 4px    --space-4: 16px   --space-8: 48px
--space-2: 8px    --space-5: 24px   --space-10: 64px
--space-3: 12px   --space-6: 32px   --space-12: 96px
```

## Radios y sombras

```css
--radius-sm: 6px;  --radius-md: 12px;  --radius-lg: 20px;  --radius-full: 999px;
--shadow-sm: 0 1px 2px rgba(20,58,44,.06);
--shadow-md: 0 4px 16px rgba(20,58,44,.08);
--shadow-lg: 0 12px 32px rgba(20,58,44,.12);
```

## Breakpoints (mobile-first)

```
sm: 480px    md: 768px    lg: 1024px    xl: 1280px
```
Contenedor máximo de contenido: **1200px**, con padding lateral fluido.

## Inventario de componentes

| Componente | Descripción | Notas de accesibilidad |
|---|---|---|
| `Header` | Logo, nav principal, utilidades, buscador | Nav con `<nav aria-label>`, menú móvil con foco gestionado |
| `SkipLink` | "Saltar al contenido" | Visible al tabular, primer elemento del DOM |
| `AlertBanner` | Aviso urgente (condicional) | `role="alert"` solo si es crítico; color danger |
| `Hero` | Título + buscador + accesos directos | Buscador con `<label>` asociado |
| `QuickAccess` | Rejilla de accesos a top tasks | Enlaces, no divs; icono + texto |
| `EventCard` | Tarjeta de evento | `<time datetime>`; título es enlace |
| `AnnouncementCard` | Tarjeta de anuncio | Fecha estructurada + enlace "leer más" |
| `ServiceCard` | Tarjeta de servicio con icono | Icono decorativo `aria-hidden` |
| `SectionHeading` | Título de sección + "ver todos" | Jerarquía de encabezados correcta |
| `Breadcrumbs` | Migas de pan | `<nav aria-label="Migas">` + `aria-current` |
| `Footer` | Contacto, legal, redes, mapa del sitio | Enlaces a accesibilidad, RGPD, transparencia |
| `Button` | Primario / secundario / texto | Foco visible, área táctil ≥ 44px |
| `Tag`/`Badge` | Etiqueta de categoría/fecha | Suficiente contraste |

## Iconografía

- Set de iconos de **trazo** coherente (ej. Lucide). Decorativos → `aria-hidden="true"`.
- Tamaño base 24px; nunca transmitir información solo por icono o color.

## Estados de interacción (obligatorios)

- **:hover** y **:focus-visible** diferenciados; foco con anillo de 2px bien contrastado.
- `prefers-reduced-motion`: desactivar animaciones no esenciales.
- Áreas táctiles mínimas de **44×44px**.
