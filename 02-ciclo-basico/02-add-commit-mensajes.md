# add, commit y los mensajes de commit bien hechos

> **Lo que te vas a llevar:** dominar el uso práctico de `add` y `commit`, y escribir mensajes que de verdad sirvan para algo.

## Repaso rápido de `add` y `commit`

Ya vimos en la entrada anterior que `add` mueve cambios al *staging area* y `commit` los guarda en el historial. Aquí nos centramos en cómo usarlos bien en el día a día, y sobre todo, en algo que se subestima mucho: **cómo escribir el mensaje del commit**.

## Formas de usar `git add`

```bash
git add archivo.js          # añade un archivo concreto
git add carpeta/            # añade todos los cambios de una carpeta
git add .                   # añade todos los cambios del proyecto
git add -p                  # te deja elegir, trozo a trozo, qué añadir de cada archivo
```

`git add -p` (de "patch") es especialmente útil cuando has hecho varios cambios distintos en un mismo archivo y solo quieres incluir parte de ellos en este commit. Git te va mostrando cada bloque de cambios y te pregunta si quieres incluirlo o no.

## Formas de usar `git commit`

```bash
git commit -m "Mensaje del commit"
```

Si necesitas un mensaje más largo, con una descripción además del título, es mejor no forzarlo todo en un `-m`:

```bash
git commit
```

Esto abre tu editor de texto configurado, donde puedes escribir un título y, dejando una línea en blanco, una descripción más detallada.

También existe un atajo para añadir todos los archivos ya vigilados por Git (los que no son nuevos) y hacer commit en un solo paso:

```bash
git commit -am "Mensaje del commit"
```

Ojo: esto **no** incluye archivos completamente nuevos (los que nunca has hecho `add` antes), solo modificaciones sobre archivos que Git ya conocía.

## Cómo escribir buenos mensajes de commit

Un mensaje de commit no es solo un trámite, es **documentación**. Dentro de unos meses (o dentro de un rato), tú u otra persona vais a necesitar entender qué hizo ese commit sin tener que leer todo el código cambiado.

Algunas reglas simples que marcan mucho la diferencia:

- **Usa el imperativo:** "Arregla el bug de login" en lugar de "Arreglado bug de login" o "Arreglando bug". Es una convención, pero ayuda a que el historial se lea de forma consistente.
- **Sé específico, no genérico:** `"Fix bug"` no dice nada. `"Corrige validación de email vacío en el formulario de registro"` sí.
- **Un commit, un propósito:** si tu mensaje necesita un "y" para describir lo que hiciste ("arreglo el login y actualizo estilos"), probablemente deberían ser dos commits distintos.
- **El título, corto; los detalles, en la descripción:** si hace falta explicar el "por qué" de un cambio, resérvalo para la descripción, no lo metas todo en el título.

Ejemplo de un commit bien escrito, con título y descripción:

```
Corrige validación de email vacío en el registro

Antes se permitía enviar el formulario con el campo email
vacío, causando un error 500 en el backend. Se añade
validación en el frontend antes de enviar la petición.
```

## Cómo se rompe esto

El error típico es acumular muchísimos cambios sin relación entre sí y meterlos todos en un único commit gigante con un mensaje tipo `"cambios"` o `"wip"`. El problema aparece más adelante: si algo se rompe y necesitas volver atrás, no puedes deshacer solo la parte problemática, porque todo está mezclado en el mismo commit.

Es mejor acostumbrarse a hacer commits pequeños y frecuentes, cada uno con un propósito claro, aunque al principio parezca que ralentiza el trabajo.

## Para ir más lejos

Existe una convención bastante extendida llamada **Conventional Commits**, que estructura los mensajes con un prefijo (`feat:`, `fix:`, `docs:`, `refactor:`...) para indicar el tipo de cambio. La veremos con más detalle en la sección de buenas prácticas.

---

📹 *Vídeo relacionado: [pendiente]*
