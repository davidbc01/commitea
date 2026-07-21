# cherry-pick: traer un commit concreto de otra rama

> **Lo que te vas a llevar:** saber traer un commit específico de otra rama sin necesidad de fusionar toda la rama entera.

## Cuándo hace falta esto

A veces no quieres todos los cambios de una rama, solo **uno concreto**. Un caso típico: arreglaste un bug en una rama de feature que todavía no está lista para fusionarse entera, pero ese arreglo puntual sí quieres llevarlo ya a `main`.

Para eso no hace falta un `merge` completo. Existe `cherry-pick`, que coge un commit específico de cualquier rama y lo aplica sobre la rama en la que estás.

## Cómo usarlo

Primero, localiza el hash del commit que quieres traer (con `git log` en la rama donde está):

```bash
git log --oneline feature/login
```

```
a1b2c3d Arregla validación de email
e4f5g6h Añade formulario de login (aún incompleto)
```

Quieres solo el primero. Te colocas en la rama de destino y haces:

```bash
git checkout main
git cherry-pick a1b2c3d
```

Esto crea un **nuevo commit** en `main`, con los mismos cambios que tenía `a1b2c3d`, pero con un identificador distinto (igual que pasaba con `rebase`: el contenido es el mismo, el commit es técnicamente nuevo).

## Un ejemplo real

Estás desarrollando una funcionalidad grande en `feature/panel-admin`, todavía muy incompleta. En el camino, arreglas un bug de seguridad que no tiene nada que ver con esa funcionalidad, y ese arreglo sí necesita estar ya en producción, sin esperar a que el panel de admin esté terminado.

```bash
git log --oneline feature/panel-admin
```

```
9f8e7d6 Arregla vulnerabilidad XSS en comentarios
...
```

```bash
git checkout main
git cherry-pick 9f8e7d6
git push
```

El arreglo llega a `main` (y de ahí a producción) sin tener que esperar a que el resto de la funcionalidad esté lista.

## Cómo se rompe esto

El error típico es hacer cherry-pick de un commit que **depende de otros cambios** que no has traído. Si el commit que copias usa una función o variable que se definió en un commit anterior de esa misma rama (que no has traído), el cherry-pick puede fallar o, peor, aplicarse pero dejar el código roto de forma no evidente.

Antes de hacer cherry-pick, revisa si ese commit tiene sentido de forma aislada, o si depende de contexto que solo existe en la rama original.

## Para ir más lejos

Si el cherry-pick genera un conflicto (por ejemplo, porque `main` ya ha cambiado esa misma zona del código), Git te lo indica igual que en un merge normal: puedes resolverlo a mano, hacer `git add` de los archivos resueltos, y continuar con `git cherry-pick --continue`. Si prefieres cancelarlo, `git cherry-pick --abort` te devuelve al estado anterior.

---

📹 *Vídeo relacionado: [pendiente]*
