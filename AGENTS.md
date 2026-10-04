# AGENTS.md

Instrucciones para el agente de IA que abra este repositorio (Claude Code, Cursor, Codex, Copilot, Gemini). Se cargan solas: no hay que pegar nada en ningun chat.

## Que es este repositorio

Es el codigo base de un reto de aprendizaje de Pragma: **Maestría en Versionamiento con Git**.

| | |
|---|---|
| Tema | Técnicas de versionamiento |
| Nivel | senior-l2 |
| Chapter | Integración — Desarrollo |
| Especialidad | Api |
| Stack | OpenAPI 3.1 / API First con políticas de gateway |
| Patron arquitectonico | Estructura modular de documentación y políticas con enfoque API Gateway |
| Tiempo estimado | 10 horas |

## Receta del stack

Esqueleto obligatorio:

- `openapi.yaml con paths, schemas y responses completos`
- `policies/ con las politicas del gateway (rate limit, auth, transformacion)`
- `environments/ con la configuracion por ambiente`
- `tests/ con la coleccion de contrato`
- `README.md con el contrato y los codigos de error`

Dependencias:

- @redocly/cli 1.12.0
- Postman n/a
- OpenAPI 3.1 n/a
- API Gateway (APIGee, Azure API Management, etc.) n/a

## Tu tarea

Dejar este proyecto en estado **verificable**: que el comando de verificacion corra sin errores. Escribi los archivos en disco, en este repositorio. No generes ZIPs ni archivos adjuntos.

En orden:

1. Corre `npx --yes @redocly/cli lint openapi/openapi.yaml` y mira que falla.
2. Completa lo que falte de la lista de abajo: manifiesto de dependencias, punto de entrada, capa de interfaz y las capas del patron declarado.
3. Arregla SOLO los errores que impiden compilar o arrancar.
4. Volve a correr `npx --yes @redocly/cli lint openapi/openapi.yaml` hasta que pase.
5. Pará ahí.

## Regla dura: las fases son trabajo del humano

**PROHIBIDO implementar los entregables de las fases.** El valor del reto esta en que la persona los resuelva. Tu trabajo es que tenga un proyecto que arranca; el hueco pedagogico se queda como esta.

No resuelvas nada de esto:

- **Fase 1 — Diferenciación de Repositorios**: Guía documentada que explica la diferencia entre repositorios locales y remotos, y cómo manejar la sincronización.
- **Fase 2 — Resolución de Conflictos**: Procedimiento documentado para la resolución de conflictos en Git con ejemplos prácticos.
- **Fase 3 — Conceptos Fundamentales de Control de Versiones**: Guía documentada que explica los conceptos fundamentales de control de versiones en Git, incluyendo el uso de ramas temporales y inmutables.
- **Fase 4 — Aplicación Práctica de Enfoques de Despliegue**: Documentación del proceso de aplicación de GitFlow y trunk-based development en un proyecto real, incluyendo evaluación de pros y contras.

Distincion operativa:

- **Arreglar** (si): import faltante, tipo que no existe, dependencia sin declarar, error de sintaxis, archivo referenciado que no existe.
- **No tocar** (no): logica de negocio incompleta, validaciones ausentes, secretos hardcodeados, APIs deprecadas que funcionan, concurrencia insegura, patrones mejorables. Eso es lo que la persona tiene que encontrar.

## Superficie de practica (NO completes)

Estos archivos SON el ejercicio de la persona. No los implementes; deja stubs. No toques la logica que el reto pide completar.

- [ ] `openapi/openapi.yaml` — El topic pide el contrato de API: openapi.yaml es el ejercicio.

## Lo que falta y tenes que completar

No se detectaron huecos: estan los archivos declarados, el boilerplate del stack y ninguna referencia quedo colgando. Igual corre el comando de verificacion — que los archivos existan no garantiza que compilen.

### Presentes (12)

- `package.json`
- `openapi/openapi.yaml`
- `policies/versioning_policy.yaml`
- `policies/conflict_resolution_policy.yaml`
- `environments/dev.yaml`
- `environments/prod.yaml`
- `tests/versioning_contract_test.postman_collection.json`
- `docs/guia_repositorios_locales_remotos.md`
- `docs/procedimiento_resolucion_conflictos.md`
- `docs/conceptos_control_versiones.md`
- `README.md`
- `docs/aplicacion_gitflow_trunkbased.md`

### Capas del patron declarado

Cada una tiene que existir como directorio real con al menos un archivo. Codigo plano en la raiz no satisface el patron.

- `openapi`
- `policies`
- `environments`
- `tests`
- `docs`

## Verificacion

```bash
npx --yes @redocly/cli lint openapi/openapi.yaml
```

El comando tiene que pasar SIN implementar los archivos de la superficie de practica: solo andamiaje.

Ese comando pasando es la definicion de "terminado" para vos.

## Convenciones que tenes que respetar

- Un solo ecosistema: no declares librerias de otro lenguaje ni mezcles gestores de paquetes.
- Toda libreria que uses tiene que estar declarada en el manifiesto de dependencias.
- Todo import declarado tiene que usarse; todo tipo usado tiene que existir o venir de una dependencia declarada.
- El patron es **Estructura modular de documentación y políticas con enfoque API Gateway**: los contratos (interfaces, puertos) los define la capa interna y los implementa la externa, nunca al revés.
- Los archivos que crees llevan implementacion real, no stubs: sin `TODO`, sin cuerpos vacios, sin `// getters y setters`.

## Contexto del candidato

Sirve para calibrar el nivel del codigo, no para resolver las fases.

- Perfil: Chapter Integración, Especialidad Desarrollador, Tecnología API, Senior
- Brecha que el reto ataca: Dominar técnicas avanzadas de versionamiento con Git: diferenciación entre repositorio local y remoto, resolución de conflictos, conceptos fundamentales de control de versiones, ramas temporales (features, hotfix, release), y ramas inmutables en enfoques modernos de despliegue (GitFlow, trunk-based development). Candidato con experiencia senior en arquitectura SOA y sistemas distribuidos, trabajando en equipos distribuidos.

---

*Generado por Challenge Generator — Pragma. `README.md` tiene el enunciado completo del reto para la persona. `PROMPT_MEJORA.md` es la variante para pegar en un chat, si se prefiere ese flujo.*
