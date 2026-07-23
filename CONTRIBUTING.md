# Contribuir a Commitea

Gracias por pensar en aportar algo. Este repo funciona mejor cuantas más
dudas reales recoja, así que cualquier contribución —desde arreglar una
errata hasta añadir un artículo entero— es bienvenida.

## Antes de nada

- Si es un cambio pequeño (una errata, un enlace roto, un ejemplo mal
  explicado), abre directamente una pull request.
- Si es un artículo nuevo o un cambio grande, mejor abre primero un issue
  para comentarlo. Así evitamos que trabajes en algo que no encaje o que
  ya esté en marcha.

## Cómo está organizado el contenido

```
commitea/
├── 01-fundamentos/          Curso base, en orden
├── 02-ciclo-basico/
├── 03-ramas/
├── 04-colaboracion-github/
├── dudas-frecuentes/        Casos concretos, sin orden fijo
└── buenas-practicas/        Para cuando ya controlas lo básico
```

- Si tu propuesta es un caso concreto que le pasa a la gente ("se me ha
  colado un commit en la rama que no era", "no sé deshacer un merge"),
  va en `dudas-frecuentes/`.
- Si es una recomendación de cómo hacer las cosas bien (convenciones,
  estrategias), va en `buenas-practicas/`.
- Los bloques numerados (`01` a `04`) son el recorrido guiado para quien
  empieza de cero. Si tu propuesta encaja ahí, coméntalo en el issue antes
  de escribir nada — el orden y la progresión importan en esos bloques.

## El formato de cada artículo

Todos los archivos siguen la misma estructura. Cópiala tal cual:

```markdown
# Título del artículo

> **Lo que te vas a llevar:** el concepto en una frase.

## [Sección explicando el problema o contexto]

Explicación corta y clara, sin rodeos.

## [Sección con el ejemplo]

Ejemplo real, con comandos y el resultado esperado:

\`\`\`bash
git comando --flag
\`\`\`

## Cómo se rompe esto

El error típico que se comete con esto, y cómo evitarlo o arreglarlo.

## Para ir más lejos

(Opcional) Algo relacionado para quien quiera profundizar.

---

📹 *Vídeo relacionado: [pendiente]*
```

Un par de reglas de estilo:

- Tono cercano, como si se lo explicaras a un compañero — no como
  documentación técnica fría.
- Ejemplos con contexto real, no solo el comando en abstracto.
- Nombra el archivo en minúsculas y con guiones, sin acentos ni ñ
  (`rebase-vs-merge.md`, no `Rebase Vs. Merge.md`).
- Si el archivo va en uno de los bloques numerados (`01-fundamentos/`,
  etc.), el nombre lleva el número de orden delante
  (`01-que-es-git.md`). Si va en `dudas-frecuentes/` o
  `buenas-practicas/`, no lleva número.

## Cómo hacer la pull request

1. Haz fork del repo y clónalo.
2. Crea una rama descriptiva (`git checkout -b duda/rama-equivocada`).
3. Añade o edita el `.md` correspondiente.
4. Si es un artículo nuevo, añade también su entrada en la web —
   pregúntame en el issue y te digo cómo, ya que ese repo es privado.
5. Abre la PR describiendo qué cambia y por qué.

Cualquier duda, abre un issue y lo hablamos ahí.
