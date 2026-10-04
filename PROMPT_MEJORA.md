# Prompt para Mejorar el Codigo Base

Copia y pega el contenido del bloque de abajo en un asistente de IA (Claude, ChatGPT)
para obtener un ZIP con el proyecto completo y arrancable.

Si preferis trabajar en tu editor con un agente local (Claude Code, Cursor, Copilot), usa `AGENTS.md` en vez de este archivo: dice lo mismo pero para que escriba los archivos en disco.

## Las dos reglas que no se negocian

1. **Completa el boilerplate.** Todo lo que el proyecto necesita para compilar y arrancar: manifiesto de dependencias, punto de entrada, configuracion, capa de interfaz, y las capas del patron arquitectonico declarado. Eso es andamiaje y es tu trabajo.
2. **NO resuelvas el reto.** Los entregables de las fases son el trabajo de la persona. El hueco pedagogico se deja como esta: el proyecto arranca, pero lo que el reto pide implementar NO esta implementado.

Dicho de otra forma: si algo impide compilar, arreglalo. Si algo es logica de negocio incompleta, validaciones ausentes, un secreto hardcodeado o un patron mejorable, dejalo exactamente como esta — es lo que la persona tiene que encontrar.

## Superficie de practica — NO resuelvas

Estos archivos SON el ejercicio de la persona. No los implementes; deja stubs.

- `openapi/openapi.yaml` — El topic pide el contrato de API: openapi.yaml es el ejercicio.

## Como saber que terminaste

```bash
npx --yes @redocly/cli lint openapi/openapi.yaml
```

Ese comando corriendo sin errores es la definicion de "listo".

---

