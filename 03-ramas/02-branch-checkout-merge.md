# branch, checkout/switch y merge

> **Lo que te vas a llevar:** saber crear ramas, moverte entre ellas, y juntar el trabajo de una rama con otra.

## Crear ramas: `git branch`

```bash
git branch feature/login
```

Esto crea una rama nueva llamada `feature/login`, pero **no te mueve a ella**. Sigues en la rama en la que estabas. `git branch` sin argumentos te muestra la lista de ramas que existen, marcando con un asterisco en cuál estás:

```bash
git branch
```

```
  feature/login
* main
```

## Moverte entre ramas: `checkout` y `switch`

Para cambiar de rama, tradicionalmente se usa:

```bash
git checkout feature/login
```

En versiones más recientes de Git existe `switch`, pensado específicamente para esto (mientras que `checkout` hace varias cosas a la vez, lo que a veces genera confusión):

```bash
git switch feature/login
```

Ambos hacen lo mismo en este caso: cambian tu working directory para reflejar el estado de esa rama. Puedes usar el que prefieras; en el resto del repo usaremos `checkout` por ser el más extendido, pero `switch` es perfectamente válido.

Un atajo útil: crear una rama y moverte a ella en un solo paso:

```bash
git checkout -b feature/login
# o, equivalente:
git switch -c feature/login
```

## Juntar ramas: `git merge`

Cuando has terminado el trabajo en una rama y quieres incorporarlo a otra (normalmente, a `main`), usas `merge`. El proceso es: te colocas en la rama que **va a recibir** los cambios, y le dices que fusione la otra:

```bash
git checkout main
git merge feature/login
```

Esto trae todos los commits de `feature/login` a `main`. Si nadie más ha tocado `main` mientras tanto, Git puede hacer esto de forma automática y limpia (lo que se llama un "fast-forward": simplemente mueve la etiqueta de `main` hacia adelante).

Si `main` sí ha recibido cambios propios mientras tanto, Git crea un **commit de merge**, que combina ambas historias:

```
A --- B --- C   (main)
       \     \
        D --- E   commit de merge
       (feature/login)
```

Este commit de merge no tiene nada de malo — es simplemente cómo Git representa que dos líneas de trabajo se han unido.

## Cómo se rompe esto

El error típico es hacer cambios directamente sobre `main` "porque total, es rápido", saltándote la creación de una rama. El problema aparece cuando ese cambio rápido resulta no ser tan rápido, o rompe algo, y ya está mezclado con el resto del proyecto sin ninguna separación que te permita aislarlo o descartarlo fácilmente.

La costumbre que conviene coger: cualquier cambio que no sea trivial, en su propia rama.

## Para ir más lejos

Para borrar una rama que ya has fusionado y no necesitas más:

```bash
git branch -d feature/login
```

Git te avisará si intentas borrar una rama que **no** ha sido fusionada todavía, como protección para que no pierdas trabajo por accidente.

En la siguiente entrada veremos qué pasa cuando el merge no puede hacerse automáticamente: los conflictos.

---

📹 *Vídeo relacionado: [pendiente]*
