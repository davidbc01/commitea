# Tu primer repositorio: init, clone, status

> **Lo que te vas a llevar:** saber crear un repositorio desde cero, o descargar uno que ya existe, y entender qué está pasando en él en todo momento.

## ¿Qué es un repositorio?

Un repositorio (o "repo") es, simplemente, **una carpeta que Git está vigilando**. Dentro de esa carpeta, Git guarda una subcarpeta oculta llamada `.git`, donde vive todo el historial de cambios.

Hay dos formas de empezar a trabajar con un repositorio: crear uno nuevo desde cero, o descargar uno que ya existe en GitHub.

## Crear un repositorio nuevo: `git init`

Si estás empezando un proyecto desde cero, primero creas la carpeta y luego le dices a Git que empiece a vigilarla:

```bash
mkdir mi-proyecto
cd mi-proyecto
git init
```

Después de esto, verás un mensaje confirmando que se ha inicializado un repositorio vacío. A partir de este momento, Git está listo para empezar a guardar el historial de lo que hagas en esa carpeta, aunque todavía no ha guardado nada.

## Descargar un repositorio existente: `git clone`

Si el proyecto ya existe en GitHub (por ejemplo, quieres colaborar en un proyecto de otra persona, o recuperar uno tuyo en un ordenador nuevo), no usas `init`, usas `clone`:

```bash
git clone https://github.com/usuario/proyecto.git
```

Esto descarga la carpeta completa del proyecto, junto con **todo su historial de commits**, no solo el estado actual de los archivos. Es la diferencia clave entre descargar un .zip de un proyecto y clonarlo con Git: con `clone` te llevas también la memoria de cómo se ha llegado hasta ahí.

## Ver el estado de tu repositorio: `git status`

Este es probablemente el comando que más vas a usar. `git status` te dice, en cualquier momento, qué está pasando en tu repositorio: qué archivos has modificado, cuáles están listos para hacer commit, y cuáles Git todavía no está vigilando.

```bash
git status
```

Un resultado típico se ve así:

```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        nuevo-archivo.js
```

Esto te está diciendo dos cosas distintas: `index.html` ha sido modificado pero todavía no está preparado para el commit, y `nuevo-archivo.js` es un archivo nuevo que Git todavía no conoce.

## Cómo se rompe esto

El error típico aquí es hacer `git init` **dentro de una carpeta que ya es, sin saberlo, parte de otro repositorio** (por ejemplo, dentro de una subcarpeta de un proyecto que ya tenía Git). Esto puede crear repositorios anidados que dan comportamientos raros y confusos.

Antes de hacer `git init`, es buena costumbre comprobar con `git status` si ya estás dentro de un repositorio existente. Si el comando responde con información de un repo (en lugar de un error tipo "not a git repository"), ya estás dentro de uno.

## Para ir más lejos

`git status` no modifica nada, solo te informa. Es un comando totalmente seguro que puedes (y deberías) ejecutar constantemente mientras trabajas, para no perder de vista en qué punto estás.

---

📹 *Vídeo relacionado: [pendiente]*