```
## Briefing del reto (autoridad)
Este bloque manda sobre los archivos adjuntos. El stack y el rol salen de AQUÍ, no de un topic genérico ni de markdown placeholder.

### Perfil
Chapter Integración, Especialidad Desarrollador, Tecnología API, Senior

### Brecha de conocimiento
Dominar técnicas avanzadas de versionamiento con Git: diferenciación entre repositorio local y remoto, resolución de conflictos, conceptos fundamentales de control de versiones, ramas temporales (features, hotfix, release), y ramas inmutables en enfoques modernos de despliegue (GitFlow, trunk-based development). Candidato con experiencia senior en arquitectura SOA y sistemas distribuidos, trabajando en equipos distribuidos.

### Reto
- Tema: Técnicas de versionamiento
- Seniority: senior-l2
- Tipo: mixed
- Título: Maestría en Versionamiento con Git
- Tiempo estimado: 10 horas

### Fases (trabajo del HUMANO — PROHIBIDO completarlas)
No implementes estos entregables. Dejalos como hueco pedagógico. El asistente solo materializa el proyecto arrancable para que el participante pueda trabajar.
- Fase 1: Diferenciación de Repositorios — objetivo: Entender y aplicar la diferencia entre repositorios locales y remotos en Git. — entregable (NO resolver): Guía documentada que explica la diferencia entre repositorios locales y remotos, y cómo manejar la sincronización.
- Fase 2: Resolución de Conflictos — objetivo: Adquirir habilidades para resolver conflictos de manera eficiente en Git. — entregable (NO resolver): Procedimiento documentado para la resolución de conflictos en Git con ejemplos prácticos.
- Fase 3: Conceptos Fundamentales de Control de Versiones — objetivo: Comprender y aplicar conceptos clave de control de versiones en Git. — entregable (NO resolver): Guía documentada que explica los conceptos fundamentales de control de versiones en Git, incluyendo el uso de ramas temporales y inmutables.
- Fase 4: Aplicación Práctica de Enfoques de Despliegue — objetivo: Aplicar conocimientos de versionamiento en un proyecto real utilizando GitFlow y trunk-based development. — entregable (NO resolver): Documentación del proceso de aplicación de GitFlow y trunk-based development en un proyecto real, incluyendo evaluación de pros y contras.

Eres un asistente experto en análisis, corrección y generación de archivos de cualquier tipo:
código fuente, documentación, hojas de cálculo, documentos Word, configuraciones, entre otros.
Voy a enviarte una cadena de texto que contiene uno o más archivos. Cada archivo está delimitado por un marcador con el siguiente formato:
// === ARCHIVO: ruta/del/archivo.extension ===
o también puede aparecer como:
## === ARCHIVO: ruta/del/archivo.extension ===
Lo que sigue al marcador puede ser:

El contenido real del archivo (código, texto, YAML, etc.)
Una descripción en lenguaje natural de lo que debe contener el archivo


TU TAREA
PASO 0 — ¿Esto es un proyecto o una carcasa?
Antes de extraer archivos, leé el Briefing (si está) y diagnosticá el adjunto.

Es CARCASA si ocurre CUALQUIERA de estas:
- No hay manifiesto de dependencias del stack del briefing (manifest.json de VTEX IO / package.json / pom.xml / build.gradle / requirements.txt / go.mod / *.tf / *.csproj, según corresponda)
- Hay un "binario" que en realidad es un comentario ("no puede ser mostrado como texto plano", placeholder .fig/.docx vacío)
- Los markdowns ya completan entregables de fases posteriores ("se implementó fade-in", lista de áreas ya resuelta)

Si es CARCASA:
- MATERIALIZÁ un proyecto que arranca en el stack del briefing (VTEX IO Store Framework, Angular, Terraform, pytest, Nest, etc.). Incluí manifiesto, punto de entrada y capa de interfaz reales.
- NO copies los markdowns de "solución" como si fueran el producto. Son ruido de generación.
- NO resuelvas las fases del briefing (están marcadas PROHIBIDO). Dejá el hueco pedagógico: el flujo existe, las microinteracciones/calidad/infra que el reto pide NO están hechas.
- Después seguí al PASO 5 (ZIP).

Si es un proyecto REAL (manifiesto + código que compila o arranca):
- Seguí PASO 1 en adelante. 🔴 compilación sí. 🟡 pedagógico no.

PASO 1 — Detección y extracción
Identifica todos los archivos presentes en la cadena. Para cada archivo extrae:

Su ruta completa (ej: src/main/java/com/pragma/Service.java)
Su contenido o descripción

PASO 2 — Clasificación por tipo
Clasifica cada archivo en una de estas categorías:
A) Código fuente (Java, Python, TypeScript, JavaScript, Kotlin, etc.)
B) Configuración / documentación (YAML, properties, Markdown, JSON, txt, etc.)
C) Excel (.xlsx, .xls, .csv)
D) Word (.docx, .doc)
E) Otro tipo de archivo binario o especial
PASO 3 — Clasificación de errores en código fuente

Objetivo prioritario: que el proyecto compile. No corrijas flujo de negocio ni lógica funcional.

Antes de modificar cualquier archivo de código fuente, clasifica cada problema encontrado en una de estas dos categorías:
🔴 ERROR DE COMPILACIÓN — corregir siempre
Son errores que impiden que el proyecto arranque, sin valor pedagógico:

Import faltante o incorrecto
Clase, método o variable referenciada que no existe en ningún archivo del proyecto
Error de sintaxis
Anotación con atributos inválidos
Dependencia ausente en pom.xml, package.json, etc.
Archivo referenciado que no existe y debe ser creado con implementación mínima

→ CORREGIR estos errores.
🟡 PROBLEMA FUNCIONAL O DE CALIDAD — preservar siempre
Son problemas que no impiden compilar. Pueden ser intencionales para el aprendizaje:

Clave secreta hardcodeada ("secret", "password123")
API deprecada que funciona pero tiene reemplazo moderno
Lógica de negocio incorrecta o incompleta
Código redundante o de baja legibilidad
Falta de validaciones en flujo de negocio
Patrones de diseño incorrectos pero funcionales
Concurrencia no segura
Configuración funcional pero no óptima

→ PRESERVAR tal cual. No corregir, no mejorar, no comentar.
PASO 4 — Procesamiento según tipo de archivo
Tipo A — Código fuente
Aplica únicamente las correcciones clasificadas como 🔴 ERROR DE COMPILACIÓN.
No alteres ningún elemento clasificado como 🟡 PROBLEMA FUNCIONAL O DE CALIDAD.
Si falta un archivo referenciado, créalo con la implementación mínima necesaria para compilar.
Tipo B — Configuración / documentación
Extrae el contenido tal cual, sin modificaciones salvo errores evidentes de sintaxis
(ej: YAML mal indentado).
Tipo C — Excel (.xlsx)
Si viene con contenido real, genera el archivo respetando ese contenido.
Si viene con descripción en lenguaje natural, genera un archivo Excel funcional con:

Fila de encabezados en negrita con color de fondo distintivo
Columnas con ancho ajustado al contenido
Tipos de dato correctos por columna
Validaciones si la descripción lo indica
Hojas nombradas descriptivamente si hay más de una
Filas de ejemplo si no hay datos reales

Tipo D — Word (.docx)
Si viene con contenido real, genera el archivo respetando ese contenido.
Si viene con descripción en lenguaje natural, genera un documento Word funcional con:

Estilos de título (Título 1, Título 2) para jerarquía de secciones
Fuente legible (Calibri o equivalente), tamaño 11-12pt para cuerpo
Márgenes estándar
Tabla de contenido si tiene múltiples secciones
Tablas con encabezados en negrita si aplica

Tipo E — Otro
Genera el archivo con el contenido o estructura más apropiada según la descripción.
PASO 5 — Exportación en ZIP
Empaqueta todos los archivos en un único archivo ZIP descargable respetando exactamente
la estructura de rutas indicada por los marcadores.
El ZIP debe incluir:

Archivos de código con únicamente los errores de compilación corregidos
Archivos de configuración y documentación sin cambios
Archivos nuevos creados para resolver dependencias de compilación faltantes
Archivos Excel y Word generados desde descripción

IMPORTANTE: El ZIP debe estar listo para descargar al finalizar. No preguntes si el usuario
quiere generarlo. Simplemente genera el archivo y proporciona el enlace de descarga; No debes desplegar en el chat el resumen de lo que arreglaste al Zip, solo entregalo.

REGLAS IMPORTANTES

No omitas ningún archivo aunque no tenga errores ni modificaciones
Respeta los nombres y rutas exactas indicadas por los marcadores
Si un archivo no tiene marcador claro, infiere el nombre desde su contenido
Si la cadena contiene solo documentación, placeholders o binarios fake, NO la reproduzcas:
aplicá PASO 0 (materializar el proyecto del briefing). Reproducir la carcasa es un fallo.
No agregues texto después del enlace de descarga del ZIP
No preguntes si el usuario quiere el ZIP: simplemente generalo siempre
Si detectas que falta un archivo de configuración necesario para compilar
(pom.xml, package.json, requirements.txt, build.gradle, etc.), créalo e inclúyelo
inferiendo su contenido desde los imports y frameworks detectados en el código
Nunca corrijas problemas 🟡 aunque parezcan obvios o fáciles de mejorar.
El participante que recibirá este proyecto los debe encontrar y resolver él mismo.


INPUT
Aquí está la cadena con los archivos:

// === ARCHIVO: package.json ===
{
  "name": "api-versioning-gateway",
  "version": "1.0.0",
  "description": "Proyecto de API First con políticas de gateway para versionamiento y manejo de conflictos",
  "main": "openapi/openapi.yaml",
  "scripts": {
    "lint": "npx @redocly/cli lint openapi/openapi.yaml",
    "validate": "npm run lint",
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "openapi",
    "api-gateway",
    "versioning",
    "git",
    "conflict-resolution"
  ],
  "author": "Pragma S.A.",
  "license": "MIT",
  "devDependencies": {
    "@redocly/cli": "1.12.0"
  },
  "dependencies": {},
  "engines": {
    "node": ">=16.0.0"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/pragma/api-versioning-gateway.git"
  },
  "bugs": {
    "url": "https://github.com/pragma/api-versioning-gateway/issues"
  },
  "homepage": "https://github.com/pragma/api-versioning-gateway#readme",
  "files": [
    "openapi/",
    "policies/",
    "environments/",
    "tests/",
    "docs/"
  ]
}

// === ARCHIVO: openapi/openapi.yaml ===
openapi: 3.1.0
info:
  title: API Versioning Gateway
  description: |-
    Contrato de API para gestión de versionamiento y manejo de conflictos en despliegues.
    Soporta múltiples versiones activas mediante routing por path y headers.
  version: 1.0.0
  contact:
    name: Pragma S.A.
    email: arquitectura@pragma.com.co
  license:
    name: MIT
    url: https://opensource.org/licenses/MIT
servers:
  - url: https://api.example.com
    description: Servidor de producción
    variables:
      version:
        default: v1
        enum:
          - v1
          - v2
  - url: https://staging-api.example.com
    description: Servidor de staging
  - url: http://localhost:8080
    description: Servidor de desarrollo
tags:
  - name: versionamiento
    description: Endpoints relacionados con el versionamiento de API
  - name: conflictos
    description: Gestión de conflictos en despliegues
  - name: ramas
    description: Operaciones sobre ramas de despliegue
paths:
  /v1/repositorios:
    get:
      tags:
        - versionamiento
      summary: Listar repositorios disponibles
      description: Retorna la lista de repositorios configurados en el sistema
      operationId: listRepositorios
      parameters:
        - name: page
          in: query
          schema:
            type: integer
            default: 1
        - name: limit
          in: query
          schema:
            type: integer
            default: 20
      responses:
        '200':
          description: Lista de repositorios
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RepositoriosResponse'
        '400':
          $ref: '#/components/responses/BadRequest'
        '500':
          $ref: '#/components/responses/InternalServerError'
    post:
      tags:
        - versionamiento
      summary: Crear nuevo repositorio
      description: Registra un nuevo repositorio en el sistema de control de versiones
      operationId: createRepositorio
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/RepositorioInput'
      responses:
        '201':
          description: Repositorio creado exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RepositorioOutput'
        '400':
          $ref: '#/components/responses/BadRequest'
        '409':
          $ref: '#/components/responses/Conflict'
  /v1/repositorios/{repoId}/ramas:
    get:
      tags:
        - ramas
      summary: Listar ramas de un repositorio
      description: Obtiene todas las ramas existentes en el repositorio especificado
      operationId: listBranches
      parameters:
        - name: repoId
          in: path
          required: true
          schema:
            type: string
        - name: tipo
          in: query
          schema:
            type: string
            enum:
              - feature
              - hotfix
              - release
              - main
      responses:
        '200':
          description: Lista de ramas
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RamasResponse'
        '404':
          $ref: '#/components/responses/NotFound'
  /v1/ramas:
    post:
      tags:
        - ramas
      summary: Crear nueva rama
      description: Crea una nueva rama en el repositorio especificado
      operationId: createBranch
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/RamaInput'
      responses:
        '201':
          description: Rama creada exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RamaOutput'
        '400':
          $ref: '#/components/responses/BadRequest'
        '409':
          $ref: '#/components/responses/Conflict'
  /v1/conflictos:
    get:
      tags:
        - conflictos
      summary: Listar conflictos activos
      description: Retorna los conflictos de merge pendientes de resolución
      operationId: listConflicts
      parameters:
        - name: estado
          in: query
          schema:
            type: string
            enum:
              - pending
              - resolved
              - all
            default: pending
      responses:
        '200':
          description: Lista de conflictos
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ConflictosResponse'
  /v1/conflictos/{conflictoId}/resolver:
    post:
      tags:
        - conflictos
      summary: Resolver conflicto de merge
      description: Aplica una estrategia de resolución al conflicto especificado
      operationId: resolveConflict
      parameters:
        - name: conflictoId
          in: path
          required: true
          schema:
            type: string
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/ResolucionInput'
      responses:
        '200':
          description: Conflicto resuelto exitosamente
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/ResolucionOutput'
        '400':
          $ref: '#/components/responses/BadRequest'
        '404':
          $ref: '#/components/responses/NotFound'
        '409':
          $ref: '#/components/responses/Conflict'
  /v2/repositorios:
    get:
      tags:
        - versionamiento
      summary: Listar repositorios v2
      description: Versión mejorada con filtros avanzados y paginación optimizada
      operationId: listRepositoriosV2
      parameters:
        - name: page
          in: query
          schema:
            type: integer
            default: 1
        - name: limit
          in: query
          schema:
            type: integer
            default: 20
        - name: sortBy
          in: query
          schema:
            type: string
            enum:
              - nombre
              - fecha_creacion
              - ultima_actualizacion
        - name: order
          in: query
          schema:
            type: string
            enum:
              - asc
              - desc
              default: asc
      responses:
        '200':
          description: Lista de repositorios v2
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/RepositoriosResponseV2'
        '400':
          $ref: '#/components/responses/BadRequest'
        '500':
          $ref: '#/components/responses/InternalServerError'
components:
  schemas:
    RepositorioInput:
      type: object
      required:
        - nombre
        - tipo
        - urlRemoto
      properties:
        nombre:
          type: string
          description: Nombre único del repositorio
          example: mi-proyecto
        tipo:
          type: string
          enum:
            - git
            - svn
          description: Tipo de sistema de control de versiones
          example: git
        urlRemoto:
          type: string
          format: uri
          description: URL del repositorio remoto
          example: https://github.com/usuario/mi-proyecto.git
        descripcion:
          type: string
          description: Descripción opcional del repositorio
          example: Repositorio principal del proyecto
        ramaDefault:
          type: string
          default: main
          description: Rama principal del repositorio
          example: main
    RepositorioOutput:
      type: object
      properties:
        id:
          type: string
          format: uuid
          description: Identificador único del repositorio
          example: 550e8400-e29b-41d4-a716-446655440000
        nombre:
          type: string
        tipo:
          type: string
        urlRemoto:
          type: string
        descripcion:
          type: string
        ramaDefault:
          type: string
        fechaCreacion:
          type: string
          format: date-time
        ultimaActualizacion:
          type: string
          format: date-time
    RepositoriosResponse:
      type: object
      properties:
        data:
          type: array
          items:
            $ref: '#/components/schemas/RepositorioOutput'
        meta:
          $ref: '#/components/schemas/PaginationMeta'
    RepositoriosResponseV2:
      type: object
      properties:
        data:
          type: array
          items:
            $ref: '#/components/schemas/RepositorioOutput'
        meta:
          $ref: '#/components/schemas/PaginationMetaV2'
    PaginationMeta:
      type: object
      properties:
        page:
          type: integer
        limit:
          type: integer
        total:
          type: integer
        totalPages:
          type: integer
    PaginationMetaV2:
      allOf:
        - $ref: '#/components/schemas/PaginationMeta'
        - type: object
          properties:
            sortBy:
              type: string
            order:
              type: string
            hasMore:
              type: boolean
    RamaInput:
      type: object
      required:
        - nombre
        - repositorioId
        - tipo
      properties:
        nombre:
          type: string
          description: Nombre de la rama
          example: feature/nueva-funcionalidad
        repositorioId:
          type: string
          format: uuid
          description: ID del repositorio donde se creará la rama
        tipo:
          type: string
          enum:
            - feature
            - hotfix
            - release
            - main
          description: Tipo de rama según estrategia de despliegue
          example: feature
        ramaBase:
          type: string
          description: Rama desde la cual se crea la nueva rama
          example: main
    RamaOutput:
      type: object
      properties:
        id:
          type: string
          format: uuid
        nombre:
          type: string
        tipo:
          type: string
        ramaBase:
          type: string
        repositorioId:
          type: string
        fechaCreacion:
          type: string
          format: date-time
        ultimoCommit:
          type: string
    RamasResponse:
      type: object
      properties:
        data:
          type: array
          items:
            $ref: '#/components/schemas/RamaOutput'
        total:
          type: integer
    ConflictoInput:
      type: object
      properties:
        archivo:
          type: string
        ramaOrigen:
          type: string
        ramaDestino:
          type: string
        tipoConflicto:
          type: string
          enum:
            - contenido
            - renombrado
            - eliminado
    ConflictoOutput:
      type: object
      properties:
        id:
          type: string
          format: uuid
        archivo:
          type: string
        ramaOrigen:
          type: string
        ramaDestino:
          type: string
        tipoConflicto:
          type: string
        estado:
          type: string
          enum:
            - pending
            - resolved
            - manual
        fechaDeteccion:
          type: string
          format: date-time
    ConflictosResponse:
      type: object
      properties:
        data:
          type: array
          items:
            $ref: '#/components/schemas/ConflictoOutput'
        total:
          type: integer
        pendientes:
          type: integer
    ResolucionInput:
      type: object
      required:
        - estrategia
      properties:
        estrategia:
          type: string
          enum:
            - ours
            - theirs
            - manual
            - merge
          description: Estrategia de resolución del conflicto
          example: manual
        contenido:
          type: string
          description: Contenido resuelto (requerido si estrategia es manual)
        comentario:
          type: string
          description: Comentario sobre la resolución
    ResolucionOutput:
      type: object
      properties:
        conflictoId:
          type: string
        estado:
          type: string
        estrategiaAplicada:
          type: string
        resueltoPor:
          type: string
        fechaResolucion:
          type: string
          format: date-time
    ErrorResponse:
      type: object
      properties:
        codigo:
          type: string
        mensaje:
          type: string
        detalles:
          type: array
          items:
            type: object
            properties:
              campo:
                type: string
              mensaje:
                type: string
    ErrorDetail:
      type: object
      properties:
        campo:
          type: string
        mensaje:
          type: string
  responses:
    BadRequest:
      description: Solicitud inválida
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
          example:
            codigo: BAD_REQUEST
            mensaje: La solicitud contiene parámetros inválidos
            detalles:
              - campo: nombre
                mensaje: El campo nombre no puede estar vacío
    NotFound:
      description: Recurso no encontrado
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
          example:
            codigo: NOT_FOUND
            mensaje: El recurso solicitado no existe
    Conflict:
      description: Conflicto de estado
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
          example:
            codigo: CONFLICT
            mensaje: El recurso ya existe o hay un conflicto con el estado actual
    InternalServerError:
      description: Error interno del servidor
      content:
        application/json:
          schema:
            $ref: '#/components/schemas/ErrorResponse'
          example:
            codigo: INTERNAL_ERROR
            mensaje: Ocurrió un error interno al procesar la solicitud
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
    apiKeyHeader:
      type: apiKey
      in: header
      name: X-API-Key
security:
  - bearerAuth: []
  - apiKeyHeader: []

// === ARCHIVO: policies/versioning_policy.yaml ===
version: 1.0.0
type: gateway-policy
name: Versionamiento de API
description: |-
  Política de gateway para manejar múltiples versiones de API mediante routing basado en headers y paths.
  Implementa versionamiento por URL path y por header Accept para maximizar flexibilidad.
  Incluye reglas de deprecación y migración entre versiones.

metadata:
  autor: Equipo de Arquitectura Pragma
  fechaCreacion: '2025-01-15'
  ultimaActualizacion: '2025-01-15'
  tags:
    - versionamiento
    - routing
    - api-gateway
    - deprecacion

configuracion:
  versionesSoportadas:
    - version: v1
      estado: deprecated
      fechaDeprecacion: '2025-06-01'
      fechaRetiro: '2025-12-01'
      rutaBase: /v1
      headerVersion: application/vnd.pragma.v1+json
    - version: v2
      estado: active
      rutaBase: /v2
      headerVersion: application/vnd.pragma.v2+json
    - version: v3
      estado: beta
      rutaBase: /v3
      headerVersion: application/vnd.pragma.v3+json
      requiereHeader: false

  estrategiaVersionamiento: hybrid
  permitirVersionPorPath: true
  permitirVersionPorHeader: true
  headerDefault: Accept
  versionHeaderName: X-API-Version

  reglasRouting:
    - nombre: Routing por Path
      prioridad: 1
      condicion:
        tipo: path
        patron: '^/v[0-9]+/'
      accion:
        tipo: route
        destino: backend-{version}
      metadata:
        tipoVersionamiento: path

    - nombre: Routing por Header Accept
      prioridad: 2
      condicion:
        tipo: header
        nombre: Accept
        valor: 'application/vnd.pragma.v*+json'
      accion:
        tipo: route
        destino: backend-{version}
      metadata:
        tipoVersionamiento: header

    - nombre: Version Default
      prioridad: 10
      condicion:
        tipo: always
      accion:
        tipo: redirect
        destino: /v2/
        codigo: 302
      metadata:
        tipoVersionamiento: default

  reglasDeprecacion:
    - version: v1
      acciones:
        - tipo: agregarHeader
          nombre: Deprecation
          valor: 'true'
        - tipo: agregarHeader
          nombre: Sunset
          valor: 'Sat, 01 Dec 2025 00:00:00 GMT'
        - tipo: agregarHeader
          nombre: Link
          valor: '</v2/>; rel="successor-version"'
        - tipo: log
          nivel: warning
          mensaje: 'Solicitud a versión deprecated: v1'

  politicasMigracion:
    - versionOrigen: v1
      versionDestino: v2
      tipo: gradual
      porcentaje: 10
      criterios:
        - tipo: header
          nombre: X-Migration-Cohort
          valores:
            - A
            - B
      acciones:
        - tipo: transformarRequest
          mapeos:
            - campo: query.pageSize
              origen: query.limit
              default: 20
        - tipo: transformarResponse
          mapeos:
            - campo: meta.totalPages
              origen: meta.total
              formula: 'Math.ceil(total / pageSize)'

  respuestasError:
    versionNoSoportada:
      codigo: 400
      mensaje: 'Versión de API no soportada. Versiones disponibles: v1, v2, v3'
      detalles:
        - campo: version
          mensaje: 'La versión solicitada no existe o está retire'
    versionDeprecated:
      codigo: 299
      mensaje: 'Esta versión de API está deprecada y será retirada'
      headers:
        - Deprecation
        - Sunset
        - Link
    versionInvalidHeader:
      codigo: 400
      mensaje: 'Header de versión inválido'
      detalles:
        - campo: Accept
          mensaje: 'El formato del header debe ser application/vnd.pragma.v{version}+json'

  logging:
    enabled: true
    nivel: info
    incluirHeaders: true
    incluirCuerpo: false
    camposLog:
      - api.version
      - api.versioning.strategy
      - api.versioning.routing.rule
      - api.deprecation.active
      - backend.target.version

  metrics:
    enabled: true
    metricas:
      - nombre: api_version_requests
        tipo: counter
        etiquetas:
          - version
          - routing.strategy
          - status
      - nombre: api_version_deprecation_warnings
        tipo: counter
        etiquetas:
          - version
      - nombre: api_version_migration_count
        tipo: counter
        etiquetas:
          - from.version
          - to.version

// === ARCHIVO: policies/conflict_resolution_policy.yaml ===
version: 1.0.0
type: gateway-policy
name: Resolución de Conflictos de Merge
description: |-
  Política para manejar conflictos de merge en despliegues de ramas.
  Define estrategias de resolución automática, reglas de fallback y manejo de errores.
  Implementa detección temprana y notificación de conflictos potenciales.

metadata:
  autor: Equipo de Arquitectura Pragma
  fechaCreacion: '2025-01-15'
  ultimaActualizacion: '2025-01-15'
  tags:
    - merge
    - conflictos
    - despliegues
    - git

configuracion:
  estrategiasResolucion:
    - nombre: ours
      descripcion: Preferir cambios de la rama actual
      automatica: true
      aplicableA:
        - conflicto.contenido.simple
        - conflicto.metadata
    - nombre: theirs
      descripcion: Preferir cambios de la rama entrante
      automatica: true
      aplicableA:
        - conflicto.contenido.simple
        - conflicto.metadata
    - nombre: manual
      descripcion: Requiere intervención manual
      automatica: false
      aplicableA:
        - conflicto.contenido.complejo
        - conflicto.binario
        - conflicto.renombrado
    - nombre: merge
      descripcion: Intentar merge automático con marcadores
      automatica: true
      aplicableA:
        - conflicto.contenido

  reglasDeteccion:
    - nombre: Detectar conflictos potenciales
      tipo: pre-merge
      condicion:
        tipo: rama
        patrones:
          - feature/*
          - hotfix/*
          - release/*
      accion:
        tipo: analizar
        incluirHistorico: true
        profundidadMaxima: 10
      notificar:
        canales:
          - email
          - slack
        umbral: 5

    - nombre: Validar compatibilidad de schemas
      tipo: pre-merge
      condicion:
        tipo: archivos
        extensiones:
          - .yaml
          - .json
          - .proto
      accion:
        tipo: validarSchema
        strictMode: true
      generarReporte: true

    - nombre: Verificar cambios en contratos
      tipo: pre-merge
      condicion:
        tipo: path
        patrones:
          - '**/openapi.yaml'
          - '**/schemas/**'
          - '**/contracts/**'
      accion:
        tipo: validarContrato
        backwardCompatible: true
      notificar:
        canales:
          - email
        roles:
          - architect
          - tech-lead

  reglasFallback:
    - nombre: Fallback por timeout
      condicion:
        tipo: timeout
        limite: 300
      accion:
        tipo: crearRamaConflicto
        prefijo: conflict/
        notificar: true
      registro:
        tipo: incident
        severidad: high

    - nombre: Fallback por conflictos binarios
      condicion:
        tipo: tipoConflicto
        valor: binario
      accion:
        tipo: rechazar
        mensaje: 'Conflicto binario requiere resolución manual'
        crearTicket: true
      registro:
        tipo: incident
        severidad: critical

    - nombre: Fallback por múltiples conflictos
      condicion:
        tipo: cantidad
        limite: 10
      accion:
        tipo: crearRamaConflicto
        prefijo: conflict/manual-
        asignar: auto
        notificar: true
      registro:
        tipo: incident
        severidad: medium

  manejoErrores:
    erroresRecuperables:
      - nombre: Timeout de red
        codigo: NET_TIMEOUT
        accion: reintentar
        reintentos: 3
        intervalo: 5000

      - nombre: Repo no accesible
        codigo: REPO_ACCESS_DENIED
        accion: notificar
        canales:
          - email
          - slack

    erroresNoRecuperables:
      - nombre: Corrupción de repositorio
        codigo: REPO_CORRUPTED
        accion: bloquear
        notificar: true
        severidad: critical

      - nombre: Permisos insuficientes
        codigo: INSUFFICIENT_PERMISSIONS
        accion: rechazar
        mensaje: 'No tienes permisos para realizar esta operación'

  notificaciones:
    canales:
      - nombre: email
        tipo: smtp
        configuracion:
          from: git-conflicts@pragma.com.co
          to:
            - team-leads@pragma.com.co
          subject: '[Conflicto] Merge conflict detected in {repo}/{branch}'
          template: conflict-notification.html

      - nombre: slack
        tipo: webhook
        configuracion:
          url: https://hooks.slack.com/services/xxx
          channel: '#git-conflicts'
          username: Git Conflict Bot
          template: slack-conflict-message.json

      - nombre: jira
        tipo: api
        configuracion:
          url: https://pragma.atlassian.net/rest/api/3
          project: DEVOPS
          tipoIssue: Bug
          prioridad: High

    reglasNotificacion:
      - evento: conflicto.detectado
        canales:
          - email
          - slack
        delay: 0
        filtros:
          - tipo: severidad
            valores:
              - high
              - critical

      - evento: conflicto.resuelto
        canales:
          - slack
        delay: 0
        filtros: []

      - evento: conflicto.manual.required
        canales:
          - email
          - jira
          - slack
        delay: 0
        filtros: []

  colaConflictos:
    nombre: conflict-resolution-queue
    tipo: fifo
    maxSize: 1000
    retention: 7d
    prioridadPorTipo:
      critical: 1
      high: 2
      medium: 3
      low: 4
    dlq: conflict-resolution-dlq
    politicaReintento:
      maxReintentos: 3
      backoff: exponential
      inicial: 1000
      max: 30000

  logging:
    enabled: true
    nivel: debug
    incluirTraza: true
    camposLog:
      - conflict.id
      - conflict.type
      - conflict.files
      - conflict.strategy.applied
      - conflict.resolution.time
      - merge.request.id
      - merge.request.author
      - merge.request.branches
      - error.code
      - error.message

  metrics:
    enabled: true
    metricas:
      - nombre: merge_conflicts_total
        tipo: counter
        etiquetas:
          - repo
          - branch
          - conflict.type
      - nombre: merge_conflicts_resolved
        tipo: counter
        etiquetas:
          - repo
          - strategy
          - auto.manual
      - nombre: merge_conflicts_resolution_time
        tipo: histogram
        etiquetas:
          - repo
          - strategy
      - nombre: merge_conflicts_failed
        tipo: counter
        etiquetas:
          - repo
          - failure.reason
      - nombre: dlq_messages_total
        tipo: counter
        etiquetas:
          - queue
          - reason


// === ARCHIVO: environments/dev.yaml ===
environment:
  name: "Desarrollo"
  description: "Entorno de desarrollo para pruebas de versionamiento y validación de políticas de gateway"
  active: true

# Configuración de la API gateway para desarrollo
gateway:
  baseUrl: "https://dev-gateway.pragma.com.co"
  timeout: 30000
  retryAttempts: 3
  retryDelay: 1000

# Endpoints de la API versionados para desarrollo
api:
  v1:
    basePath: "/v1"
    url: "https://dev-gateway.pragma.com.co/v1"
    description: "Versión 1 de la API - Legacy"
    status: "deprecated"
    sunsetDate: "2025-12-31"
    deprecationNotice: "Usar v2 antes del 31 de diciembre de 2025"
    
  v2:
    basePath: "/v2"
    url: "https://dev-gateway.pragma.com.co/v2"
    description: "Versión 2 de la API - Actual"
    status: "active"
    
  v3:
    basePath: "/v3"
    url: "https://dev-gateway.pragma.com.co/v3"
    description: "Versión 3 de la API - Beta"
    status: "beta"
    featureFlags:
      - "new_auth_flow"
      - "enhanced_validation"

# Sistema de versionamiento basado en headers
versioning:
  strategy: "header"
  headerName: "Accept"
  headerPattern: "application/vnd.pragma.{version}+json"
  defaultVersion: "v2"
  supportedVersions:
    - "v1"
    - "v2"
    - "v3"
  fallbackBehavior: "redirect_to_default"

# Configuración de rutas para cada versión
routing:
  v1:
    backend: "https://dev-backend-v1.pragma.com.co"
    policies:
      - "rate-limit-basic"
      - "auth-apikey"
    
  v2:
    backend: "https://dev-backend-v2.pragma.com.co"
    policies:
      - "rate-limit-standard"
      - "auth-oauth2"
      - "validation-v2"
    
  v3:
    backend: "https://dev-backend-v3.pragma.com.co"
    policies:
      - "rate-limit-extended"
      - "auth-oauth2"
      - "validation-v3"
      - "feature-flags"

# Credenciales para desarrollo (NO usar en producción)
credentials:
  apiKey: "dev-api-key-pragma-2025-test"
  oauth2:
    clientId: "dev-client-id-pragma"
    clientSecret: "dev-secret-pragma-test"
    tokenUrl: "https://dev-auth.pragma.com.co/oauth/token"
    scopes:
      - "read:v1"
      - "write:v1"
      - "read:v2"
      - "write:v2"
      - "read:v3"
      - "write:v3"

# Configuración de rate limiting por versión
rateLimiting:
  v1:
    requestsPerMinute: 60
    burst: 10
    
  v2:
    requestsPerMinute: 120
    burst: 20
    
  v3:
    requestsPerMinute: 200
    burst: 30

# Políticas de versionamiento específicas
versioningPolicies:
  deprecation:
    warnAfter: "2025-06-01"
    blockAfter: "2025-12-31"
    migrationGuideUrl: "https://docs.pragma.com.co/migration/v1-to-v2"
    
  backwardCompatibility:
    v1ToV2:
      breakingChanges: ["response_format", "field_renamed"]
      migrationRequired: true
    v2ToV3:
      breakingChanges: []
      migrationRequired: false

# Configuración de logs para desarrollo
logging:
  level: "debug"
  includeHeaders: true
  includeBody: true
  maskSensitiveData: false

# Configuración de circuit breaker
circuitBreaker:
  enabled: true
  failureThreshold: 5
  timeout: 60000
  resetTimeout: 30000

// === ARCHIVO: environments/prod.yaml ===
environment:
  name: "Producción"
  description: "Entorno de producción con despliegues inmutables y políticas de versionamiento estrictas"
  active: true

# Configuración de la API gateway para producción
gateway:
  baseUrl: "https://gateway.pragma.com.co"
  timeout: 15000
  retryAttempts: 2
  retryDelay: 500

# Endpoints de la API versionados para producción
api:
  v1:
    basePath: "/v1"
    url: "https://gateway.pragma.com.co/v1"
    description: "Versión 1 de la API - Legacy (solo lectura)"
    status: "deprecated"
    sunsetDate: "2025-06-30"
    deprecationNotice: "V1 será descontinuada el 30 de junio de 2025. Migrar a v2"
    readOnly: true
    
  v2:
    basePath: "/v2"
    url: "https://gateway.pragma.com.co/v2"
    description: "Versión 2 de la API - Producción estable"
    status: "active"
    readOnly: false
    
  v3:
    basePath: "/v3"
    url: "https://gateway.pragma.com.co/v3"
    description: "Versión 3 de la API - Canary"
    status: "beta"
    readOnly: false
    trafficPercentage: 10

# Sistema de versionamiento basado en headers
versioning:
  strategy: "header"
  headerName: "Accept"
  headerPattern: "application/vnd.pragma.{version}+json"
  defaultVersion: "v2"
  supportedVersions:
    - "v1"
    - "v2"
    - "v3"
  fallbackBehavior: "return_406_not_acceptable"
  strictMode: true

# Configuración de rutas para cada versión en producción
routing:
  v1:
    backend: "https://backend-v1.pragma.com.co"
    policies:
      - "rate-limit-basic-prod"
      - "auth-apikey-prod"
      - "readonly-enforcer"
    
  v2:
    backend: "https://backend-v2.pragma.com.co"
    policies:
      - "rate-limit-standard-prod"
      - "auth-oauth2-prod"
      - "validation-v2-prod"
      - "audit-logging"
    
  v3:
    backend: "https://backend-v3-canary.pragma.com.co"
    policies:
      - "rate-limit-extended-prod"
      - "auth-oauth2-prod"
      - "validation-v3-prod"
      - "feature-flags-prod"
      - "canary-routing"
      - "metrics-collector"

# Credenciales de producción (simuladas - en entorno real usar secrets manager)
credentials:
  apiKey: "prod-api-key-pragma-secure-2025"
  oauth2:
    clientId: "prod-client-id-pragma"
    clientSecret: "${OAUTH_CLIENT_SECRET}"
    tokenUrl: "https://auth.pragma.com.co/oauth/token"
    scopes:
      - "read:v2"
      - "write:v2"
      - "read:v3"
      - "write:v3"

# Configuración de rate limiting estricta por versión
rateLimiting:
  v1:
    requestsPerMinute: 30
    burst: 5
    
  v2:
    requestsPerMinute: 1000
    burst: 100
    
  v3:
    requestsPerMinute: 100
    burst: 15

# Políticas de versionamiento estrictas para producción
versioningPolicies:
  deprecation:
    warnAfter: "2025-03-01"
    blockAfter: "2025-06-30"
    migrationGuideUrl: "https://docs.pragma.com.co/migration/v1-to-v2"
    supportContact: "soporte@pragma.com.co"
    
  backwardCompatibility:
    v1ToV2:
      breakingChanges: ["response_format", "field_renamed", "status_codes"]
      migrationRequired: true
      migrationDeadline: "2025-06-30"
    v2ToV3:
      breakingChanges: []
      migrationRequired: false

# Configuración de logging en producción
logging:
  level: "info"
  includeHeaders: true
  includeBody: false
  maskSensitiveData: true
  auditEnabled: true

# Configuración de circuit breaker para producción
circuitBreaker:
  enabled: true
  failureThreshold: 3
  timeout: 10000
  resetTimeout: 60000

# Configuración de despliegues inmutables
immutableDeployment:
  enabled: true
  versionTagRequired: true
  rollbackEnabled: true
  blueGreenDeployment: true
  canaryPercentage: 10

// === ARCHIVO: tests/versioning_contract_test.postman_collection.json ===
{
  "info": {
    "name": "API Versioning Contract Tests",
    "description": "Colección de pruebas para validar el contrato de versionamiento de APIs y escenarios de conflicto. Esta colección verifica que el versionamiento mediante headers Accept funciona correctamente, que las políticas de deprecación se aplican, y que los escenarios de conflicto entre versiones se manejan apropiadamente.",
    "schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"
  },
  "variable": [
    {
      "key": "baseUrl",
      "value": "{{baseUrl}}",
      "type": "string"
    },
    {
      "key": "apiKey",
      "value": "{{apiKey}}",
      "type": "string"
    },
    {
      "key": "oauthToken",
      "value": "{{oauthToken}}",
      "type": "string"
    }
  ],
  "event": [
    {
      "listen": "prerequest",
      "script": {
        "type": "javascript",
        "exec": [
          "// Pre-request script para configurar headers de versionamiento",
          "if (!pm.variables.get('oauthToken')) {",
          "    pm.variables.set('oauthToken', 'placeholder-token');",
          "}"
        ]
      }
    },
    {
      "listen": "test",
      "script": {
        "type": "javascript",
        "exec": [
          "// Tests comunes para todas las requests",
          "pm.test('Response time is acceptable', function() {",
          "    pm.expect(pm.response.responseTime).to.be.below(1000);",
          "});"
        ]
      }
    }
  ],
  "item": [
    {
      "name": "Versionamiento mediante Header Accept",
      "item": [
        {
          "name": "Request a v1 con header Accept válido",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe responder con formato v1', function() {",
                  "    pm.expect(pm.response.headers.get('Content-Type')).to.include('application/vnd.pragma.v1+json');",
                  "});",
                  "pm.test('Debe incluir header de versión en response', function() {",
                  "    pm.expect(pm.response.headers.has('X-API-Version')).to.be.true;",
                  "});",
                  "pm.test('Status code debe ser 200', function() {",
                  "    pm.expect(pm.response.status).to.equal('OK');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v1+json",
                "type": "text"
              },
              {
                "key": "Authorization",
                "value": "Bearer {{oauthToken}}",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v1/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v1", "resources"]
            }
          },
          "response": []
        },
        {
          "name": "Request a v2 con header Accept válido",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe responder con formato v2', function() {",
                  "    pm.expect(pm.response.headers.get('Content-Type')).to.include('application/vnd.pragma.v2+json');",
                  "});",
                  "pm.test('Debe incluir versión en header X-API-Version', function() {",
                  "    pm.expect(pm.response.headers.get('X-API-Version')).to.equal('v2');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v2+json",
                "type": "text"
              },
              {
                "key": "Authorization",
                "value": "Bearer {{oauthToken}}",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v2/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v2", "resources"]
            }
          },
          "response": []
        },
        {
          "name": "Request con versión inexistente - 404",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe retornar 404 para versión inexistente', function() {",
                  "    pm.expect(pm.response.status).to.equal('Not Found');",
                  "});",
                  "pm.test('Debe incluir mensaje de error claro', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.error).to.exist;",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v99+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v99/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v99", "resources"]
            }
          },
          "response": []
        }
      ]
    },
    {
      "name": "Políticas de Deprecación",
      "item": [
        {
          "name": "Request a versión deprecated debe retornar warning",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe incluir header deprecation warning', function() {",
                  "    pm.expect(pm.response.headers.has('Deprecation')).to.be.true;",
                  "});",
                  "pm.test('Debe incluir link a documentación de migración', function() {",
                  "    var linkHeader = pm.response.headers.get('Link');",
                  "    pm.expect(linkHeader).to.include('migration');",
                  "});",
                  "pm.test('Status code sigue siendo 200', function() {",
                  "    pm.expect(pm.response.status).to.equal('OK');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v1+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v1/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v1", "resources"]
            }
          },
          "response": []
        },
        {
          "name": "Request después de fecha de sunset debe retornar 410",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe retornar 410 Gone para versión eliminada', function() {",
                  "    pm.expect(pm.response.status).to.equal('Gone');",
                  "});",
                  "pm.test('Debe incluir información de migración', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.migrationGuide).to.exist;",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v0+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v0/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v0", "resources"]
            }
          },
          "response": []
        }
      ]
    },
    {
      "name": "Escenarios de Conflicto de Versionamiento",
      "item": [
        {
          "name": "Conflicto: Path version vs Header Accept",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe preferir header Accept sobre path', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.resolvedVersion).to.equal('v2');",
                  "});",
                  "pm.test('Debe incluir warning sobre conflicto', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.warnings).to.include('version_conflict');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v2+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v1/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v1", "resources"]
            }
          },
          "response": []
        },
        {
          "name": "Conflicto: Múltiples versiones en Accept header",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe retornar 400 para Accept header inválido', function() {",
                  "    pm.expect(pm.response.status).to.equal('Bad Request');",
                  "});",
                  "pm.test('Debe explicar el error de versión', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.error).to.include('version');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v1+json, application/vnd.pragma.v2+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v2/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v2", "resources"]
            }
          },
          "response": []
        }
      ]
    },
    {
      "name": "Autenticación y Versionamiento",
      "item": [
        {
          "name": "Request sin autenticación debe retornar 401",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe retornar 401 para request no autenticado', function() {",
                  "    pm.expect(pm.response.status).to.equal('Unauthorized');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v2+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v2/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v2", "resources"]
            }
          },
          "response": []
        },
        {
          "name": "Request con scope incorrecto para versión",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe retornar 403 para scope insuficiente', function() {",
                  "    pm.expect(pm.response.status).to.equal('Forbidden');",
                  "});",
                  "pm.test('Debe indicar qué scope falta', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.requiredScope).to.equal('write:v3');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "POST",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v3+json",
                "type": "text"
              },
              {
                "key": "Authorization",
                "value": "Bearer {{oauthToken}}",
                "type": "text"
              },
              {
                "key": "Content-Type",
                "value": "application/json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v3/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v3", "resources"]
            },
            "body": {
              "mode": "raw",
              "raw": "{\"name\": \"test\"}"
            }
          },
          "response": []
        }
      ]
    },
    {
      "name": "Rate Limiting por Versión",
      "item": [
        {
          "name": "Exceder rate limit debe retornar 429",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('Debe retornar 429 cuando se excede el límite', function() {",
                  "    pm.expect(pm.response.status).to.equal('Too Many Requests');",
                  "});",
                  "pm.test('Debe incluir header Retry-After', function() {",
                  "    pm.expect(pm.response.headers.has('Retry-After')).to.be.true;",
                  "});",
                  "pm.test('Debe incluir información de rate limit', function() {",
                  "    pm.expect(pm.response.headers.has('X-RateLimit-Remaining')).to.be.true;",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v1+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v1/resources?simulate_rate_limit=true",
              "host": ["{{baseUrl}}"],
              "path": ["v1", "resources"],
              "query": [
                {
                  "key": "simulate_rate_limit",
                  "value": "true"
                }
              ]
            }
          },
          "response": []
        }
      ]
    },
    {
      "name": "Contrato de Respuesta por Versión",
      "item": [
        {
          "name": "v1 debe tener estructura de respuesta específica",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('v1 debe tener campo legacyId', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.data[0]).to.have.property('legacyId');",
                  "});",
                  "pm.test('v1 no debe tener campo metadata', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.data[0]).to.not.have.property('metadata');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v1+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v1/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v1", "resources"]
            }
          },
          "response": []
        },
        {
          "name": "v2 debe tener estructura de respuesta con metadata",
          "event": [
            {
              "listen": "test",
              "script": {
                "type": "javascript",
                "exec": [
                  "pm.test('v2 debe tener campo id y metadata', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.data[0]).to.have.property('id');",
                  "    pm.expect(jsonData.data[0]).to.have.property('metadata');",
                  "});",
                  "pm.test('v2 debe incluir timestamp de versión', function() {",
                  "    var jsonData = pm.response.json();",
                  "    pm.expect(jsonData.data[0].metadata).to.have.property('version');",
                  "});"
                ]
              }
            }
          ],
          "request": {
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "application/vnd.pragma.v2+json",
                "type": "text"
              }
            ],
            "url": {
              "raw": "{{baseUrl}}/v2/resources",
              "host": ["{{baseUrl}}"],
              "path": ["v2", "resources"]
            }
          },
          "response": []
        }
      ]
    }
  ]
}

// === ARCHIVO: docs/guia_repositorios_locales_remotos.md ===
# Guía de Repositorios Locales y Remotos en Git

## Introducción al Ecosistema Git

Git opera bajo un modelo distribuido donde cada clon del repositorio contiene el historial completo del proyecto. Esta arquitectura permite работу desconectada mientras se mantiene la capacidad de sincronizar cambios con otros colaboradores. Comprender la distinción entre repositorios locales y remotos es fundamental para gestionar el flujo de código de manera efectiva en equipos distribuidos.

El repositorio local reside en la máquina del desarrollador y contiene tres áreas principales: el directorio de trabajo (working directory), el área de preparación (staging/index) y la base de datos de objetos (commit history). El repositorio remoto, en contraste, es una versión compartida del proyecto alojada en un servidor que sirve como punto central de colaboración para todo el equipo.

## Estructura del Repositorio Local

El repositorio local de Git se estructura en capas que el desarrollador manipula directamente. El directorio de trabajo contiene los archivos del proyecto en su estado actual, permitiendo edición inmediata. El área de preparación actúa como zona intermedia donde se seleccionan los cambios que formarán parte del próximo commit. La base de datos de objetos almacena todo el historial de commits, ramas y etiquetas de manera eficiente mediante contenido direccionado.

Cada clon local incluye la carpeta `.git` que contiene toda esta información. Los comandos fundamentales del flujo local incluyen `git init` para inicializar un nuevo repositorio, `git add` para mover cambios al área de preparación, `git commit` para confirmar cambios en el historial local, y `git status` para visualizar el estado actual de los archivos.

## Repositorios Remotos y su Función

Un repositorio remoto en Git es simplemente otro clon del proyecto accesible a través de un protocolo de red. Los servidores remotos más comunes incluyen GitHub, GitLab, Bitbucket y servicios empresariales como Azure DevOps. Cada remoto tiene un nombre convencional: `origin` representa el repositorio principal del cual se realizó el clon inicial.

La gestión de remotos se realiza mediante comandos específicos. `git remote -v` lista todos los remotos configurados con sus URLs. `git remote add nombre url` agrega un nuevo remoto al repositorio local. `git remote remove nombre` elimina un remoto existente. `git remote rename nombre-antiguo nombre-nuevo` cambia el nombre de un remoto.

La sincronización entre local y remoto sigue un patrón bidireccional. Para obtener cambios del remoto se utiliza `git fetch`, que descarga objetos y referencias del remoto sin fusionarlos automáticamente. Para incorporar esos cambios al branch actual se ejecuta `git merge` o `git rebase`. El comando combinado `git pull` ejecuta fetch y merge en una sola operación, aunque su uso requiere comprensión de sus efectos.

## Sincronización y Flujo de Trabajo

El flujo de sincronización típico comienza con `git fetch origin` para obtener los últimos cambios del remoto sin modificar el código local. Después de revisar los cambios con `git log origin/main`, el desarrollador decide cómo integrarlos. Si el branch local está listo para publicar, `git push origin main` envía los commits locales al remoto.

La sincronización efectiva requiere disciplina en ciertos puntos del flujo de trabajo. Antes de iniciar trabajo local fresco, siempre es recomendable ejecutar `git pull` para asegurar que el código base está actualizado. Antes de hacer push, verificar que no existan cambios pendientes en el remoto que pudieran sobrescribirse. Usar `git fetch` regularmente mantiene el repositorio local al día con el estado real del remoto.

Problemas comunes surgen cuando se trabaja sin sincronizar adecuadamente. Hacer push de un branch que está detrás del remoto genera conflictos que deben resolverse. Realizar cambios sobre código obsoleto crea situaciones donde el merge posterior se vuelve complejo. Ignorar los cambios del remoto mientras otros desarrolladores trabajan en el mismo código genera divergencia que eventualmente requiere intervención manual.

## Gestión de Múltiples Remotos

Proyectos complejos pueden requerir múltiples repositorios remotos. Un escenario típico involucra un remoto principal (origin) para colaboración interna y un upstream para contribuciones a proyectos de código abierto. La configuración de múltiples remotos permite separar flujos de trabajo: el remoto principal recibe los cambios propios del equipo, mientras que el upstream proporciona acceso al código base original para mantener sincronización con la comunidad.

Para agregar un remoto adicional, por ejemplo upstream de un fork, se utiliza `git remote add upstream https://github.com/proyecto/original.git`. Mantener actualizado el fork requiere ejecutar `git fetch upstream` seguido de `git merge upstream/main` para integrar los cambios del proyecto original al branch local.

