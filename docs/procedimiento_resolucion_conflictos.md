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