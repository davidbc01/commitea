# rebase vs merge (cuándo usar cada uno)

> **Lo que te vas a llevar:** entender qué hace `rebase` de forma distinta a `merge`, y en qué situaciones conviene cada uno.

## El mismo problema, dos soluciones distintas

Tanto `merge` como `rebase` resuelven la misma necesidad: traer a tu rama los cambios que hay en otra (normalmente, traer `main` actualizado a tu rama de trabajo). La diferencia está en **cómo** lo hacen y qué aspecto queda en el historial.

## Cómo funciona `merge` (repaso)

Ya lo vimos: `merge` junta dos ramas creando un commit de merge que las combina, conservando ambas historias tal cual pasaron:

```
A --- B --- C   (main)
       \     \
        D --- E   commit de merge
       (feature/login)
```

El historial muestra fielmente que hubo dos líneas de trabajo en paralelo que se juntaron en un punto.

## Cómo funciona `rebase`

`rebase` hace algo distinto: **reescribe** tus commits como si los hubieras hecho a partir del último estado de la otra rama, en lugar de crear un commit que junte ambas historias.

```bash
git checkout feature/login
git rebase main
```

Antes:
```
A --- B --- C   (main)
       \
        D --- E   (feature/login)
```

Después del rebase:
```
A --- B --- C   (main)
             \
              D' --- E'   (feature/login)
```

Fíjate en algo importante: `D'` y `E'` no son los mismos commits que `D` y `E`, son **nuevos commits** con el mismo contenido, pero un historial distinto por detrás. El resultado es un historial lineal, como si tu trabajo hubiera empezado justo después de `C`, sin ninguna bifurcación visible.

## ¿Cuál usar?

Aquí no hay una respuesta única, pero sí una guía práctica:

- **Usa `merge`** cuando trabajas en una rama compartida con más gente, o cuando quieres que el historial refleje honestamente que hubo trabajo en paralelo. Es más seguro por defecto.
- **Usa `rebase`** cuando quieres mantener tu historial personal limpio y lineal, **antes de compartir esos commits con nadie** (por ejemplo, para limpiar tu propia rama de feature antes de abrir la pull request).

## La regla de oro: nunca rebases historial ya compartido

Esta es la parte más importante de esta entrada. Como `rebase` reescribe commits (crea nuevos con distinto identificador), si haces rebase sobre commits que **ya has subido y que otras personas pueden haber descargado**, les rompes el historial: sus commits locales ya no coincidirán con los tuyos.

**Rebase: seguro en tu rama personal, antes de compartirla. Peligroso en ramas compartidas donde ya ha hecho pull otra gente.**

## Cómo se rompe esto

El error típico es hacer `rebase` sobre una rama en la que ya está trabajando alguien más, y luego forzar el push. La otra persona, al hacer `pull`, se encuentra con conflictos extraños y un historial que no coincide con el que tenía, sin entender por qué. Si tienes dudas sobre si alguien más depende de esos commits, usa `merge`.

## Para ir más lejos

Existe una variante llamada `rebase -i` (interactivo), que además de reordenar tu historial sobre otra rama, te permite reescribir, combinar o reordenar tus propios commits antes de compartirlos, para dejar un historial más limpio. Es una herramienta potente, pero conviene dominar primero `rebase` normal antes de meterse ahí.

---

📹 *Vídeo relacionado: [pendiente]*
