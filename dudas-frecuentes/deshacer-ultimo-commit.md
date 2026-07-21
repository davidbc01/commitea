# "Quiero deshacer mi último commit"

> **Lo que te vas a llevar:** las distintas formas de deshacer un commit, y cuál usar según lo que realmente quieras conseguir.

## Antes de nada: "deshacer" puede significar varias cosas

Esta es la clave de esta duda. Cuando alguien dice "quiero deshacer mi último commit", en realidad puede querer decir cosas distintas:

1. Quiero que el commit desaparezca, pero conservar mis cambios para corregirlos y volver a hacer commit.
2. Quiero que el commit desaparezca del historial, pero mis cambios se queden en el working directory sin preparar (sin staging).
3. Quiero que el commit desaparezca **y** que los cambios que contenía también desaparezcan por completo.

Cada una tiene su comando.

## Opción 1: deshacer el commit, mantener los cambios en staging

```bash
git reset --soft HEAD~1
```

El commit desaparece del historial, pero todo lo que contenía sigue en la staging area, listo para que corrijas el mensaje o añadas algo más y vuelvas a hacer commit.

## Opción 2: deshacer el commit, mantener los cambios sin preparar

```bash
git reset HEAD~1
```

(Este es el comportamiento por defecto de `git reset`, equivalente a `--mixed`.) El commit desaparece, y los cambios vuelven al working directory, como si acabaras de modificar los archivos pero no hubieras hecho `add` todavía.

## Opción 3: deshacer el commit y descartar los cambios por completo

```bash
git reset --hard HEAD~1
```

Aquí no hay marcha atrás fácil: el commit desaparece y los cambios que contenía se pierden. Úsalo solo cuando estés seguro de que no quieres nada de ese commit.

## ¿Y si ya hice push del commit?

Si el commit ya está en GitHub y otras personas pueden haberlo descargado, usar `reset` y luego forzar el push puede causar problemas a esas personas (su historial local ya no coincidiría con el remoto).

Para este caso existe una alternativa más segura: `git revert`, que en lugar de borrar el commit, **crea uno nuevo que deshace los cambios del anterior**. El historial no se reescribe, solo se añade un commit más:

```bash
git revert HEAD
```

Esto es más lento de leer en el historial (quedan ambos commits, el original y el que lo revierte), pero es mucho más seguro en un repositorio compartido.

## Cómo se rompe esto

El error típico es usar `reset --hard` sin pensarlo, cuando en realidad solo se quería corregir el mensaje del commit o ajustar algo pequeño, perdiendo trabajo que sí se quería conservar. Antes de usar `--hard`, pregúntate: ¿de verdad quiero que estos cambios desaparezcan, o solo quiero rehacer el commit?

Otro error frecuente: usar `reset` sobre commits que **ya están en un repositorio compartido** con otras personas, en lugar de `revert`. Si tienes dudas sobre si alguien más pudo haber descargado ese commit, usa `revert`.

## Para ir más lejos

Si quieres corregir solo el mensaje de tu último commit, sin tocar el contenido, hay un atajo más directo que no necesita `reset`:

```bash
git commit --amend -m "Nuevo mensaje corregido"
```

---

📹 *Vídeo relacionado: [pendiente]*
