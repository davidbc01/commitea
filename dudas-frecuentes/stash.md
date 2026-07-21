# stash: guardar cambios a medias sin hacer commit

> **Lo que te vas a llevar:** saber "aparcar" cambios que no están listos para un commit, sin perderlos, cuando necesitas cambiar de tarea rápidamente.

## El problema que resuelve

Estás a mitad de un cambio, sin terminar, y de repente necesitas cambiar de rama (por ejemplo, para arreglar un bug urgente en `main`). Pero Git no te deja cambiar de rama tranquilamente si tienes cambios sin commitear que entran en conflicto con la otra rama.

No quieres hacer commit de algo a medias solo para poder cambiar de rama, pero tampoco quieres perder ese trabajo. Para esto existe `git stash`.

## Cómo funciona

`git stash` guarda tus cambios actuales (tanto en staging como en el working directory) en una especie de "cajón" aparte, y te deja el working directory limpio, como si no hubieras tocado nada:

```bash
git stash
```

```
Saved working directory and index state WIP on feature/login: a1b2c3d Añade formulario
```

Ahora puedes cambiar de rama, hacer lo que necesites, y cuando quieras recuperar tu trabajo:

```bash
git stash pop
```

Esto aplica de nuevo esos cambios sobre tu working directory, y elimina esa entrada del "cajón".

## Un ejemplo real

Estás a mitad de una funcionalidad en `feature/login`, con cambios sin terminar, cuando te avisan de un bug urgente en producción.

```bash
git stash
git checkout main
# ... arreglas el bug, haces commit, push ...
git checkout feature/login
git stash pop
```

Vuelves exactamente a donde estabas, sin haber tenido que hacer ningún commit a medias ni perder tu progreso.

## Guardar varios stashes

Puedes tener más de un stash guardado a la vez. Para verlos todos:

```bash
git stash list
```

```
stash@{0}: WIP on feature/login: a1b2c3d Añade formulario
stash@{1}: WIP on main: e4f5g6h Ajustes de estilos
```

Y aplicar uno concreto (no necesariamente el último):

```bash
git stash pop stash@{1}
```

## Cómo se rompe esto

El error típico es acumular varios stashes y perder la cuenta de qué contenía cada uno, hasta el punto de no recordar si era seguro borrarlos. `git stash pop` elimina la entrada al aplicarla, pero si usas `git stash apply` en su lugar (que aplica sin eliminar), es fácil acabar con una lista de stashes viejos sin saber cuáles siguen siendo necesarios.

Buena costumbre: usa `stash` para pausas cortas, no como almacenamiento a largo plazo de trabajo sin terminar. Si algo va a tardar en retomarse, es mejor hacer un commit (aunque sea con un mensaje tipo "WIP: pendiente de terminar") en su propia rama.

## Para ir más lejos

Puedes darle un mensaje descriptivo a cada stash, muy útil si vas a tener varios a la vez:

```bash
git stash push -m "Formulario de login a medias"
```

---

📹 *Vídeo relacionado: [pendiente]*
