# Instalación y configuración inicial

> **Lo que te vas a llevar:** tener Git instalado y configurado correctamente antes de tu primer commit.

## Instalar Git

Git se instala distinto según tu sistema operativo:

**Windows**

Descarga el instalador desde [git-scm.com](https://git-scm.com) y sigue el asistente. Durante la instalación te preguntará varias cosas (editor por defecto, gestión de saltos de línea...); si no tienes claro qué elegir, las opciones que vienen marcadas por defecto funcionan bien para empezar.

**macOS**

Si tienes [Homebrew](https://brew.sh) instalado:

```bash
brew install git
```

Si no, macOS te lo pide instalar automáticamente la primera vez que ejecutas `git` en la terminal (a través de las Herramientas de Línea de Comandos de Xcode).

**Linux**

Depende de tu distribución. En Ubuntu/Debian:

```bash
sudo apt update
sudo apt install git
```

Para comprobar que se ha instalado correctamente, en cualquier sistema:

```bash
git --version
```

Deberías ver algo como `git version 2.4x.x`.

## Configurar tu identidad

Antes de hacer tu primer commit, Git necesita saber quién eres. Esta información se guarda en cada commit que hagas, así que conviene configurarla bien desde el principio:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

El flag `--global` significa que esta configuración se aplica a todos tus proyectos en ese ordenador, no solo al que tengas abierto ahora mismo.

Puedes comprobar que se ha guardado correctamente con:

```bash
git config --global user.name
git config --global user.email
```

## Configurar SSH para GitHub (recomendado)

Para poder subir cambios a GitHub sin que te pida usuario y contraseña cada vez, lo normal es configurar una clave SSH.

**1. Generar la clave** (si no tienes una ya):

```bash
ssh-keygen -t ed25519 -C "tu@email.com"
```

Te pedirá dónde guardarla; con pulsar Enter para aceptar la ruta por defecto es suficiente.

**2. Copiar la clave pública:**

```bash
cat ~/.ssh/id_ed25519.pub
```

Copia todo el contenido que te muestra la terminal.

**3. Añadirla a GitHub:**

Ve a GitHub → Settings → SSH and GPG keys → New SSH key, y pega la clave que copiaste.

**4. Comprobar que funciona:**

```bash
ssh -T git@github.com
```

Si todo está bien, verás un mensaje confirmando que te has autenticado correctamente.

## Cómo se rompe esto

El error típico aquí es configurar `user.email` con un correo distinto al que tienes asociado en tu cuenta de GitHub. Esto no rompe nada técnicamente (los commits se hacen igual), pero **GitHub no reconocerá esos commits como tuyos**: no aparecerán vinculados a tu perfil ni contarán en tu gráfico de contribuciones, aunque técnicamente sean tuyos.

Si esto te pasa, puedes corregirlo simplemente actualizando la configuración con el email correcto para los próximos commits.

## Para ir más lejos

Además de `--global`, puedes configurar valores distintos por proyecto quitando ese flag (`git config user.email "otro@email.com"` dentro de la carpeta del proyecto). Es útil si usas, por ejemplo, un email distinto para proyectos personales y de trabajo.

<!-- --- -->

<!-- 📹 *Vídeo relacionado: [pendiente]* -->
