# Code review básico, cómo responder a comentarios

> **Lo que te vas a llevar:** entender qué es una code review y cómo manejar los comentarios que recibas sin tomártelo como algo personal.

## Qué es una code review

Cuando abres una pull request, normalmente alguien la revisa antes de aceptarla. Esa revisión (code review) consiste en leer tus cambios, entender qué hacen, y comentar cosas: dudas, sugerencias, errores que ha visto, o simplemente aprobar el cambio tal cual está.

GitHub te permite comentar línea por línea del código cambiado, no solo dejar un comentario general en la PR. Esto hace que la conversación quede anclada exactamente a la parte del código de la que se está hablando.

## Los tres resultados posibles de una review

Cuando alguien revisa tu PR en GitHub, normalmente elige uno de estos tres:

- **Approve** (aprobar): el cambio está bien, listo para fusionarse.
- **Comment** (comentar): deja observaciones, pero sin bloquear ni aprobar formalmente.
- **Request changes** (solicitar cambios): hay algo que debe corregirse antes de aceptar la PR.

## Cómo responder a comentarios

Recibir comentarios en una PR es completamente normal, incluso en proyectos donde llevas tiempo colaborando. No es un juicio sobre ti, es parte del proceso.

Algunas pautas que ayudan:

- **Responde a cada comentario**, aunque sea con un simple "hecho" o "buen punto, lo cambio". Deja claro que lo has leído y tenido en cuenta.
- **Si no estás de acuerdo, explica por qué**, con argumentos técnicos, no a la defensiva. A veces el revisor tiene razón, a veces falta contexto que tú sí tienes — la conversación es para eso.
- **Haz los cambios en nuevos commits sobre la misma rama**, no reescribas el historial a mitad de review (esto puede complicar que el revisor vea qué ha cambiado desde su último comentario).

```bash
# Después de ajustar el código según los comentarios:
git add .
git commit -m "Ajusta validación según comentarios de review"
git push
```

Esto añade el cambio a la misma PR automáticamente, sin necesidad de abrir una nueva.

## Un ejemplo de respuesta bien manejada

> **Revisor:** "¿Por qué usas un `for` aquí en lugar de `.map()`? Sería más consistente con el resto del archivo."
>
> **Tú:** "Buen punto, no me había fijado en el resto del archivo. Lo cambio a `.map()`."

Corto, directo, sin dramatismo. Así es como debería sentirse la mayoría de los intercambios en una review.

## Cómo se rompe esto

El error típico de quien empieza es tomarse los comentarios de review como una crítica personal, y responder a la defensiva o, peor, ignorarlos. Esto genera fricción innecesaria y ralentiza el proceso. Una review no está evaluando tu valía como programador, está evaluando ese código concreto, en ese momento concreto.

## Para ir más lejos

Con el tiempo, tú también vas a revisar código de otras personas. La misma regla aplica al revés: comenta siempre pensando en ayudar a que el código mejore, no en demostrar que has encontrado un fallo. Un buen comentario de review explica el "por qué", no solo el "qué está mal".

---

📹 *Vídeo relacionado: [pendiente]*
