# Qué es una rama de verdad

> **Lo que te vas a llevar:** entender qué es realmente una rama en Git, más allá de "para hacer cosas nuevas sin tocar lo que ya funciona".

## La explicación superficial (y por qué se queda corta)

Casi todo el mundo te va a decir que una rama sirve "para trabajar en algo nuevo sin afectar al proyecto principal". Es cierto, pero es una explicación de *para qué la usas*, no de *qué es*. Y sin entender qué es de verdad, cuesta razonar sobre qué está pasando cuando algo no sale como esperabas.

## Qué es una rama, técnicamente

Una rama en Git **no es una copia de tus archivos**. Es, simplemente, **una etiqueta que apunta a un commit concreto**.

Cuando haces un nuevo commit estando en una rama, esa etiqueta se mueve automáticamente para apuntar al nuevo commit. Eso es todo. No hay ninguna carpeta duplicada por detrás, ni archivos copiados: solo una referencia que se mueve.

Esto es justo lo que hace que crear una rama en Git sea instantáneo y casi gratuito en espacio, a diferencia de lo que sería, por ejemplo, copiar toda la carpeta del proyecto para "tener una versión aparte".

## Un ejemplo visual

Imagina que tienes este historial en la rama `main`:

```
A --- B --- C   (main)
```

Cada letra es un commit. `main` apunta a `C`, el último.

Si creas una rama nueva:

```bash
git branch feature/login
```

Ahora tienes dos etiquetas apuntando al mismo sitio:

```
A --- B --- C   (main, feature/login)
```

Si te cambias a `feature/login` y haces un commit nuevo:

```bash
git checkout feature/login
# ... editas archivos, haces commit ...
```

```
A --- B --- C   (main)
             \
              D   (feature/login)
```

`main` se queda donde estaba. `feature/login` avanza. Los archivos de tu proyecto solo reflejan el estado de la rama en la que estás en cada momento — Git se encarga de "reescribir" tu carpeta de trabajo cada vez que cambias de rama.

## Por qué importa entenderlo así

Cuando entiendes que una rama es solo una etiqueta que se mueve, cosas que antes parecían magia empiezan a tener sentido: por qué crear ramas es tan rápido, por qué puedes tener decenas de ramas sin que ocupen apenas espacio extra, y por qué "borrar una rama" no borra ningún commit si otra rama (o etiqueta) sigue apuntando a esos mismos commits.

## Cómo se rompe esto

El error típico de quien no tiene esto claro es tener miedo a crear ramas, pensando que es una operación "pesada" o arriesgada. Es justo lo contrario: crear ramas en Git es barato y seguro. El verdadero peligro está en no separar tu trabajo en ramas cuando deberías, mezclando en `main` cosas que todavía no están terminadas o probadas.

## Para ir más lejos

Puedes ver a qué commit apunta exactamente cada rama con:

```bash
git log --oneline --graph --all
```

Esto te muestra visualmente cómo se van separando y en qué commit exacto nació cada rama, algo muy útil cuando el proyecto empieza a tener varias ramas activas a la vez.

---

📹 *Vídeo relacionado: [pendiente]*