## Resolución de Problemas de Sincarnación

El error "rejected" al hacer push indica que el remoto tiene cambios que no existen en el local. La solución más común es hacer pull del remoto, resolver cualquier conflicto, y luego intentar el push nuevamente. El flujo completo sería: `git pull --rebase origin main`, resolver conflictos si existen, y luego `git push origin main`.

El error "fetch first" ocurre cuando el remoto tiene commits que no están presentes localmente. Nunca se debe hacer force push a ramas compartidas, ya que sobrescribiría el trabajo de otros. La práctica correcta es obtener los cambios, integrarlos apropiadamente, y luego publicar la versión combinada.

Cuando el historial local diverge significativamente del remoto, Git refusará el push directo. En tales casos, se requiere un merge explícito o un rebase para reconciliar los historiales. El merge crea un commit de fusión que combina ambas líneas de desarrollo, mientras que rebase aplica los commits locales sobre el historial del remoto, creando un historial lineal más limpio.

## Mejores Prácticas para Sincronización

Mantener un historial limpio requiere adherirse a prácticas consistentes. Fetch regularmente, al menos al inicio de cada sesión de trabajo. Pull con rebase en lugar de merge para mantener un historial lineal en branches de características. Push frecuentemente para evitar acumulación de cambios locales que podrían divergir significativamente del código base compartido.

