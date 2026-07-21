# Git hooks básicos

> **Lo que te vas a llevar:** entender qué son los git hooks y cómo usarlos para automatizar comprobaciones antes de un commit o un push.

## Nota sobre `.gitignore`

Esta entrada cierra el punto de "`.gitignore`, git hooks básicos" del índice. El `.gitignore` ya lo vimos en detalle en `dudas-frecuentes/gitignore-mal-configurado.md`, así que aquí nos centramos solo en los hooks.

## Qué es un git hook

Un hook es un **script que Git ejecuta automáticamente** en momentos concretos de su flujo de trabajo: antes de un commit, después de un commit, antes de un push, etc. Te permite automatizar comprobaciones o tareas sin depender de que tú (o cualquiera del equipo) se acuerde de hacerlas manualmente.

Cada repositorio tiene una carpeta `.git/hooks/` con ejemplos de scripts ya incluidos (con extensión `.sample`), que no se ejecutan hasta que les quitas esa extensión y los conviertes en ejecutables.

## Los hooks más útiles para empezar

- **`pre-commit`**: se ejecuta justo antes de completar un commit. Ideal para comprobar que el código pasa el linter, o que no hay errores de formato, antes de que el commit se registre.
- **`commit-msg`**: se ejecuta para validar el mensaje del commit. Aquí es donde podrías forzar, por ejemplo, que todos los commits sigan la convención de Conventional Commits que vimos antes.
- **`pre-push`**: se ejecuta antes de subir cambios al remoto. Útil para, por ejemplo, correr los tests automáticos y bloquear el push si algo falla.

## Un ejemplo sencillo

Crear un hook `pre-commit` que impida hacer commit si hay algún `console.log` olvidado en el código (algo muy común al depurar):

```bash
#!/bin/sh
if git diff --cached | grep -q "console.log"; then
  echo "Elimina los console.log antes de hacer commit"
  exit 1
fi
```

Este script se guardaría en `.git/hooks/pre-commit`, y habría que darle permisos de ejecución:

```bash
chmod +x .git/hooks/pre-commit
```

A partir de ahí, cualquier intento de commit que incluya un `console.log` en las líneas añadidas se bloqueará automáticamente.

## El problema: los hooks no se comparten con Git

Aquí está el matiz importante: la carpeta `.git/` **no forma parte del historial del proyecto**, así que estos hooks no se suben al repositorio ni llegan a quien clona el proyecto. Cada persona tendría que configurarlos manualmente, lo cual no es práctico en equipo.

Por eso, en proyectos reales, es habitual usar herramientas que gestionan esto por ti, como **Husky** (muy usado en proyectos de Node/JavaScript), que guarda la configuración de hooks dentro del propio proyecto (fuera de `.git/`) y la instala automáticamente para todo el equipo cuando alguien clona el repositorio.

## Cómo se rompe esto

El error típico es configurar hooks manuales en `.git/hooks/` pensando que "ya están protegidos", sin darse cuenta de que son solo locales. El resto del equipo sigue pudiendo hacer commits sin esas comprobaciones, porque nunca las recibieron. Si la comprobación es importante para el proyecto, conviene gestionarla con una herramienta compartida (como Husky) en lugar de un hook manual.

## Para ir más lejos

Herramientas como Husky suelen combinarse con `lint-staged`, que aplica el linter solo a los archivos que realmente vas a comitear (no a todo el proyecto), haciendo que el hook sea rápido incluso en proyectos grandes.

---

📹 *Vídeo relacionado: [pendiente]*
