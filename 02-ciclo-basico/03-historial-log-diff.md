# El historial: log, diff, show

> **Lo que te vas a llevar:** saber consultar el historial de tu proyecto y ver exactamente qué cambió en cada momento.

## Por qué esto importa

Todos los commits que has ido haciendo forman un historial. Pero ese historial no sirve de nada si no sabes consultarlo. Estos tres comandos son los que vas a usar para moverte por él: `git log` (qué commits hay), `git diff` (qué ha cambiado exactamente) y `git show` (el detalle de un commit concreto).

## `git log`: ver el historial de commits

```bash
git log
```

Te muestra la lista de commits, del más reciente al más antiguo, con su hash (identificador único), autor, fecha y mensaje:

```
commit 8f3d92a1c4e5b6f7a8b9c0d1e2f3a4b5c6d7e8f9
Author: David <tu@email.com>
Date:   Mon Jul 20 10:32:00 2026 +0200

    Corrige validación de email vacío en el registro
```

Como esta vista puede ser muy larga, hay opciones que la hacen más manejable:

```bash
git log --oneline           # una línea por commit, mucho más compacto
git log --oneline -5        # solo los últimos 5 commits
git log --author="David"    # filtra por autor
git log -- archivo.js       # solo commits que afectaron a ese archivo
```

`git log --oneline` es probablemente el que más vas a usar en el día a día, porque te da una vista rápida de qué ha ido pasando.

## `git diff`: ver cambios exactos

`git diff` te muestra, línea a línea, qué se ha añadido o eliminado. Tiene varios usos según qué quieras comparar:

```bash
git diff                    # cambios en el working directory que aún no están en staging
git diff --staged           # cambios que ya están en staging, listos para el commit
git diff HEAD~1 HEAD        # diferencias entre el commit anterior y el actual
```

El resultado se ve así, con `-` para líneas eliminadas y `+` para líneas añadidas:

```diff
- const email = req.body.email;
+ const email = req.body.email?.trim();
+ if (!email) {
+   return res.status(400).send("Email requerido");
+ }
```

## `git show`: el detalle de un commit concreto

Si quieres ver exactamente qué cambió en un commit específico (no el último, uno cualquiera del historial), usas `git show` seguido del hash:

```bash
git show 8f3d92a
```

No hace falta escribir el hash completo, con los primeros 7-8 caracteres suele ser suficiente para identificarlo sin ambigüedad.

## Cómo se rompe esto

El error típico es no saber diferenciar `git diff` de `git diff --staged`, y pensar "no he cambiado nada" cuando en realidad sí hay cambios, solo que ya están en la staging area (por eso `git diff` a secas no los muestra). Si algo no aparece donde lo esperas, prueba con la otra variante antes de asumir que no hay cambios.

## Para ir más lejos

Si quieres una vista más visual del historial, con las ramas representadas gráficamente:

```bash
git log --oneline --graph --all
```

Esto se vuelve especialmente útil una vez empieces a trabajar con ramas, que es justo el siguiente bloque.

---

📹 *Vídeo relacionado: [pendiente]*
