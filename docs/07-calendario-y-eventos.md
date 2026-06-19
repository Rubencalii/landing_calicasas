# 07 · Calendario de eventos (integración Google Calendar)

## Decisión de arquitectura

**Sin backend propio.** Los eventos del pueblo se gestionan en un **Google Calendar**
del ayuntamiento. La web lo consume y lo muestra; el vecino puede suscribirse al suyo.

Ventajas para un ayuntamiento pequeño:
- El "panel de administración" ya existe: **es Google Calendar** (web + app móvil), que el
  personal ya sabe usar. Sin formación, sin login que asegurar, sin BD que mantener.
- Sincronización nativa: quien se suscribe recibe los eventos y sus cambios en su móvil.
- Coste cero y máxima fiabilidad.

## Cómo funciona

```
[Personal del ayuntamiento]
        │  añade/edita eventos
        ▼
[Google Calendar "Eventos de Calicasas"]  ← fuente única de la verdad
        │
        ├──(API / iCal)──►  [Web calicasas.es]  muestra agenda + calendario bonito
        │
        └──(suscripción)─►  [Móvil del vecino]   "Añadir a mi calendario"
```

## Para los vecinos: enlazarse al calendario

La web ofrecerá botones de **suscripción** (no solo "ver"):
- **Añadir a Google Calendar:** `https://calendar.google.com/calendar/u/0/r?cid=<ID_CALENDARIO>`
- **Suscribirse (iCal/Apple/Outlook):** enlace `webcal://` al `.ics` público del calendario.
- **Añadir un evento suelto:** enlace "Add to Calendar" por evento (Google/ICS).

Así el vecino se suscribe una vez y recibe **todos los eventos futuros** automáticamente.

## Para la web: mostrar los eventos

Dos formas, de menos a más trabajo:

1. **Embed oficial de Google Calendar** (iframe).
   - Cero código de integración. Rápido.
   - ⚠️ Estético y de accesibilidad limitados (es el widget de Google, poco "de marca")
     y carga recursos de Google (implicación de cookies/RGPD → bajo consentimiento).

2. **Lectura por API / feed iCal y render propio** (recomendado).
   - Se lee el calendario público (Google Calendar API con API key, o el feed `.ics`).
   - Se pintan los eventos con **nuestros** componentes (`EventCard`, agenda, mini-calendario).
   - ✅ De marca, accesible, sin cargar el widget de Google en la página.
   - Los campos disponibles de cada evento de Google: `summary` (título), `start`/`end`,
     `location` (lugar), `description` (descripción). Categoría/cartel se pueden codificar
     en la descripción (p. ej. una línea `Categoría: cultura`) o como convención de color.

> Mapeo con el modelo de contenidos (doc 04): el evento de Google cubre los campos
> esenciales de la entidad `Evento`. Si en el futuro se necesitan campos ricos (cartel,
> inscripciones, categorías formales), se podría subir a la Opción B (admin + BD), pero
> **no es necesario ahora**.

## Pasos de implementación (cuando toque construir)

1. Crear el calendario **"Eventos de Calicasas"** en la cuenta Google del ayuntamiento.
2. Hacerlo **público** (solo lectura para el mundo; edición para el personal).
3. Obtener el **ID del calendario** y la **API key** (o la URL del feed `.ics`).
4. En la web: función que lee los eventos próximos y los renderiza en la agenda/home.
5. Añadir los botones de **suscripción** y "añadir a mi calendario" por evento.
6. RGPD: si se usa el iframe de Google, cargarlo bajo consentimiento; con la opción de
   render propio vía API/iCal, no se incrustan recursos de Google en la página.

## Nota para la maqueta del alcalde

En la **maqueta visual** (Figma/Canva) el calendario se representa como un **mini-calendario
mensual + lista de próximos eventos** con el diseño de marca. No necesita estar conectado a
Google todavía: es una imagen que comunica la idea ("así se verá, y se sincroniza con tu móvil").
