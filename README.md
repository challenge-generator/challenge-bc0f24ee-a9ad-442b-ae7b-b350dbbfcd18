# Maestría en Versionamiento con Git

Como desarrollador senior en un equipo de arquitectura SOA y sistemas distribuidos, debes dominar técnicas avanzadas de versionamiento con Git. Esto incluye diferenciar entre repositorio local y remoto, resolver conflictos, comprender conceptos fundamentales de control de versiones, manejar ramas temporales (features, hotfix, release) y ramas inmutables en enfoques modernos de despliegue (GitFlow, trunk-based development). Tu tarea es asegurar que el código se versiona correctamente, se resuelven conflictos de manera eficiente y se siguen las mejores prácticas de despliegue.

## Informacion General

| Campo | Valor |
|-------|-------|
| **Tema** | Técnicas de versionamiento |
| **Nivel** | senior-l2 |
| **Tipo** | mixed |
| **Tiempo estimado** | 10 horas |

## Fases del Reto

### Fase 0: Configuración del Proyecto

**Objetivo:** Obtener el proyecto base funcional enviando el Código Base a un asistente de IA, que lo analizará, corregirá errores y generará un ZIP listo para usar.

**Tiempo estimado:** 15-30 minutos

**Instrucciones:**

- Asegúrate de tener instalado para ejecutar el proyecto: Node.js 18+, npm, VS Code o similar.
- Copia todo el contenido del campo **Código Base** de este reto — incluyendo el texto de instrucciones que aparece al inicio.
- Abre un asistente de IA (Claude en claude.ai, ChatGPT o Gemini — se recomienda Claude), pega el contenido copiado en el chat y envíalo.
- El asistente analizará los archivos, corregirá errores y generará un archivo ZIP descargable. Descárgalo y extráelo en la carpeta donde quieras trabajar.
- Ejecuta `npm install && npm run build` (o `npm start`). Si no hay errores, estás listo.

**Entregable:** El proyecto compila/arranca sin errores.

<details>
<summary>Pistas de conocimiento</summary>

- Copia el Código Base completo incluyendo el texto de instrucciones al inicio — esas instrucciones le indican al asistente exactamente qué hacer con los archivos.
- Si el asistente no genera el ZIP automáticamente al terminar el análisis, escríbele: "genera el ZIP ahora".
- Si el proyecto tiene errores al arrancar, comparte el mensaje de error con el mismo asistente para que lo corrija.

</details>

### Fase 1: Diferenciación de Repositorios

**Objetivo:** Entender y aplicar la diferencia entre repositorios locales y remotos en Git.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Investiga las diferencias fundamentales entre repositorios locales y remotos en Git.
- Crea una guía que explique cómo sincronizar cambios entre ambos tipos de repositorios.
- Identifica posibles problemas que pueden surgir durante la sincronización y cómo mitigarlos.

**Entregable:** Guía documentada que explica la diferencia entre repositorios locales y remotos, y cómo manejar la sincronización.

<details>
<summary>Pistas de conocimiento</summary>

- Revisa conceptos básicos de Git como clone, push, pull, fetch.
- Considera escenarios de trabajo en equipo y cómo afectan las operaciones de sincronización.

</details>

### Fase 2: Resolución de Conflictos

**Objetivo:** Adquirir habilidades para resolver conflictos de manera eficiente en Git.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Identifica los tipos de conflictos que pueden ocurrir en Git.
- Crea un procedimiento paso a paso para resolver conflictos de merge.
- Proporciona ejemplos de conflictos comunes y cómo resolverlos.

**Entregable:** Procedimiento documentado para la resolución de conflictos en Git con ejemplos prácticos.

<details>
<summary>Pistas de conocimiento</summary>

- Revisa herramientas y comandos de Git para identificar y resolver conflictos.
- Considera escenarios donde múltiples desarrolladores están trabajando en la misma rama.

</details>

### Fase 3: Conceptos Fundamentales de Control de Versiones

**Objetivo:** Comprender y aplicar conceptos clave de control de versiones en Git.

**Tiempo estimado:** 3 horas

**Instrucciones:**

- Investiga y documenta los conceptos fundamentales de control de versiones en Git.
- Crea una guía que explique cómo utilizar ramas temporales (features, hotfix, release) y ramas inmutables en enfoques modernos de despliegue.
- Proporciona ejemplos prácticos de cómo aplicar estos conceptos en proyectos reales.

**Entregable:** Guía documentada que explica los conceptos fundamentales de control de versiones en Git, incluyendo el uso de ramas temporales y inmutables.

<details>
<summary>Pistas de conocimiento</summary>

- Revisa metodologías como GitFlow y trunk-based development.
- Considera cómo estos conceptos pueden aplicarse en proyectos de arquitectura SOA y sistemas distribuidos.

</details>

### Fase 4: Aplicación Práctica de Enfoques de Despliegue

**Objetivo:** Aplicar conocimientos de versionamiento en un proyecto real utilizando GitFlow y trunk-based development.

**Tiempo estimado:** 2 horas

**Instrucciones:**

- Selecciona un proyecto real o ficticio que requiera despliegue.
- Aplica los conceptos de versionamiento aprendidos para gestionar el proyecto utilizando GitFlow y trunk-based development.
- Documenta el proceso y los resultados obtenidos.
- Evalúa los pros y contras de cada enfoque y decide cuál es más adecuado para el proyecto.

**Entregable:** Documentación del proceso de aplicación de GitFlow y trunk-based development en un proyecto real, incluyendo evaluación de pros y contras.

<details>
<summary>Pistas de conocimiento</summary>

- Revisa casos de estudio de proyectos que han utilizado GitFlow y trunk-based development.
- Considera cómo la elección del enfoque de despliegue puede afectar la colaboración y el despliegue en tu equipo.

</details>

## Dimensiones Evaluadas

- **queEs**: ¿Qué son los repositorios locales y remotos en Git y cómo difieren?
- **paraQueSirve**: ¿Para qué sirven las ramas temporales y inmutables en Git?
- **comoSeUsa**: ¿Cómo se resuelven los conflictos de merge en Git?
- **erroresComunes**: ¿Cuáles son los errores comunes al versionar con Git y cómo se pueden evitar?
- **queDecisionesImplica**: ¿Qué decisiones implica la elección entre GitFlow y trunk-based development para un proyecto?

## Criterios de Evaluacion

- Diferenciar entre repositorios locales y remotos en Git.
- Resolver conflictos de merge de manera eficiente.
- Aplicar conceptos fundamentales de control de versiones en Git.
- Evaluar y decidir entre GitFlow y trunk-based development para un proyecto.

## Como trabajar con un asistente de IA

Hay dos caminos, elegi uno:

- **AGENTS.md** (recomendado) — instrucciones nativas del repo. Abri esta carpeta con tu agente local (Claude Code, Cursor, Codex, Copilot, Gemini) y las carga solo. Sabe que archivos faltan y con que comando se verifica, y completa el scaffold escribiendo en disco.
- **PROMPT_MEJORA.md** — para copiar y pegar en un chat (claude.ai, ChatGPT). Devuelve un ZIP con el proyecto. Sirve si no tenes un agente en el IDE.

Ninguno de los dos resuelve las fases del reto: eso es tu trabajo.

## Verificacion

El proyecto esta listo para trabajar cuando este comando corre sin errores:

```bash
npx --yes @redocly/cli lint openapi/openapi.yaml
```

---

*Reto generado automaticamente por Challenge Generator - Pragma*
