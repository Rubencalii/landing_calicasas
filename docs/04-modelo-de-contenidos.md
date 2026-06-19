# 04 · Modelo de contenidos

El cambio clave del rediseño: **dejar de tener carteles en imagen y pasar a contenido
estructurado** (datos). Cada cartel actual se modela como una entidad con campos.

## Entidades

### `Evento`

| Campo | Tipo | Obligatorio | Notas |
|---|---|:--:|---|
| `id` | string | ✅ | slug único |
| `titulo` | string | ✅ | |
| `fechaInicio` | date/datetime | ✅ | ISO 8601 |
| `fechaFin` | date/datetime | ❌ | para eventos de varios días |
| `hora` | string | ❌ | ej. "22:00" |
| `lugar` | string | ❌ | ej. "Parque Mariana Pineda" |
| `descripcion` | text (markdown) | ❌ | |
| `imagen` | media | ❌ | con `alt` obligatorio si existe |
| `categoria` | enum | ❌ | cultura, deporte, fiestas, infantil… |
| `enlace` | url | ❌ | inscripciones / más info |
| `estado` | enum | ✅ (derivado) | próximo / en curso / pasado |

**Ejemplos reales (de la web actual):**
- Karting Calicasas — 11/07 — Karting Grana (Purchil) — 20:00 — inscripciones limitadas
- Cine de Verano "La Sirenita" — 04/07 — Parque Mariana Pineda — 22:00
- Biblioteca en la calle — lunes 07–28/07 — Plaza de la Constitución — 20:00–21:30

### `Anuncio` / `Aviso`

| Campo | Tipo | Obligatorio | Notas |
|---|---|:--:|---|
| `id` | string | ✅ | |
| `titulo` | string | ✅ | |
| `fecha` | date | ✅ | |
| `cuerpo` | text (markdown) | ❌ | |
| `urgente` | boolean | ❌ | si `true` → aparece en la banda de avisos del hero |
| `vigenciaHasta` | date | ❌ | para auto-ocultar avisos caducados |
| `enlace` | url | ❌ | puede apuntar a un servicio interno |

**Ejemplos reales:** nuevos horarios de autobuses → enlaza a *Transporte y Movilidad*;
recogida de enseres; punto de información a la persona consumidora; ofibus CaixaBank;
prevención Virus del Nilo.

### `Servicio`

| Campo | Tipo | Obligatorio | Notas |
|---|---|:--:|---|
| `id` | string | ✅ | slug |
| `nombre` | string | ✅ | |
| `categoria` | enum | ✅ | salud, cultura, deporte, administración… |
| `descripcion` | text | ✅ | |
| `direccion` | string | ❌ | |
| `telefono` | string | ❌ | |
| `email` | string | ❌ | |
| `horario` | structured | ❌ | días + franjas |
| `icono` | string | ✅ | nombre del icono |
| `enlaceExterno` | url | ❌ | si el servicio vive fuera |

### `PaginaInformativa` (Article)

Para Saluda del Alcalde, Historia, Patrimonio, Tradiciones, etc.

| Campo | Tipo | Obligatorio |
|---|---|:--:|
| `slug` | string | ✅ |
| `titulo` | string | ✅ |
| `cuerpo` | markdown | ✅ |
| `imagenes` | media[] | ❌ |
| `descargas` | file[] | ❌ |
| `actualizado` | date | ❌ |

### `Contacto` (singleton institucional)

```yaml
nombre: Ayuntamiento de Calicasas
direccion: Plaza de la Constitución, 1
cp: "18290"
localidad: Calicasas
provincia: Granada
telefono: "+34 958 40 96 01"
email: ayto.calicasas@gmail.com
redes:
  facebook: https://www.facebook.com/p/Ayuntamiento-de-Calicasas-100066442969952/
  instagram: https://www.instagram.com/ayuntamientodecalicasas/
  whatsapp: https://whatsapp.com/channel/0029VaOe3y6LNSa3gY36hy24
externos:
  sedeElectronica: https://calicasas.sedelectronica.es/
```

## Dónde viven los datos (fases)

1. **Prototipo / portfolio:** ficheros locales en `src/data/*.js` o `*.json`.
   Suficiente para demostrar el diseño y la estructura.
2. **Producción con edición por personal no técnico:** un **CMS headless**
   (Strapi, Directus o similar) o Markdown + panel. Decisión en doc 05.

> Regla de oro de accesibilidad: **ninguna información esencial solo en una imagen**.
> Toda imagen lleva `alt`; los carteles se transcriben a campos de la entidad.
