# 06 · Accesibilidad y cumplimiento legal

> Una web de administración pública **está obligada por ley** a cumplir accesibilidad.
> Esto no es opcional ni un "extra".

## Marco legal aplicable (España)

- **Real Decreto 1112/2018**, sobre accesibilidad de los sitios web y aplicaciones del
  sector público → exige nivel de conformidad **WCAG 2.1 AA** (norma **UNE-EN 301549**).
- **Declaración de accesibilidad** obligatoria y publicada (con mecanismo de contacto/queja).
- **Reglamento (UE) 2016/679 (RGPD)** + **LOPDGDD** → privacidad, cookies, formularios.
- **Ley 19/2013 de transparencia** → enlace al Portal de Transparencia.

## Checklist WCAG 2.1 AA (operativa)

### Perceptible
- [ ] Texto alternativo en toda imagen informativa; `alt=""` en decorativas.
- [ ] **Nada esencial transmitido solo por imagen** (transcribir carteles a texto).
- [ ] Contraste de texto ≥ 4.5:1 (≥ 3:1 en texto grande). Ver tokens del doc 03.
- [ ] No usar **solo el color** para transmitir información (añadir icono/texto).
- [ ] Contenido reflowable hasta 320px sin scroll horizontal; zoom 200% sin pérdida.
- [ ] Vídeos con subtítulos; audio con transcripción (si los hubiera).

### Operable
- [ ] Toda la funcionalidad accesible **por teclado**, sin trampas de foco.
- [ ] **Foco visible** y con buen contraste (`:focus-visible`).
- [ ] Enlace **"Saltar al contenido"** al inicio del DOM.
- [ ] Áreas táctiles ≥ 44×44px.
- [ ] Respetar `prefers-reduced-motion`; sin parpadeos > 3/seg.
- [ ] Menú móvil: foco gestionado, cierre con `Esc`.

### Comprensible
- [ ] `lang="es"` en `<html>`.
- [ ] Jerarquía de encabezados correcta (un solo `<h1>` por página, sin saltos).
- [ ] Formularios con `<label>` asociado, errores claros y `aria-describedby`.
- [ ] Lenguaje claro y sencillo (público amplio, incluida población mayor).

### Robusto
- [ ] HTML semántico (`<nav>`, `<main>`, `<header>`, `<footer>`, `<article>`).
- [ ] ARIA solo cuando aporta (no sustituye al HTML semántico).
- [ ] Estados comunicados (`aria-current`, `aria-expanded`, `aria-live` en avisos).

## Herramientas de validación

- **axe DevTools** / **WAVE** — auditoría automática (detecta ~30-40%).
- **Lighthouse** (accesibilidad + rendimiento + SEO).
- **Navegación solo con teclado** (Tab/Shift+Tab/Enter/Esc).
- **Lector de pantalla**: NVDA (Windows) o VoiceOver (Mac).
- **Contraste**: comprobador de la WebAIM.

> La validación automática **no basta**: hay que probar con teclado y lector de pantalla.

## RGPD / privacidad

- [ ] Página de **Política de privacidad** y **Aviso legal**.
- [ ] **Cookies**: si solo hay técnicas/esenciales, no requiere banner de consentimiento;
      cualquier analítica/terceros sí lo requiere.
- [ ] **Fuentes autohospedadas** (`@fontsource`) en lugar del CDN de Google Fonts
      (evita transferir IPs a terceros).
- [ ] Formularios: base de legitimación, finalidad y enlace a la política.
- [ ] Mapas/embeds de terceros: cargar bajo consentimiento o usar alternativa.

## Entregables de cumplimiento

1. **Declaración de accesibilidad** publicada (estado de conformidad + contacto).
2. **Aviso legal** + **Política de privacidad** + **Política de cookies**.
3. Enlaces en el pie a: Accesibilidad, Privacidad, Aviso legal, Transparencia, Mapa del sitio.