Utilizar ramas de características aisladas reduce los conflictos de sincronización. Cada feature branch debe derivar de la rama principal actualizada antes de iniciar el desarrollo. Antes de merges a ramas principales, verificar que el branch está actualizado con el último código del destino.

La comunicación con el equipo es crucial cuando se trabaja en archivos compartidos. Notificar antes de realizar cambios significativos en archivos que otros podrían estar modificando reduce la probabilidad de conflictos inesperados y facilita la coordinación del trabajo paralelo.

// === ARCHIVO: docs/procedimiento_resolucion_conflictos.md ===
# Procedimiento para Resolver Conflictos de Merge en Git

## Fundamentos de los Conflictos en Git

Un conflicto de merge ocurre cuando Git no puede fusionar automáticamente dos ramas debido a cambios incompatibles en las mismas líneas de código o archivos. Esta situación es normal en equipos que trabajan en paralelo y representa una oportunidad para que el desarrollador controle explícitamente cómo se combinan los cambios. Git detecta conflictos cuando las modificaciones en ambas ramas afectan las mismas secciones de un archivo y no existe una estrategia automática para resolver la diferencia.

El proceso de resolución de conflictos requiere comprensión del estado actual del código, los cambios entrantes y el código base original. Git marca las áreas en conflicto dentro de los archivos afectados, permitiendo al desarrollador evaluar cada situación y decidir qué versión mantener, cómo combinarlas, o si se requiere una solución completamente nueva.

