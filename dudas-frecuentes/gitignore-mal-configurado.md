# .gitignore mal configurado

> **Lo que te vas a llevar:** entender qué es el `.gitignore`, cómo usarlo bien, y qué hacer si empezaste a vigilar un archivo que no debías.

## Qué es el `.gitignore`

Es un archivo especial, en la raíz de tu proyecto, que le dice a Git qué archivos o carpetas **ignorar por completo** — es decir, ni `git status` los va a mostrar, ni `git add .` los va a incluir, aunque existan en tu carpeta.

Se usa para todo aquello que no debería formar parte del historial del proyecto: dependencias instaladas (`node_modules/`), archivos de configuración local con credenciales (`.env`), archivos generados automáticamente (carpetas de build), o archivos propios de tu editor o sistema operativo (`.DS_Store`, `.vscode/`).

## Cómo se usa

Un `.gitignore` es simplemente un archivo de texto con un patrón por línea:

```
node_modules/
.env
dist/
.DS_Store
*.log
```

- `node_modules/` ignora esa carpeta entera.
- `.env` ignora ese archivo concreto.
- `*.log` ignora cualquier archivo que termine en `.log`, sin importar el nombre.

Este archivo debe crearse **desde el principio del proyecto**, antes de que esos archivos lleguen a hacerse commit por primera vez.

## El problema: cuando llega tarde

Aquí está el error más típico y el motivo de esta entrada: si un archivo **ya ha sido comiteado** antes de añadirlo al `.gitignore`, añadirlo ahora no lo va a sacar del historial. Git ya lo está vigilando, y seguirá haciéndolo, aunque aparezca en el `.gitignore`.

## Cómo arreglarlo (caso: el archivo está en el repo pero ya no debería)

Si te das cuenta de que, por ejemplo, `node_modules/` se ha comiteado por error, y ahora quieres que Git deje de vigilarlo (sin borrarlo de tu disco, solo del control de versiones):

```bash
git rm -r --cached node_modules/
echo "node_modules/" >> .gitignore
git add .gitignore
git commit -m "Deja de vigilar node_modules"
```

`git rm --cached` elimina el archivo o carpeta del control de Git, pero el flag `--cached` es clave: **mantiene el archivo en tu disco**, solo dejar de vigilarlo con Git.

## Importante: esto no borra el archivo del historial pasado

Este proceso hace que, a partir de ahora, ese archivo deje de vigilarse. Pero si en algún commit anterior ya estaba incluido, sigue existiendo ahí, en el historial. Para un `node_modules/` esto no suele ser grave (no es información sensible), pero si lo que se comiteó por error fue algo como un `.env` con contraseñas, esto **no es suficiente** — hace falta reescribir el historial, como vimos en la entrada de "he hecho push y me arrepiento".

## Cómo se rompe esto

El error de raíz casi siempre es el mismo: no crear el `.gitignore` antes del primer commit del proyecto. Cógelo como costumbre: **antes de tu primer `git add .`, para y piensa qué no debería estar ahí.**

Muchos proyectos y frameworks (Laravel, Node, Astro...) ya generan un `.gitignore` decente por defecto al crear el proyecto — revísalo, pero no asumas que está completo para tu caso concreto.

## Para ir más lejos

GitHub mantiene una colección de plantillas de `.gitignore` para distintos lenguajes y frameworks en [github.com/github/gitignore](https://github.com/github/gitignore), útil como punto de partida en lugar de escribir uno desde cero.

---

📹 *Vídeo relacionado: [pendiente]*
