# Fork vs clone (la confusión típica de principiantes)

> **Lo que te vas a llevar:** entender la diferencia entre hacer fork y hacer clone, y saber cuándo usar cada uno.

## Por qué se confunden tanto

Ambos conceptos tienen que ver con "conseguir una copia de un proyecto", y por eso se mezclan fácilmente al principio. Pero resuelven problemas distintos, y elegir mal puede meterte en líos cuando quieras colaborar.

## Qué es `clone`

Ya lo vimos en fundamentos: `git clone` descarga un repositorio a tu ordenador, junto con todo su historial.

```bash
git clone https://github.com/usuario/proyecto.git
```

Lo importante aquí: **sigue siendo el mismo repositorio**, solo que ahora tienes una copia local. Si tienes permisos de escritura sobre ese repositorio (por ejemplo, es tuyo, o eres colaborador directo), puedes hacer `push` de tus cambios sin problema.

## Qué es `fork`

Un fork es distinto: es una **copia completa del repositorio, pero en tu propia cuenta de GitHub**. No se hace con un comando de Git, se hace desde la web de GitHub, pulsando el botón "Fork" en el repositorio que te interesa.

El resultado es un nuevo repositorio, en tu perfil, que es una copia independiente del original — pero que mantiene una relación con él (GitHub sabe de qué proyecto proviene).

## ¿Cuándo usar cada uno?

Aquí está la clave que suele fallar a quien empieza:

- **Tienes permisos de escritura sobre el repo** (es tuyo, o te han añadido como colaborador) → usas `clone` directamente. No necesitas fork.
- **No tienes permisos de escritura** (es un proyecto open source de otra persona, y quieres contribuir) → primero haces **fork** (para tener tu propia copia donde sí tienes permisos), y luego haces **clone** de tu fork a tu ordenador.

Es decir, para contribuir a un proyecto que no es tuyo, normalmente haces ambas cosas, en este orden: fork en GitHub, clone de tu fork en tu ordenador.

```bash
# Después de hacer fork desde la web de GitHub:
git clone https://github.com/tu-usuario/proyecto.git
```

## Un ejemplo real

Quieres contribuir a un proyecto open source que te gusta, pero no eres colaborador de ese repositorio.

1. Entras en GitHub, pulsas "Fork". Ahora tienes `github.com/tu-usuario/proyecto`, una copia en tu cuenta.
2. Clonas tu fork a tu ordenador y haces tus cambios ahí.
3. Subes tus cambios a tu fork con `git push`.
4. Desde GitHub, abres una **pull request** proponiendo que tus cambios se incorporen al proyecto original.

Ese último paso lo veremos en detalle en la siguiente entrada.

## Cómo se rompe esto

El error típico es intentar hacer `git push` directamente sobre un repositorio del que solo has hecho `clone`, sin ser colaborador y sin haber hecho fork antes. GitHub te devolverá un error de permisos (algo como `Permission denied` o `403`), porque simplemente no tienes autorización para escribir ahí. La solución no es forzar el push, es hacer fork primero.

## Para ir más lejos

Si haces fork de un proyecto y el original recibe cambios nuevos después, tu fork **no se actualiza automáticamente**. Tendrás que sincronizarlo manualmente añadiendo el repositorio original como un remoto adicional (normalmente llamado `upstream`) y trayendo sus cambios. Es un caso algo más avanzado que veremos en dudas frecuentes si hace falta.

---

📹 *Vídeo relacionado: [pendiente]*