## Detección e Identificación de Conflictos

Cuando un merge o rebase encuentra conflictos, Git aborta la operación y muestra un mensaje indicando qué archivos tienen conflictos. El comando `git status` revela el estado del repositorio, mostrando los archivos en estado "unmerged" con indicadores visuales. Cada archivo conflictivo contiene marcas especiales que delimitan las diferentes versiones.

Las marcas de conflicto siguen un formato específico: `<<<<<<< HEAD` indica el inicio de las modificaciones de la rama actual, `=======` separa las dos versiones, y `>>>>>>> nombre-rama` marca el fin de los cambios entrantes. Entre estas marcas aparece el contenido de cada versión, permitiendo identificar exactamente qué difiere entre ambas ramas.

Para conflictos complejos en múltiples archivos, el comando `git diff --name-only --diff-filter=U` lista únicamente los archivos con conflictos sin procesar. Esta información resulta útil para planificar la resolución de manera sistemática, especialmente cuando hay numerosos archivos afectados.

## Procedimiento Paso a Paso para Resolución

**Paso 1: Detener el merge si está en progreso.** Si el conflicto ocurrió durante un merge activo, Git ya ha detenido la operación. Para rebase, la operación también se detiene automáticamente. No intentar continuar sin resolver primero los conflictos, ya que esto dejaría el repositorio en un estado inconsistente.

