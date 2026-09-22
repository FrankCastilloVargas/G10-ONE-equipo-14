# CommunityLab

Proyecto del equipo **G10 · Hackaton ONE · Equipo 14**. Desafío: Motor Inteligente de
Transformación y Distribución para Comunidades Digitales.

## Introducción

CommunityLab transforma interacciones de comunidades digitales en oportunidades y borradores
de contenido. El MVP procesa archivos JSON o CSV, analiza sentimiento, temas y relevancia
mediante IA, genera contenido para LinkedIn y FAQ, permite revisión humana y almacena el
resultado final en OCI Object Storage.

## Objetivos

- Procesar y deduplicar interacciones de la comunidad.
- Detectar temas, sentimiento, relevancia y oportunidades de contenido.
- Generar borradores de LinkedIn y FAQ basados en evidencia.
- Permitir editar, aprobar o rechazar los activos generados.
- Mantener trazabilidad y guardar los paquetes aprobados en OCI.

## Arquitectura

Flujo principal:

```
JSON/CSV -> FastAPI -> Pydantic -> PostgreSQL -> LangGraph -> LLM Gateway
-> reglas de negocio -> Streamlit -> aprobación -> OCI Object Storage
```

Componentes principales:

- **FastAPI y Pydantic** — API, contratos y validación.
- **LangGraph y LLM Gateway** — análisis y generación estructurada con proveedor de IA intercambiable.
- **PostgreSQL** — estado, trazabilidad y auditoría.
- **Streamlit** — carga, visualización y curaduría humana.
- **OCI Object Storage** — almacenamiento de paquetes, manifiestos y activos aprobados.
- **Git y GitHub** — versionado del código: [G10-ONE-equipo-14](https://github.com/No-Country-simulation/G10-ONE-equipo-14).
- **Jira** — gestión del proyecto, backlog y tickets: [Proyecto CommunityLab en Jira](https://g10-latam-equipo14.atlassian.net/).

## Estructura del repositorio

```
backend/     # API FastAPI, lógica de negocio, LangGraph, persistencia en PostgreSQL
frontend/    # Interfaz Streamlit para curaduría (revisar, editar, aprobar/rechazar)
docs/        # Documentación técnica y de producto (arquitectura, contratos, ADRs)
tests/       # Tests unitarios y de integración
```

## Setup

1. Clonar el [repositorio](https://github.com/No-Country-simulation/G10-ONE-equipo-14).
2. Instalar Docker y Docker Compose.
3. Configurar `.env` con credenciales del LLM, PostgreSQL y OCI (ver `.env.example`).
4. Levantar API, base de datos y dashboard con Docker Compose.
5. Crear o configurar el bucket de OCI Object Storage.
6. Ejecutar las pruebas y cargar el dataset JSON o CSV de demostración.
7. Gestionar tareas, responsables y avances desde [Jira](https://g10-latam-equipo14.atlassian.net/).

## Estado actual

🚧 En construcción — Sprint 1 (E1: base técnica y contratos).

## Convenciones de contribución

Branching, PRs y Definition of Done se documentan en `docs/CONTRIBUTING.md` (E1-S06).

Convención de ramas mientras tanto:
- `main` — protegida, siempre estable/demo-able.
- `feature/<clave-jira>-descripcion-corta` — una por Story/Task.
- `fix/<clave-jira>-descripcion` — para bugfixes.