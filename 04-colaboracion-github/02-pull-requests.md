# Pull requests: cómo se hace uno bien

> **Lo que te vas a llevar:** entender qué es una pull request y cómo abrir una que sea fácil de revisar y aceptar.

## Qué es una pull request

Una pull request (PR) es, en esencia, una **propuesta de cambios**. Le estás diciendo al proyecto: "he hecho estos cambios en mi rama (o en mi fork), ¿los incorporáis a la vuestra?"

No es un comando de Git, es una funcionalidad de GitHub (y plataformas similares). Técnicamente, una PR compara dos ramas y te muestra las diferencias, permitiendo que otras personas las revisen, comenten, pidan cambios, y finalmente las acepten (o no).

## El flujo típico

1. Creas una rama para tu cambio (nunca trabajas directamente sobre `main`).
2. Haces tus commits en esa rama.
3. Subes la rama a GitHub con `git push`.
4. Desde GitHub, abres una pull request comparando tu rama con la rama principal del proyecto (normalmente `main`).
5. Alguien revisa tus cambios, comenta si hace falta, y si todo está bien, la fusiona.

```bash
git checkout -b fix/boton-envio
# ... haces tus cambios y commits ...
git push -u origin fix/boton-envio
```

Después de este `push`, GitHub te suele mostrar directamente un enlace para abrir la pull request desde esa rama.

## Cómo escribir una buena pull request

Una PR bien hecha se revisa rápido y genera menos idas y venidas. Algunas claves:

- **Título claro:** igual que con los commits, describe qué hace el cambio, no cómo te sientes al respecto ("Arregla validación de email en registro", no "Cambios varios").
- **Descripción con contexto:** qué problema resolvías, cómo lo resolviste, y si hay algo que el revisor debería tener en cuenta especialmente.
- **PRs pequeñas y enfocadas:** una PR que cambia 15 archivos sin relación entre sí es agotadora de revisar. Si puedes dividir el trabajo en varias PRs más pequeñas, casi siempre es mejor.
- **Enlaza el issue relacionado**, si existe (por ejemplo, escribiendo `Closes #12` en la descripción, lo que además cierra automáticamente ese issue al fusionar la PR).

## Un ejemplo de buena descripción

```
## Qué hace

Corrige la validación del email en el formulario de registro,
que actualmente permite enviarse vacío.

## Cómo probarlo

1. Ir a /registro
2. Dejar el campo email vacío y enviar
3. Debería mostrar un error en lugar de enviar la petición

Closes #12
```

## Cómo se rompe esto

El error típico es abrir una PR gigante que mezcla varios cambios sin relación (un arreglo de bug, una refactorización, y un cambio de estilos, todo junto). Esto hace que revisarla sea lento y confuso, y que si algo hay que rechazar, no se pueda hacer sin rechazar todo lo demás también.

Si te das cuenta de que tu PR está creciendo mucho, suele ser buena señal de que conviene dividirla en varias más pequeñas.

## Para ir más lejos

Muchos proyectos usan **PRs en modo "draft"** (borrador) cuando el trabajo todavía no está terminado pero quieres compartir el progreso o pedir feedback temprano. GitHub las marca visualmente distintas, dejando claro que todavía no están listas para fusionarse.

---

📹 *Vídeo relacionado: [pendiente]*