**Paso 2: Analizar los conflictos identificados.** Ejecutar `git status` para ver la lista completa de archivos con conflictos. Para cada archivo, examinar las marcas de conflicto y entender qué cambios provienen de cada rama. El comando `git diff` entre las dos ramas puede ejecutarse antes de resolver para visualizar las diferencias completas: `git diff rama1...rama2`.

**Paso 3: Editar cada archivo conflictivo.** Abrir los archivos marcados y decidir para cada conflicto cuál versión usar. Las opciones incluyen: mantener la versión de HEAD (rama actual), mantener la versión entrante, combinar ambas manualmente, o escribir una nueva versión que incorpore elementos de ambas según sea necesario. Eliminar las marcas de conflicto `<<<<<<<`, `=======`, y `>>>>>>>` una vez tomada la decisión.

**Paso 4: Agregar los archivos resueltos.** Después de editar cada archivo conflictivo, marcarlo como resuelto mediante `git add nombre-archivo`. Este comando indica a Git que el archivo ha sido procesamiento y está listo para ser incluido en el merge. Para agregar todos los archivos resueltos simultáneamente, usar `git add .` después de haber procesado cada uno.

**Paso 5: Completar el merge o continuar el rebase.** Una vez resueltos todos los conflictos y agregados los archivos, ejecutar `git commit` para completar el merge. Git abrirá el editor de texto para el mensaje de commit, que por defecto describe la operación de merge. Guardar y cerrar para finalizar. En caso de rebase, ejecutar `git rebase --continue` para aplicar el siguiente commit del proceso.

## Ejemplo Práctico de Resolución

Considérese un escenario donde dos desarrolladores modifican simultáneamente el archivo `configuracion.json`. El desarrollador A añade un nuevo entorno de producción en la rama `feature/produccion`, mientras el desarrollador B actualiza credenciales en la rama `fix/credenciales`. Al hacer merge de ambas ramas a main, Git detecta conflicto.

El archivo conflictivo mostraría:
```
{
  "desarrollo": {
    "url": "http://localhost:3000"
  },
<<<<<<< HEAD
  "produccion": {
    "url": "https://prod.miempresa.com",
    "tier": "premium"
  },
=======
  "produccion": {
    "url": "https://miempresa.com"
  },
>>>>>>> fix/credenciales
}
```

La resolución requiere evaluar ambas propuestas. Si la versión de HEAD tiene la configuración más completa, mantenerla eliminando las líneas de la versión entrante. Si la versión entrante tiene información valiosa (como la URL actualizada), incorporarla. En este caso, la mejor solución probablemente combine ambas: la URL de una versión con el tier de otra, resultando en:
```
{
  "desarrollo": {
    "url": "http://localhost:3000"
  },
  "produccion": {
    "url": "https://prod.miempresa.com",
    "tier": "premium"
  }
}
```

## Estrategias Avanzadas de Resolución

**Abortar y reconsiderar.** Si los conflictos son excesivamente complejos o existe incertidumbre, `git merge --abort` (para merge) o `git rebase --abort` (para rebase) revierte el proceso completamente. Esta opción permite analizar mejor la situación, discutir con el equipo, o buscar ayuda antes de proceder.

**Usar herramientas visuales.** Herramientas como VSCode, IntelliJ, GitKraken o Meld proporcionan interfaces visuales para resolver conflictos mostrando las diferencias lado a lado. Estas herramientas facilitan la identificación de cambios y permiten selección gráfica entre versiones. Configurar la herramienta preferida con `git config merge.tool nombre-herramienta`.

**Resolver durante el checkout.** Para conflictos en archivos específicos, `git checkout --conflict=merge archivo` regenera las marcas de conflicto si se necesita verlas nuevamente. El comando `git checkout --ours archivo` selecciona automáticamente la versión de la rama actual, mientras `git checkout --theirs archivo` selecciona la versión entrante. Estas opciones son útiles cuando se sabe con certeza qué versión adoptar.

## Prevención de Conflictos Frecuentes

La prevención de conflictos reduce el tiempo dedicado a su resolución. Comunicar activamente con el equipo sobre qué archivos se están modificando evita trabajo paralelo en los mismos archivos. Hacer fetch y pull regularmente mantiene el código local actualizado, reduciendo la divergencia con el trabajo de otros desarrolladores.

Trabajar en ramas de corta duración reduce la ventana de tiempo donde pueden surgir conflictos. Mergear frecuentemente la rama principal a la rama de feature mantiene el código actualizado y permite resolver conflictos menores de manera incremental en lugar de enfrentar múltiples conflictos acumulados.

Dividir archivos grandes en módulos independientes reduce la probabilidad de que múltiples desarrolladores modifiquen las mismas líneas simultáneamente. Establecer convenciones de equipo sobre estructura de archivos y responsabilidades claras facilita la coordinación.

## Manejo de Conflictos en Diferentes Escenarios

**Conflictos en archivos binarios.** Git no puede fusionar archivos binarios automáticamente. La solución típica es elegir una versión completa (la nuestra o la entrante) mediante `git checkout --ours archivo.bin` o `git checkout --theirs archivo.bin`, luego agregar el archivo seleccionado.

**Conflictos en renombrados.** Cuando Git detecta que un archivo fue renombrado en una rama y modificado en otra, puede resultar en conflictos aparentemente extraños. Usar `git diff` con la opción `--name-status` ayuda a entender qué archivos están involucrados.

**Conflictos en submodules.** Los submodules requieren sincronización independiente después de resolver conflictos en el repositorio principal. Ejecutar `git submodule update --init --recursive` después del merge asegura que los submodules estén en el estado correcto.

// === ARCHIVO: docs/conceptos_control_versiones.md ===
# Conceptos Fundamentales de Control de Versiones

## Naturaleza y Propósito del Control de Versiones

