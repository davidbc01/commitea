# "He hecho push y me arrepiento"

> **Lo que te vas a llevar:** entender por qué un push cambia las reglas del juego, y qué opciones tienes según la situación.

## Por qué esto es distinto a arrepentirte de un commit local

Mientras un commit vive solo en tu ordenador, puedes reescribirlo, borrarlo o moverlo sin ningún problema: nadie más lo ha visto. Pero en cuanto haces `git push`, ese commit pasa a existir también en el repositorio remoto (GitHub), y **potencialmente, otras personas ya lo han descargado** con un `git pull`.

Esto significa que "deshacer" un push no es tan simple como deshacer un commit local: si reescribes el historial remoto, cualquiera que ya tuviera esos commits se queda con un historial que ya no coincide.

## Situación 1: subiste algo que no debía subirse, pero no es sensible

Por ejemplo, un archivo de más, o un cambio a medias que preferirías no tener ahí todavía.

La opción más segura, sobre todo si trabajas con más gente, es usar `git revert` (que ya vimos en la entrada anterior): crea un commit nuevo que deshace los cambios, sin reescribir el historial.

```bash
git revert HEAD
git push
```

Esto es limpio, no rompe nada para nadie más, y queda un registro claro de que ese cambio se deshizo intencionadamente.

## Situación 2: trabajas solo en el repositorio y quieres el historial limpio

Si nadie más ha podido descargar ese commit (por ejemplo, lo acabas de subir hace segundos, en un proyecto personal), puedes permitirte reescribir el historial:

```bash
git reset --hard HEAD~1
git push --force
```

`--force` sobreescribe el historial remoto con el tuyo. Es una operación que hay que usar con cuidado: si hay algo en el remoto que tú no tienes localmente, lo perderás sin aviso.

## Situación 3: has subido información sensible (contraseñas, claves API, etc.)

Este es el caso más delicado, y **`revert` no es suficiente**. Aunque el commit siguiente "deshaga" el cambio, la información sensible sigue existiendo en el historial, visible para cualquiera que mire commits anteriores.

Aquí hacen falta pasos adicionales:

1. Cambia inmediatamente esa clave o contraseña donde corresponda (considérala comprometida, aunque el repo sea privado).
2. Elimina el rastro del historial con herramientas pensadas para esto, como [`git filter-repo`](https://github.com/newren/git-filter-repo) o BFG Repo-Cleaner, que reescriben todo el historial eliminando ese dato.
3. Haz `push --force` con el historial limpio.

Este proceso es más avanzado y merece su propia guía detallada más adelante — por ahora, lo importante es saber que **el primer paso siempre es rotar la credencial**, no solo borrar el commit.

## Cómo se rompe esto

El error típico (y el más peligroso) es pensar que un simple `revert` o borrar el archivo en un commit posterior "soluciona" el problema de haber subido una contraseña. El dato sigue en el historial de Git, accesible para cualquiera que lo consulte, aunque ya no aparezca en la versión actual del archivo.

## Para ir más lejos

Para evitar llegar a la situación 3 directamente, es buena práctica usar un archivo `.gitignore` bien configurado desde el principio del proyecto, para que archivos con credenciales (como `.env`) ni siquiera lleguen a estar en el radar de Git. Lo veremos en la sección de buenas prácticas.

---

📹 *Vídeo relacionado: [pendiente]*
