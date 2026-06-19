# 02 · Arquitectura de información

Se **conserva la estructura de 4 secciones** de la web actual (es correcta y conocida
por los vecinos), pero se reorganiza la home en torno a **tareas + actualidad**.

## Navegación principal

```
Inicio (Actualidad)
├─ Tu Ayuntamiento
│  ├─ Saluda del Alcalde
│  ├─ Equipo de Gobierno
│  ├─ Corporación Municipal
│  ├─ Bandos y Ordenanzas
│  ├─ Sede Electrónica            ↗ externo (calicasas.sedelectronica.es)
│  ├─ Portal de Transparencia     ↗ externo
│  ├─ Perfil del Contratante      ↗ externo
│  ├─ Ventanilla Virtual          ↗ externo
│  └─ Correo Corporativo          ↗ externo
├─ Conoce tu Pueblo
│  ├─ Historia
│  ├─ Patrimonio
│  ├─ Localización
│  ├─ Callejero
│  ├─ Asociaciones y Colectivos
│  ├─ Lugares de Interés
│  ├─ Tradiciones y Fiestas
│  └─ Galería de Imágenes
├─ Servicios
│  ├─ Cursos y Talleres
│  ├─ Centro de Salud
│  ├─ Biblioteca
│  ├─ Centro Vuela Guadalinfo
│  ├─ Polideportivo
│  ├─ Cementerio
│  ├─ Transporte y Movilidad
│  ├─ Juzgado de Paz
│  ├─ Área de Juventud
│  ├─ Área de Igualdad
│  └─ Teléfonos Locales de Interés
└─ Contacto
```

Enlaces de utilidad (persistentes en cabecera/pie): **Sede Electrónica**,
**Buzón de Sugerencias**, **Mapa del sitio**, redes sociales (Facebook, Instagram, WhatsApp).

## Convención de URLs (slugs sin tildes)

La web actual usa tildes en las URLs (`localización`, `corporación-municipal`), lo que da
problemas de compatibilidad. Nueva convención: **minúsculas, sin tildes, con guiones**.

| Sección | Antes | Después |
|---|---|---|
| Localización | `/conoce-tu-pueblo/localización/` | `/conoce-tu-pueblo/localizacion` |
| Corporación | `/tu-ayuntamiento/corporación-municipal/` | `/tu-ayuntamiento/corporacion-municipal` |
| Área de Juventud | `/servicios/área-de-juventud/` | `/servicios/area-de-juventud` |

> Mantener **redirecciones 301** desde las URLs antiguas para no perder enlaces ni SEO.

## Estructura de la home (orden vertical)

1. **Cabecera** — logo + nav + accesos de utilidad (sede, buzón) + buscador.
2. **Banda de avisos urgentes** (opcional, condicional) — bandos/avisos críticos
   (cortes de agua, plazos). Solo aparece si hay aviso activo. Alto contraste.
3. **Hero funcional** — título + buscador grande ("¿Qué necesitas?") + 4-6 accesos
   directos a las top tasks (Sede electrónica, Bandos, Agenda, Trámites, Empleo, Contacto).
4. **Agenda de eventos** — próximos eventos en **tarjetas** (no carrusel de carteles).
5. **Anuncios y avisos** — anuncios varios en tarjetas con título, fecha y enlace.
6. **Servicios destacados** — acceso rápido a los servicios más usados con iconos.
7. **Conoce el pueblo** — bloque visual hacia historia/patrimonio/turismo.
8. **Pie institucional** — contacto, transparencia, accesibilidad, RGPD, redes, mapa del sitio.

## Plantillas de página (page templates)

| Plantilla | Usada en | Componentes clave |
|---|---|---|
| `Home` | Inicio | Hero, accesos, agenda, anuncios, servicios |
| `SectionIndex` | Tu Ayuntamiento, Conoce tu Pueblo, Servicios | Hero de sección + grid de subpáginas |
| `Article` | Saluda, Historia, Patrimonio… | Título, cuerpo de texto, imágenes, descargas |
| `ServiceDetail` | Cada servicio | Descripción, horario, dirección, teléfono, mapa |
| `EventList` | Agenda completa | Filtros por fecha/tipo + tarjetas de evento |
| `Contact` | Contacto | Datos + formulario + mapa |
| `Gallery` | Galería de imágenes | Cuadrícula de fotos con lightbox accesible |
| `NotFound` | 404 | Mensaje + buscador + enlaces útiles |

## Migración: a dónde va cada contenido actual

- Carrusel de cabecera → **Hero funcional** (deja de ser decorativo).
- "Anuncios y Eventos de Actualidad" (7 imágenes) → entidades **Anuncio** + **Evento**.
- "Agenda de Eventos Recientes" → entidad **Evento** (lista filtrable).
- "Eventos Anteriores" → archivo de la lista de eventos (filtro "pasados").
- Botones-imagen (Sede, Buzón, redes) → **accesos directos** del hero + utilidades de cabecera/pie.
