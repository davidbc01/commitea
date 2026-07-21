# ¿Qué es GitHub y en qué se diferencia de Git?

> **Lo que te vas a llevar:** entender que Git y GitHub no son lo mismo, y para qué sirve cada uno.

## La confusión más típica al empezar

Mucha gente que empieza usa "Git" y "GitHub" como si fueran sinónimos. Es normal, porque casi siempre se aprenden juntos, pero son dos cosas distintas:

- **Git** es la herramienta que guarda el historial de cambios de tu proyecto. Vive en tu ordenador y funciona sin internet.
- **GitHub** es una plataforma web donde puedes **subir** ese historial, para tenerlo respaldado en la nube y para poder compartirlo o trabajar en él con otras personas.

Dicho de otra forma: Git es el motor, GitHub es uno de los sitios donde puedes aparcar el coche para que otros lo vean.

## ¿Por qué hace falta algo como GitHub?

Con Git solo, tu historial de cambios vive únicamente en tu ordenador. Eso significa que:

- Si tu ordenador se rompe, pierdes ese historial (a menos que lo tengas respaldado en otro sitio).
- Si quieres colaborar con alguien, no hay forma sencilla de compartir ese historial sin GitHub o algo parecido.

GitHub resuelve esto dándote un lugar en la nube (un **repositorio remoto**) donde subir tu historial de Git, y donde otras personas pueden acceder a él, proponer cambios, o simplemente verlo.

Importante: **GitHub no es la única opción**. Existen alternativas como GitLab o Bitbucket, que hacen básicamente lo mismo. GitHub es, de lejos, la más usada, por eso es la que vamos a usar aquí.

## Un ejemplo sencillo

Imagina que tienes un proyecto con Git funcionando en tu ordenador, con varios commits ya hechos. Para subirlo a GitHub por primera vez, el proceso (simplificado) sería:

```bash
git remote add origin https://github.com/tu-usuario/tu-proyecto.git
git push -u origin main
```

Con esto, tu historial local queda también disponible en GitHub. A partir de ahí, cada vez que hagas un nuevo commit, puedes subirlo con:

```bash
git push
```

Y si quieres traer cambios que hay en GitHub pero no en tu ordenador (por ejemplo, cambios que ha subido otra persona):

```bash
git pull
```

## Cómo se rompe esto

El error típico es pensar que hacer un `commit` ya sube los cambios a GitHub. No es así: **el commit solo guarda el cambio en tu historial local**. Hasta que no haces `git push`, esos cambios no existen en GitHub, y nadie más puede verlos.

Es una fuente común de confusión: alguien hace varios commits, cree que ya está "subido", y luego se sorprende de que en GitHub no aparece nada nuevo.

## Para ir más lejos

GitHub además de alojar repositorios ofrece herramientas extra que no son parte de Git en sí: issues (para reportar problemas o ideas), pull requests (para proponer cambios), y GitHub Actions (para automatizar tareas). Iremos viendo varias de estas en las siguientes secciones, especialmente en la de colaboración.

---

📹 *Vídeo relacionado: [pendiente]*
