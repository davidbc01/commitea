# Convenciones de commits (Conventional Commits)

> **Lo que te vas a llevar:** una forma estandarizada de escribir mensajes de commit que hace el historial más útil y permite automatizar cosas a partir de él.

## Por qué existe una convención

Ya vimos en el ciclo básico cómo escribir buenos mensajes de commit. Conventional Commits va un paso más allá: propone un **formato fijo**, para que cualquiera que lea el historial (o cualquier herramienta automatizada) pueda entender de un vistazo qué tipo de cambio es cada commit, sin tener que leer el mensaje completo.

## El formato

```
tipo(alcance opcional): descripción breve
```

Por ejemplo:

```
feat(auth): añade login con Google
fix(carrito): corrige cálculo de totales con descuentos
docs: actualiza instrucciones de instalación
```

## Los tipos más usados

- **feat:** una funcionalidad nueva.
- **fix:** una corrección de un bug.
- **docs:** cambios solo en documentación.
- **style:** cambios de formato que no afectan a la lógica (espacios, indentación, punto y coma...).
- **refactor:** cambio en el código que no arregla un bug ni añade funcionalidad, solo lo reorganiza o mejora.
- **test:** añadir o corregir tests.
- **chore:** tareas de mantenimiento que no tocan código de producción (actualizar dependencias, configurar herramientas...).

El "alcance" (lo que va entre paréntesis) es opcional, y sirve para indicar qué parte del proyecto afecta el cambio (`auth`, `carrito`, `api`...). Útil en proyectos grandes con varias áreas claramente diferenciadas.

## Un ejemplo con descripción larga

Igual que con cualquier commit, si hace falta más contexto, se añade en el cuerpo del mensaje:

```
fix(carrito): corrige cálculo de totales con descuentos

El descuento se aplicaba antes de sumar el IVA, en lugar
de después, dando un total incorrecto en pedidos con
cupones activos.
```

## Cambios que rompen compatibilidad (breaking changes)

Si un cambio rompe algo que dependía del comportamiento anterior, se indica añadiendo `!` después del tipo, o con `BREAKING CHANGE:` en el cuerpo del mensaje:

```
feat(api)!: cambia el formato de respuesta del endpoint /usuarios
```

Esto es especialmente útil en proyectos que generan versiones automáticamente a partir del historial (por ejemplo, decidiendo si la siguiente versión debe subir de forma menor o mayor según el tipo de cambios acumulados).

## Cómo se rompe esto

El error típico es aplicar la convención a medias: usar los prefijos (`feat:`, `fix:`...) pero seguir escribiendo mensajes vagos por detrás (`feat: cambios`). El prefijo por sí solo no aporta nada si la descripción sigue sin decir qué ha cambiado realmente. La convención es una capa extra sobre un buen mensaje, no un sustituto de escribirlo bien.

## Para ir más lejos

Existen herramientas como `commitlint` que puedes integrar en tu proyecto para **forzar** que todos los commits sigan esta convención antes de aceptarse, algo útil en equipos donde varias personas comitean con estilos distintos.

---

📹 *Vídeo relacionado: [pendiente]*
