# Conflictos de merge: cómo resolverlos sin entrar en pánico

> **Lo que te vas a llevar:** entender por qué aparece un conflicto, cómo leerlo, y cómo resolverlo paso a paso sin miedo a romper el proyecto.

## ¿Qué es un conflicto de merge?

Un conflicto pasa cuando Git no puede decidir por ti cómo combinar dos cambios, porque **dos personas (o dos ramas) han modificado la misma parte de un archivo de forma distinta**.

Git es bueno fusionando cambios automáticamente cuando no se pisan entre sí. Pero cuando sí se pisan, te lo deja a ti. Eso no es un error tuyo ni un fallo de Git: es lo esperado cuando varias personas tocan el mismo código.

## Ejemplo real

Imagina que tú y un compañero estáis trabajando sobre el mismo archivo `README.md`.

Tú, en tu rama `feature/login`, cambias una línea:

```bash
git add README.md
git commit -m "Actualizo instrucciones de instalación"
```

Mientras tanto, tu compañero ha cambiado esa misma línea en `main` y ya ha hecho merge.

Cuando intentas traer los cambios de `main` a tu rama:

```bash
git checkout feature/login
git merge main
```

Git te devuelve algo así:

```
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

## Cómo leer el conflicto

Si abres `README.md`, verás algo como esto:

```
<<<<<<< HEAD
Para instalar, ejecuta `npm install`
=======
Para instalar, ejecuta `pnpm install`
>>>>>>> main
```

- Todo lo que hay entre `<<<<<<< HEAD` y `=======` es **tu versión** (la rama en la que estás).
- Todo lo que hay entre `=======` y `>>>>>>> main` es **la versión de la rama que estás fusionando** (en este caso, `main`).

## Cómo se resuelve

1. Decide qué versión quieres conservar (o combina ambas manualmente).
2. Borra las marcas `<<<<<<<`, `=======` y `>>>>>>>` — no son parte del archivo, son solo indicadores de Git.
3. Deja el archivo como debería quedar finalmente.
4. Marca el conflicto como resuelto y haz commit:

```bash
git add README.md
git commit -m "Resuelvo conflicto en README.md"
```

Con eso, el merge queda completado.

## Cómo se rompe esto

El error más típico de principiante: **dejar las marcas de conflicto (`<<<<<<<`, `=======`, `>>>>>>>`) en el archivo sin darte cuenta** y hacer commit así. El código queda roto y nadie entiende por qué, hasta que alguien revisa el archivo y ve las marcas ahí.

Truco para evitarlo: antes de hacer `git add`, busca en el archivo si quedan `<<<<<<<` sueltos. Muchos editores (VS Code, por ejemplo) los resaltan automáticamente en colores.

## Para ir más lejos

- Si el conflicto es muy grande o tienes dudas, puedes abortar el merge en cualquier momento con `git merge --abort` y volver al estado anterior, sin miedo.
- Herramientas visuales (como el editor de conflictos de VS Code, o `git mergetool`) facilitan mucho este proceso cuando estás empezando.

---

📹 *Vídeo relacionado: [pendiente]*
