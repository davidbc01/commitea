# "Metí un commit en la rama equivocada"

> **Lo que te vas a llevar:** saber mover un commit que hiciste sin querer en la rama que no era.

## El problema

Te pasa más de lo que crees: estás trabajando, haces un commit, y de repente te das cuenta de que estabas en `main` (o en cualquier otra rama) en lugar de en la rama que tocaba. El commit ya está hecho, pero en el sitio equivocado.

La buena noticia: esto tiene arreglo sencillo, siempre que **todavía no hayas hecho push**.

## Caso 1: el commit está en `main` y aún no has hecho push

Este es el caso más común y el más fácil de arreglar.

**Paso 1: crea la rama correcta desde donde estás ahora mismo.**

Como una rama nueva simplemente apunta al commit actual, si la creas ahora, se lleva tu commit con ella:

```bash
git branch feature/login
```

**Paso 2: vuelve `main` atrás, al estado anterior a tu commit.**

```bash
git checkout main
git reset --hard HEAD~1
```

`HEAD~1` significa "un commit antes de donde estoy". Esto mueve `main` hacia atrás, dejando tu commit fuera de `main`... pero sigue existiendo, porque `feature/login` todavía apunta a él.

**Paso 3: cámbiate a la rama correcta para seguir trabajando ahí.**

```bash
git checkout feature/login
```

Resultado: `main` está limpio, como si el commit nunca hubiera pasado por ahí, y tu trabajo está a salvo en `feature/login`.

## Caso 2: ya has hecho push del commit a `main`

Aquí la cosa se complica un poco, porque `reset --hard` reescribe el historial, y si ya lo subiste, otras personas pueden haber descargado ese commit. Reescribir el historial compartido es delicado (lo veremos con detalle en la sección de rebase).

Si estás en este caso y trabajas solo en el repositorio, puedes hacer lo mismo de arriba y luego forzar el push:

```bash
git push origin main --force
```

Pero si otras personas colaboran en el mismo repo, avísales antes: un `--force` puede desincronizar su trabajo local si no lo saben.

## Cómo se rompe esto

El error típico que agrava esta situación es hacer `reset --hard` **sin haber creado antes la rama nueva**. Si borras el commit de `main` sin haberlo "guardado" en otra rama primero, lo pierdes (aunque, como veremos en otra entrada, todavía se podría recuperar con `git reflog` durante un tiempo — pero es mucho más sencillo no llegar a esa situación).

Regla de oro: **primero crea la rama de destino, después toca la rama de origen.**

## Para ir más lejos

Puedes evitar este problema por completo cogiendo la costumbre de comprobar en qué rama estás antes de empezar a trabajar:

```bash
git branch --show-current
```

Muchos editores (VS Code, por ejemplo) también muestran la rama actual en la barra inferior, así que un vistazo rápido antes de hacer commit puede ahorrarte este susto.

---

📹 *Vídeo relacionado: [pendiente]*
