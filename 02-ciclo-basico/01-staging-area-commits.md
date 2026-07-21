# Working directory, staging area y commits

> **Lo que te vas a llevar:** entender las tres "zonas" por las que pasa un cambio en Git, que es el concepto que más cuesta al principio.

## El concepto que más lía al empezar

Cuando modificas un archivo en tu proyecto, ese cambio no se guarda en el historial de Git automáticamente. Pasa por tres zonas distintas, y entender esto es la clave para dejar de sentir que Git hace cosas "por arte de magia":

1. **Working directory** (directorio de trabajo): son tus archivos tal cual los ves y editas en tu carpeta. Aquí es donde escribes código.
2. **Staging area** (área de preparación): una zona intermedia donde colocas los cambios que quieres que formen parte del próximo commit.
3. **Repositorio** (historial): una vez haces commit, el cambio queda guardado permanentemente en el historial de Git.

Una forma de verlo: el *working directory* es tu mesa de trabajo, la *staging area* es una bandeja donde vas dejando lo que ya has decidido entregar, y el *commit* es cuando entregas esa bandeja de forma oficial y queda registrado que la entregaste.

## Por qué existe una zona intermedia

Podría parecer un paso innecesario: ¿por qué no guardar directamente los cambios sin pasar por esa "bandeja"?

La staging area te da **control**. Puedes modificar varios archivos a la vez, pero decidir que solo algunos de esos cambios formen parte de este commit, dejando el resto para más adelante. Esto te permite hacer commits pequeños y ordenados, en lugar de mezclar cambios que no tienen relación entre sí.

## Un ejemplo real

Imagina que has modificado dos archivos: `index.html` (arreglaste un botón) y `notas.txt` (apuntes personales que no quieres subir todavía).

```bash
git status
```

```
Changes not staged for commit:
        modified:   index.html
        modified:   notas.txt
```

Ambos están en el *working directory*, modificados pero no preparados. Si solo quieres incluir `index.html` en el commit:

```bash
git add index.html
```

Ahora `index.html` está en la staging area, listo para el commit, mientras que `notas.txt` sigue fuera:

```bash
git status
```

```
Changes to be committed:
        modified:   index.html

Changes not staged for commit:
        modified:   notas.txt
```

Y para completar el commit con lo que está en la staging area:

```bash
git commit -m "Arreglo el botón de envío"
```

`notas.txt` sigue sin estar en el historial, tal y como querías.

## Cómo se rompe esto

El error típico es usar `git add .` (el punto añade todo lo modificado) sin pensarlo, y acabar metiendo en el commit archivos que no querías incluir (apuntes personales, archivos de configuración local, credenciales...). Esto es especialmente peligroso si el repositorio es público.

Antes de hacer commit, es buena costumbre revisar con `git status` (o incluso `git diff`) qué vas a incluir exactamente, en lugar de dar por hecho que `add .` va a coger solo lo que tú tenías en mente.

## Para ir más lejos

Si ya hiciste `git add` de un archivo por error y quieres sacarlo de la staging area (sin perder el cambio, solo devolverlo al *working directory*), puedes usar:

```bash
git restore --staged archivo.txt
```

---

📹 *Vídeo relacionado: [pendiente]*
