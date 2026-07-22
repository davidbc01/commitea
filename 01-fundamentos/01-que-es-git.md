# ¿Qué es Git y por qué existe?

> **Lo que te vas a llevar:** entender qué problema resuelve Git y por qué casi todo el desarrollo de software lo usa hoy en día.

## El problema antes de Git

Imagina que estás escribiendo un documento importante tú solo. Para no perder el trabajo, probablemente hayas hecho algo como esto alguna vez:

```
proyecto.docx
proyecto_final.docx
proyecto_final_v2.docx
proyecto_final_v2_BUENO.docx
proyecto_final_definitivo.docx
```

Funciona... hasta que dejas de acordarte de qué versión es la buena, o hasta que dos personas tienen que trabajar sobre el mismo documento a la vez y no saben cómo juntar sus cambios sin pisarse.

Ahora multiplica eso por un proyecto de software con cientos o miles de archivos, y varias personas tocándolos al mismo tiempo. Sin una herramienta que lo gestione, es un caos total.

## Qué es Git

Git es un **sistema de control de versiones**. En cristiano: es una herramienta que guarda un historial de todos los cambios que haces en tus archivos, para que puedas:

- Ver qué ha cambiado, cuándo y quién lo cambió.
- Volver a una versión anterior si algo se rompe.
- Trabajar en paralelo con otras personas sobre el mismo proyecto sin pisaros (o, si os pisáis, resolverlo de forma controlada).
- Probar cosas nuevas sin miedo a estropear lo que ya funciona.

Git no vive "en la nube" por defecto. Es una herramienta que se instala en tu ordenador y guarda ese historial en una carpeta oculta (`.git`) dentro de tu proyecto. Todo funciona localmente, sin necesidad de internet.

## Un ejemplo sencillo

Sin Git, cambiar algo en tu código y arrepentirte significa intentar recordar cómo estaba antes, o rebuscar en carpetas de copias de seguridad.

Con Git, el proceso es:

```bash
git add archivo.js
git commit -m "Añado validación del formulario"
```

Ese `commit` es como una fotografía del estado de tus archivos en ese momento exacto. Si más adelante algo se rompe, puedes volver a esa fotografía. Git guarda todas las fotografías, en orden, y te deja moverte entre ellas.

## Cómo se rompe esto

El error típico de quien empieza es pensar que Git guarda cambios automáticamente, como un autoguardado. No es así: **Git solo recuerda lo que tú le pides explícitamente que recuerde**, mediante `add` y `commit`. Si editas un archivo y no haces commit, ese cambio no está "protegido" por Git todavía, solo existe en tu carpeta de trabajo.

Esto lo veremos en detalle en la siguiente entrada, sobre el ciclo básico de trabajo.

## Para ir más lejos

Git fue creado en 2005 por Linus Torvalds (el creador de Linux) para gestionar el desarrollo del propio kernel de Linux, un proyecto con miles de colaboradores. Estaba diseñado para ser rápido y para funcionar bien incluso cuando mucha gente trabaja a la vez sobre el mismo código — por eso hoy es el estándar en prácticamente todo el desarrollo de software.

<!-- --- -->

<!-- 📹 *Vídeo relacionado: [pendiente]* -->