El control de versiones es un sistema que registra cambios en archivos a lo largo del tiempo, permitiendo recuperar versiones específicas, comparar modificaciones entre estados, y colaborar eficientemente entre múltiples contribuyentes. En el contexto de desarrollo de software moderno, representa la columna vertebral de la coordinación de equipos, la trazabilidad del código, y la gestión del ciclo de vida del software.

Git, el sistema de control de versiones más utilizado actualmente, implementa un modelo distribuido donde cada desarrollador tiene una copia completa del repositorio, incluyendo todo el historial. Este diseño proporciona resiliencia ante fallos de servidor, permite trabajo offline, y ofrece operaciones locales extremadamente rápidas.

La arquitectura de Git se fundamenta en snapshots en lugar de diferencias. Cada commit representa una instantánea completa del proyecto en un momento dado, no un conjunto de parches. Esta aproximación, aunque consume más espacio inicial, proporciona rendimiento superior al recuperar cualquier versión del historial.

## Modelo de Datos y Estructura Interna

El modelo de datos de Git se construye sobre tres tipos principales de objetos. Los blobs (binary large objects) almacenan el contenido de cada archivo. Los trees representan directorios, conteniendo referencias a blobs y otros trees. Los commits apuntan a un tree específico e incluyen metadatos como autor, mensaje, y referencias a commits padre.

Cada objeto en Git se identifica mediante un hash SHA-1 de 40 caracteres, proporcionando integridad criptográfica. Este contenido direccionamiento significa que git determina si dos archivos son idénticos comparando sus hashes, sin necesidad de extensiones de archivo.

Las referencias (refs) son punteros nombrados a commits específicos. Las ramas (branches) son referencias móviles que avanzan automáticamente con cada nuevo commit. Las etiquetas (tags) son referencias fijas típicamente usadas para marcar versionesRelease específicas. La referencia especial HEAD indica el commit actualmente desprotegido.

## Ramas en Git: Tipos y Propósito

Las ramas en Git son punteros ligeros móviles hacia commits específicos. Crear una rama crea una nueva referencia que puede moverse independientemente de otras ramas. Esta operación es extremadamente económica en términos de recursos, ya que solo crea un archivo de texto con el hash del commit.

**Ramas de característica (feature branches)** encapsulan nueva funcionalidad sin afectar el código estable. Cada feature branch deriva de una rama base (típicamente main o develop) y, una vez completada y revisada, se fusiona de vuelta a la rama base. Esta práctica aísla trabajo en progreso y permite desarrollo paralelo sin interferencia.

**Ramas de soporte (hotfix branches)** abordan problemas críticos en producción. Se crean desde la rama de producción, permiten corrección urgente sin contaminar el desarrollo activo, y se fusionan tanto a producción como a la rama de desarrollo principal una vez completada la corrección.

**Ramas de release** preparation el código para un nuevo despliegue. Permiten estabilización final, corrección de bugs menores, y actualización de metadatos de versión sin afectar el desarrollo activo de nuevas características.

## Ramas Inmutables y Modelos de Despliegue

Las ramas inmutables son referencias que una vez creadas nunca se modifican. Su contenido permanece fijo, proporcionando un punto de referencia estable y reproducible. En modelos de despliegue modernos, estas ramas representan estados deployables del sistema.

El modelo de **GitFlow** utiliza ramas inmutables para releases. La rama `main` contiene exclusivamente commits de release, cada uno representando una versión deployable. La rama `develop` integra características completadas. Las ramas `release-*` y `hotfix-*` son temporales pero sus resultados se consolidan como commits inmutables en main.

**Trunk-Based Development** representa una aproximación más simple donde los desarrolladores trabajan directamente en la rama principal o en ramas de vida muy corta (menos de dos días). Las ramas de característica pueden existir pero típicamente se mergean diariamente. Este modelo enfatiza integración continua y reduce la complejidad de gestión de ramas.

La elección entre GitFlow y trunk-based development depende del contexto del equipo. GitFlow ofrece estructura clara para equipos con ciclos de release definidos y necesidad de múltiples versiones simultáneas. Trunk-based suits equipos que priorizan velocidad de integración y tienen capacidades robustas de testing y deployment continuo.

## Estrategias de Ramificación por Contexto

**Para equipos pequeños (menos de 5 desarrolladores):** trunk-based development con ramas de característica de corta duración minimiza overhead administrativo. Todos los desarrolladores pueden trabajar directamente en main con feature flags para ocultar funcionalidad incompleta. La integración continua valida que el código siempre permanece en estado deployable.

**Para equipos medianos (5-15 desarrolladores):** combinación de GitFlow simplificado con protección de ramas principales. La rama main requiere pull requests y verificación automática. Las ramas de feature se crean desde main, se desarrollan, y se mergean mediante PRs que requieren aprobación y tests passing.

**Para equipos grandes (más de 15 desarrolladores):** estructura de GitFlow completa con roles claramente definidos. Ramas de release paralelas para diferentes líneas de producto. Políticas de protección estrictas en main y develop. Integración obligatoria de herramientas de análisis de código estático y revisión obligatoria por pares.

## Conceptos de Despliegue y Versionado

El versionado semántico (semver) proporciona un sistema consistente para numerar versiones. El formato MAJOR.MINOR.PATCH indica: cambios incompatibles en la API (MAJOR), funcionalidad nueva兼容ibilty hacia atrás (MINOR), correcciones de bugs compatibilty hacia atrás (PATCH). Esta convención permite a los consumidores de una biblioteca entender el impacto de actualizar.

Los tags de Git implementan versionado semántico en el repositorio. Crear un tag con `git tag -a v1.2.3 -m "Versión 1.2.3"` marca el commit actual como una versión específica. Los tags pueden ser ligera (simple referencia) o anotados (incluyen metadata extendido).

El versionado de APIs requiere consideraciones adicionales. Mantener múltiples versiones activas simultáneamente (v1, v2, v3) permite migración gradual de consumidores. Las estrategias incluyen versionado en URL (/v1/resource), versionado en header (Accept: application/vnd.api.v1+json), y versionado mediante query parameter (?version=1).

## Integración con Pipeline de Despliegue

Los pipelines de CI/CD aprovechan el control de versiones para automatización. Cada push a una rama puede activar ejecución de tests, análisis estático, y construcción de artefactos. Los tags en branches específicos (main tras merge de release) disparan despliegues a producción.

La configuración de pipelines típicamente incluye etapas de: checkout del código (usando la referencia del commit o tag), instalación de dependencias, ejecución de tests unitarios, análisis de código, construcción de artefactos, y despliegue a entornos sucesivos (dev, staging, producción).

Protección de ramas principales mediante pull requests previene deployments accidentales de código no revisado. Las reglas de protección pueden requerir: revisiones obligatorias, tests passing, análisis de seguridad passing, y restricción de force push.

## Conceptos Avanzados y Patrones de Colaboración

**Cherry-picking** permite aplicar commits específicos de una rama a otra sin fusionar toda la rama. Útil para aplicar hotfixes selectivos o migrar cambios específicos entre líneas de desarrollo.

**Rebasing** reescribe el historial de commits aplicando la serie de commits sobre otra base. Proporciona un historial lineal limpio pero requiere precaución en ramas compartidas. El rebase interactivo (`git rebase -i`) permite modificar, combinar, o eliminar commits durante el proceso.

**Git worktrees** permiten tener múltiples copias de trabajo del mismo repositorio en diferentes directorios. Facilita trabajar en múltiples ramas simultáneamente sin cambiar de directorio o hacer stash de cambios.

**Git hooks** son scripts que se ejecutan automáticamente en respuesta a eventos de Git. Permiten automatizar verificaciones (tests, linting), enforce políticas (mensajes de commit, protección de ramas), y notificaciones. Se localizan en `.git/hooks` y pueden ser locales o de servidor (a través de plataformas como GitHub o GitLab).


// === ARCHIVO: README.md ===
# API Versioning Gateway

Proyecto de gestión de versionamiento de APIs utilizando un enfoque API First con políticas de gateway. Este repositorio contiene el contrato OpenAPI, políticas de versionamiento, configuración por ambiente y tests de contrato para garantizar la integridad del versionamiento de APIs.

## Estructura del Proyecto

```
api-versioning-gateway/
├── openapi/
│   └── openapi.yaml          # Contrato principal de la API (OpenAPI 3.1)
├── policies/
│   ├── versioning_policy.yaml      # Políticas de versionamiento del gateway
│   └── conflict_resolution_policy.yaml  # Políticas de resolución de conflictos
├── environments/
│   ├── dev.yaml             # Configuración del entorno de desarrollo
│   └── prod.yaml            # Configuración del entorno de producción
├── tests/
│   └── versioning_contract_test.postman_collection.json  # Tests de contrato
├── docs/
│   ├── aplicacion_gitflow_trunkbased.md  # Comparativa de estrategias de despleigue
│   ├── guia_repositorios_locales_remotos.md
│   ├── procedimiento_resolucion_conflictos.md
│   └── conceptos_control_versiones.md
├── package.json
└── README.md
```

## Requisitos Previos

- Node.js versión 16.0.0 o superior
- npm (incluido con Node.js)
- Redocly CLI (se instala automáticamente con `npm install`)

## Instalación

Para instalar las dependencias del proyecto, ejecuta:

```bash
npm install
```

Este comando installará automáticamente Redocly CLI como dependencia de desarrollo, que es necesario para validar el contrato OpenAPI.

## Validación del Contrato OpenAPI

El proyecto utiliza Redocly CLI para validar que el contrato OpenAPI cumple con las especificaciones y buenas prácticas. Para ejecutar la validación:

```bash
npm run lint
```

Este comando es un alias para `npx @redocly/cli lint openapi/openapi.yaml` y verificará:

- Sintaxis válida del documento OpenAPI
- Referencias correctas entre componentes
- Cumplimiento de las políticas de versionamiento definidas
- Esquemas de respuesta coherentes

## Tests y Validación de Versionamiento

### Ejecución de Tests de Contrato

Los tests de contrato se encuentran en `tests/versioning_contract_test.postman_collection.json`. Para ejecutarlos:

1. Importa la colección en Postman
2. Configura las variables de entorno según el ambiente (dev o prod)
3. Ejecuta la colección completa

Los tests validan los siguientes escenarios:

- Routing correcto basado en headers de versión
- Respuestas apropiadas para versiones no soportadas
- Manejo de conflictos de versionamiento
- Consistencia entre versiones activas

### Validación del Contrato de Versionamiento

El contrato de versionamiento define las siguientes reglas:

