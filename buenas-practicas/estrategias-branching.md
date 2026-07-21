# Estrategias de branching (Git Flow vs trunk-based)

> **Lo que te vas a llevar:** conocer las dos estrategias más comunes para organizar ramas en un proyecto, y cuándo tiene sentido cada una.

## Por qué hace falta una estrategia

Ya sabes crear ramas, fusionarlas y colaborar con pull requests. Lo que falta es un criterio compartido: **¿qué rama representa lo que está en producción? ¿Cuándo se crea una rama nueva? ¿Cuándo se fusiona?**

Sin un criterio claro, cada persona del equipo hace las cosas a su manera, y el repositorio se vuelve difícil de seguir. Aquí vemos las dos estrategias más extendidas.

## Git Flow

Es una estrategia con varias ramas permanentes y roles bien definidos:

- **`main`**: refleja siempre lo que está en producción.
- **`develop`**: rama de integración, donde se junta el trabajo antes de pasar a producción.
- **`feature/*`**: una rama por cada funcionalidad nueva, que nace de `develop` y vuelve a `develop` al terminar.
- **`release/*`**: cuando `develop` está lista para publicarse, se prepara en una rama de release (ajustes finales, versión...) antes de fusionarse a `main`.
- **`hotfix/*`**: para arreglos urgentes directamente sobre producción, que después se propagan también a `develop`.

```
main:     ---A-------------F-----------
                             \
develop:  ---B---C---D---E---/---G-----
                \       /
feature/x:       \-----/
```

**Cuándo tiene sentido:** proyectos con ciclos de publicación planificados (versiones concretas, no despliegue continuo), o con requisitos de estabilidad altos donde conviene un proceso de release formal.

**Cuándo se queda corto:** proyectos pequeños o con despliegue continuo — toda esta estructura añade complicación que no aporta valor si publicas cambios varias veces al día.

## Trunk-based development

Estrategia mucho más simple: **una sola rama principal** (`main` o `trunk`), sobre la que todo el mundo trabaja con ramas de vida muy corta.

- Se crea una rama para un cambio pequeño.
- Se fusiona a `main` rápido (en horas o pocos días, no semanas).
- `main` se despliega constantemente, apoyándose en buenas prácticas como tests automáticos y *feature flags* (activar/desactivar funcionalidades sin necesidad de ramas separadas) para gestionar cambios que aún no están listos para todo el mundo.

```
main:  ---A---B---C---D---E---F---
              \       /
               \-----/
              (rama corta)
```

**Cuándo tiene sentido:** equipos con buena cobertura de tests e integración continua, proyectos con despliegue frecuente, equipos pequeños o de tamaño medio donde la coordinación es más ágil.

**Cuándo se queda corto:** si el equipo no tiene disciplina de tests o revisión rápida, fusionar tan seguido a `main` puede introducir inestabilidad constante.

## ¿Cuál elegir?

Para un proyecto personal o un equipo pequeño con despliegue frecuente (que es probablemente tu caso si estás empezando), **trunk-based** suele ser más sencillo y con menos fricción. Git Flow tiene más sentido cuando el proyecto tiene ciclos de versión bien definidos, o requisitos de estabilidad que justifican el proceso extra.

No hace falta adoptar ninguna de las dos al pie de la letra — muchos equipos usan versiones simplificadas, quedándose solo con las partes que les resultan útiles.

## Cómo se rompe esto

El error típico es adoptar Git Flow completo en un proyecto pequeño "porque es lo que se hace en las empresas grandes", y acabar con una carga de proceso (ramas de release, hotfix, develop...) que no aporta nada si el equipo son dos personas desplegando varias veces por semana. La estrategia debe adaptarse al proyecto, no al revés.

## Para ir más lejos

Independientemente de la estrategia, una regla que casi siempre ayuda: **cuanto más tiempo vive una rama sin fusionarse, más probable es que tenga conflictos difíciles de resolver al integrarla.** Ramas cortas, aunque no sigas trunk-based al 100%, casi siempre son buena idea.

---

📹 *Vídeo relacionado: [pendiente]*
