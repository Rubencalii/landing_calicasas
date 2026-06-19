# 01 · Brief y objetivos

## Contexto

El Ayuntamiento de Calicasas (Granada, 18290) dispone de un portal construido sobre
**IONOS MyWebsite**, un constructor web básico. El contenido dominante son **carteles
en imagen** (eventos y anuncios), sin estructura ni texto alternativo, lo que genera
problemas de accesibilidad, mantenimiento y posicionamiento.

## Problemas detectados en la web actual

1. **Orientada a "navegar", no a "hacer".** El ciudadano entra a resolver una tarea
   (un trámite, una cita, ver un bando) pero la home prioriza un carrusel decorativo.
2. **Información atrapada en imágenes.** Los eventos y anuncios son carteles JPG/PNG:
   no son buscables, ni accesibles, ni reutilizables.
3. **Accesibilidad insuficiente.** En una administración pública el cumplimiento del
   Real Decreto 1112/2018 y la norma UNE-EN 301549 es **obligatorio por ley**.
4. **Diseño desactualizado y poco jerarquizado.** Carrusel pesado, jerarquía visual
   débil, experiencia móvil mejorable.
5. **Dependencia de un constructor cerrado.** Difícil de evolucionar y mantener.

## Objetivos del rediseño

| # | Objetivo | Cómo se mide |
|---|----------|--------------|
| O1 | Que el ciudadano resuelva tareas frecuentes en 1-2 clics | Accesos directos visibles en la home |
| O2 | Convertir el contenido en datos estructurados | Eventos/anuncios como entidades (no imágenes) |
| O3 | Cumplir accesibilidad WCAG 2.1 AA | Auditoría y declaración de accesibilidad |
| O4 | Experiencia mobile-first | Diseño responsive, validado en móvil real |
| O5 | Imagen institucional moderna y de confianza | Sistema de diseño coherente (doc 03) |
| O6 | Facilitar el mantenimiento | Contenido editable sin tocar el diseño |

## Público objetivo

- **Vecinos del municipio** (rango de edad amplio, incluida población mayor → legibilidad y simplicidad).
- **Personas que buscan un trámite concreto** (sede electrónica, citas, pagos).
- **Visitantes / turismo local** (historia, patrimonio, fiestas).
- **Empresas y proveedores** (perfil del contratante, contratación pública).

## Tareas prioritarias del usuario ("top tasks")

1. Acceder a la **Sede Electrónica** / realizar un trámite.
2. Consultar **bandos, anuncios y avisos** urgentes (cortes de agua, plazos…).
3. Ver la **agenda de eventos** del municipio.
4. Encontrar un **servicio** (centro de salud, biblioteca, polideportivo…) con horarios y contacto.
5. **Contactar** con el ayuntamiento.

## Principios de diseño

- **Primero la tarea, después la estética.** El diseño sirve a la utilidad.
- **Texto antes que imagen.** La información va en texto estructurado; la imagen acompaña.
- **Accesible por defecto**, no como añadido final.
- **Cercano pero institucional.** Confianza administrativa con calidez de pueblo.
- **Sobrio y duradero.** Evitar modas que envejezcan mal en una web pública.

## Fuera de alcance (por ahora)

- Multidioma (la web es solo en español; se deja la puerta abierta en la arquitectura).
- Migración de los servicios externos de administración electrónica (Sede, Transparencia,
  Perfil del Contratante) — se **enlazan**, no se reconstruyen.

## Decisiones tomadas (19/06/2026)

- **Encargo real** → el cumplimiento legal (accesibilidad RD 1112/2018 + RGPD) es obligatorio.
- **Mismo dominio** (`calicasas.es`) → solo habrá que reapuntar el DNS al nuevo hosting al lanzar.
- **Sin backend propio.** Los eventos viven en un **Google Calendar** del ayuntamiento; la web lo
  muestra y permite al vecino **suscribirse** a su propio calendario. El "panel de administración"
  es, simplemente, editar ese Google Calendar (ver doc 07).
- **Validación con el alcalde mediante maqueta visual** (Figma / Canva) **antes** de construir.

## Decisiones aún por confirmar

- ¿Hosting final? (estático en Vercel/Netlify, o servidores asociados al dominio actual).
- ¿Se conserva el correo `ayto.calicasas@gmail.com` o se pasa a un buzón de dominio institucional?