1. **Versionado por URL**: Cada versión mayor tiene su propio path (ej. `/v1/resource`, `/v2/resource`)
2. **Headers de versión**: Soporte para header `Accept` con media type versionado
3. **Cabeceras de respuesta**: Cada respuesta incluye `API-Version` en headers
4. **Deprecación**: Las versiones obsoletas incluyen header `Sunset` y `Deprecation`

Para verificar que el contrato cumple con estas reglas, ejecuta:

```bash
npm run validate
```

## Configuración por Entorno

### Desarrollo (dev.yaml)

El entorno de desarrollo está configurado para apuntar a servicios de staging con logs detallados. Para использовать este entorno:

```bash
# Los valores se cargan automáticamente desde environments/dev.yaml
```

### Producción (prod.yaml)

El entorno de producción apunta a los servicios finales con configuración optimizada para rendimiento. Para использовать este entorno:

```bash
# Los valores se cargan automáticamente desde environments/prod.yaml
```

## Políticas del Gateway

### Versioning Policy

Define las reglas para el routing de versiones:

- Patrones de URL permitidos por versión
- Headers obligatorios por versión
- Tiempos de respuesta esperados
- Límites de tasa por versión

### Conflict Resolution Policy

Establece el procedimiento para resolver conflictos entre versiones:

- Detección de conflictos de schema
- Estrategia de merge para cambios no rompedores
- Procedimiento para cambios rompedores

## Contribución

Para contribuir al proyecto:

1. Crea un branch feature desde `main`
2. Realiza tus cambios siguiendo las convenciones del proyecto
3. Ejecuta `npm run lint` para validar el contrato
4. Ejecuta los tests de Postman para verificar funcionalidad
5. Crea un pull request para revisión

## Licencia

MIT License - Pragma S.A.

## Recursos Adicionales

- [Documentación de OpenAPI 3.1](https://spec.openapis.org/oas/v3.1.0)
- [Redocly CLI Documentation](https://redocly.com/docs/cli/)
- [Guía de versionamiento de APIs](https://swagger.io/blog/api-versioning-with-openapi/)

// === ARCHIVO: docs/aplicacion_gitflow_trunkbased.md ===
# Aplicación de GitFlow y Trunk-Based Development en Proyectos Reales

## Introducción

El versionamiento efectivo del código fuente es fundamental para equipos que trabajan en sistemas distribuidos y arquitecturas SOA. Dos enfoques predominantes han emergido como estándares de la industria: GitFlow y Trunk-Based Development. Este documento proporciona una guía práctica para evaluar, seleccionar e implementar cada enfoque en proyectos reales, considerando las características específicas del ecosistema de integración y gestión de APIs.

## GitFlow: El Flujo Basado en Ramas de Largo Plazo

### Conceptos Fundamentales

GitFlow es un modelo de ramificación que utiliza múltiples ramas de larga duración para organizar el flujo de trabajo. Las ramas principales incluyen:

- **main/master**: Rama principal que contiene el código en producción. Solo acepta merges de otras ramas y representa el historial oficial del proyecto.
- **develop**: Rama de integración que contiene el código para la próxima liberación. Funciona como rama base para las características nuevas.

Las ramas auxiliares incluyen:

- **feature/*** : Ramas temporales para desarrollar nuevas funcionalidades. Se crean desde `develop` y se merguean de vuelta a `develop`.
- **release/*** : Ramas de preparación para una liberación específica. Permiten ajustes finales sin afectar el desarrollo activo.
- **hotfix/*** : Ramas para correcciones urgentes en producción. Se crean desde `main` y se merguean tanto a `main` como a `develop`.

### Implementación Práctica

Para iniciar GitFlow en un proyecto, primero se inicializa el repositorio con la rama principal y la rama de desarrollo:

```bash
# Inicializar repositorio
git init
git add README.md
git commit -m "Initial commit"

# Crear rama develop
git checkout -b develop
git push -u origin develop
```

El flujo de trabajo diario implica crear ramas de feature desde develop, trabajar en ellas, y merguearlas de vuelta:

```bash
# Crear nueva feature
git checkout develop
git checkout -b feature/nueva-funcionalidad

# Trabajar y commitear
git add .
git commit -m "Implementa nueva funcionalidad"

# Mergear a develop
git checkout develop
git merge feature/nueva-funcionalidad
git push origin develop

# Eliminar rama de feature
git branch -d feature/nueva-funcionalidad
```

### Pros de GitFlow

1. **Historial claro**: La estructura de ramas proporciona una visualización inmediata del estado del proyecto y las líneas de trabajo paralelas.
2. **Separación rigurosa**: Mantiene código de producción (main) completamente separado del código en desarrollo (develop).
3. **Soporte para release trains**: Ideal para equipos que liberan en ciclos fijos (mensuales, trimestrales) con múltiples versiones simultáneas.
4. **Facilita compliance**: En entornos regulados, la rama main funciona como auditoría inmutable del código productivo.
5. **Gestión de hotfixes**: Proporciona un camino claro y controlado para corregir errores críticos sin interrumpir el desarrollo activo.

### Contras de GitFlow

1. **Complejidad operativa**: Requiere disciplina del equipo para gestionar múltiples tipos de ramas y recordar cuándo usar cada una.
2. **Integración continua limitada**: El código pasa períodos prolongados en ramas aisladas, aumentando el riesgo de conflictos tardíos.
3. **Overhead para proyectos pequeños**: La sobrecarga administrativa no se justifica en equipos pequeños o proyectos con despliegues continuos.
4. **Merge hell**: Ramas de larga duración que no se sincronizan regularmente con develop generan conflictos complejos de resolver.

## Trunk-Based Development: Integración Continua en la Rama Principal

### Conceptos Fundamentales

Trunk-Based Development (TBD) es un enfoque donde los desarrolladores trabajan en ramas de corta duración (menos de un día) o directamente en la rama principal (trunk). El principio fundamental es integrar código frecuentemente para evitar divergencias y detectar problemas de integración tempranamente.

Características distintivas:

- **Rama principal (trunk/main)**: Única rama de larga duración. Todo el código converge aquí.
- **Feature flags**: Mecanismo para ocultar funcionalidad incompleta hasta que esté lista para liberarse.
- **Ramificación de corta duración**: Las ramas de feature existen horas o días, no semanas.
- **Commit frecuentes**: Integración múltiplas veces al día para mantener el trunk deployable.

### Implementación Práctica

El flujo básico de TBD implica trabajar directamente en el trunk o en ramas muy cortas:

```bash
# Trabajar directamente en trunk (para cambios pequeños)
git checkout main
git pull origin main
# hacer cambios
git commit -m "Fix: corrige validación de versión"
git push origin main

# Para features mayores, rama de corta duración
git checkout -b feature/nueva-funcionalidad
git commit -m "WIP: inicio de implementación"
git push origin feature/nueva-funcionalidad

# Mergear rápidamente (dentro de 1-2 días)
git checkout main
git merge feature/nueva-funcionalidad
git push origin main
```

Los feature flags permiten desplegar código incompleto sin afectar a usuarios:

```javascript
// Ejemplo de feature flag en código
if (featureFlags.isEnabled('new-versioning-schema')) {
  return handleNewVersioning(request);
} else {
  return handleLegacyVersioning(request);
}
```

### Pros de Trunk-Based Development

1. **Integración continua real**: Los equipos detectan problemas de integración en horas, no semanas.
2. **Reducción de merge conflicts**: La короткая duración de ramas minimiza la divergence entre ramas.
3. **Despliegue continuo**: El trunk siempre está en estado deployable, facilitando CI/CD.
4. **Simplicidad**: Un modelo mental más sencillo con menos reglas y excepciones.
5. **Feedback rápido**: Los cambios llegan a producción más rápido, permitiendo iteraciones ágiles.

### Contras de Trunk-Based Development

1. **Disciplina requerida**: Necesita equipo maduro que entienda feature flags, testing automatizado y refactoring continuo.
2. **Riesgo de romper producción**: Si no hay suficientes safeguards (tests automatizados, feature flags), cambios defectuosos llegan a producción.
3. **Difícil para release trains**: Equipos que necesitan control estricto sobre qué contenido va en cada release pueden encontrarlo restrictivo.
4. **Complejidad en feature flags**: Gestionar múltiples feature flags puede convertirse en deuda técnica si no se limpian oportunamente.

## Comparativa y Criterios de Selección

### Matriz de Decisión

| Criterio | GitFlow | Trunk-Based |
|----------|---------|-------------|
| Tamaño del equipo | Cualquiera | Preferiblemente pequeño-mediano |
| Frecuencia de release | Ciclos fijos (mensual, trimestral) | Continuo o diario |
| Complejidad del proyecto | Alto | Bajo-medio |
| Tolerancia a riesgo | Baja (entornos regulados) | Alta |
| Madurez del equipo | Variable | Alta |
| Necesidad de auditoría | Alta | Media |

### Recomendaciones por Contexto

**Utilizar GitFlow cuando:**
- El proyecto está en un entorno regulado que requiere auditoría completa del código productivo.
- Se trabajan con ciclos de release fijos y predecibles.
- El equipo tiene múltiples versiones simultáneas en producción.
- Se necesita separación clara entre desarrollo y producción para compliance.
- El equipo está comenzando con control de versiones y necesita estructura.

**Utilizar Trunk-Based Development cuando:**
- Se practica DevOps con despliegue continuo.
- El equipo es pequeño y puede comunicar cambios rápidamente.
- Se prioriza la velocidad de entrega sobre el control estricto.
- Se utilizan feature flags extensivamente.
- El proyecto tiene buena cobertura de tests automatizados.

**Enfoque híbrido:** Muchos equipos adoptan un modelo híbrido que combina elementos de ambos:

- Usar TBD para el día a día con feature flags.
- Mantener ramas de release para gestionar el contenido de cada versión.
- Utilizar hotfix branches solo cuando sea necesario (equivalente a GitFlow).

## Aplicación en Este Proyecto

Este proyecto de versionamiento de APIs sigue un enfoque híbrido adaptado a las necesidades de gestión de contratos OpenAPI y políticas de gateway:

1. **Rama principal (main)**: Contiene el contrato validado y aprobado para producción.
2. **Ramas de feature**: Para desarrollar nuevas políticas o modificar el contrato.
3. **Pull requests**: Requieren validación del contrato (`npm run lint`) y revisión de pares.
4. **Tags de versión**: Cada release del contrato se etiqueta para trazabilidad.

La elección de este modelo permite iteraciones rápidas en el contrato mientras mantiene la integridad del versionamiento de la API.

```
