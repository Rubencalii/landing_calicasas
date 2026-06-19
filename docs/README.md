# Documentación — Rediseño web Ayuntamiento de Calicasas

Este directorio contiene toda la documentación del proyecto de rediseño del portal
oficial del Ayuntamiento de Calicasas (Granada).

## Índice de documentos

| # | Documento | Para qué sirve |
|---|-----------|----------------|
| 00 | [especificaciones.md](./especificaciones.md) | Extracción del contenido y estructura de la web **actual** (punto de partida) |
| 01 | [01-brief-y-objetivos.md](./01-brief-y-objetivos.md) | Por qué se rediseña, objetivos, público y criterios de éxito |
| 02 | [02-arquitectura-de-informacion.md](./02-arquitectura-de-informacion.md) | Mapa del sitio nuevo, navegación y jerarquía de la home |
| 03 | [03-sistema-de-diseno.md](./03-sistema-de-diseno.md) | Tokens de diseño: color, tipografía, espaciado, componentes |
| 04 | [04-modelo-de-contenidos.md](./04-modelo-de-contenidos.md) | Entidades de contenido (eventos, anuncios, servicios…) |
| 05 | [05-plan-tecnico-y-fases.md](./05-plan-tecnico-y-fases.md) | Stack, estructura de carpetas y fases de ejecución |
| 06 | [06-accesibilidad-y-cumplimiento.md](./06-accesibilidad-y-cumplimiento.md) | Requisitos legales: accesibilidad, RGPD, transparencia |
| 07 | [07-calendario-y-eventos.md](./07-calendario-y-eventos.md) | Integración de eventos con Google Calendar (sin backend propio) |

## Estado del proyecto

- **Fase actual:** Documentación cerrada → siguiente paso: **maqueta visual para el alcalde** (Figma/Canva)
- **Tipo:** Encargo real · mismo dominio (`calicasas.es`) · **sin backend propio**
- **Eventos:** vía Google Calendar (ver doc 07)
- **Stack previsto:** Vite + React + React Router (ver doc 05)
- **Plataforma actual a sustituir:** IONOS MyWebsite

## Cómo usar esta documentación

1. Lee el **brief (01)** para entender objetivos y alcance.
2. La **arquitectura (02)** y el **modelo de contenidos (04)** definen *qué* se construye.
3. El **sistema de diseño (03)** define *cómo se ve*.
4. El **plan técnico (05)** define *cómo se construye* y en qué orden.
5. La **accesibilidad (06)** es transversal y de cumplimiento **obligatorio** por ser administración pública.
