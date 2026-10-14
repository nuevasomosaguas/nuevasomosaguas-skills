---
name: alta-biblioteca
description: Añade un libro o un artículo al área secundaria de la biblioteca de la Nueva Somosaguas como propuesta, y cura las propuestas en una sesión de revisión con una lista fija de criterios. Úsala cuando pidan añadir, proponer o recomendar una obra para la biblioteca, cuando peguen recursos nuevos para ella, o cuando abran una sesión de revisión de propuestas.
---

# Alta en la biblioteca

La biblioteca vive en el repositorio [website](https://github.com/nuevasomosaguas/nuevasomosaguas.github.io), en `biblioteca.bib`. Sus reglas están en dos sitios: la cabecera de `biblioteca.bib`, que define cada campo, y `CLAUDE.md`, que da los pasos de un alta y de una sesión de revisión. Léelos antes de empezar: `CLAUDE.md` no se carga solo si la sesión empezó en otra carpeta. Esta guía añade lo que esos archivos no dicen: el orden de trabajo y los criterios con que se revisa una propuesta.

Hay dos momentos, y nunca van en la misma sesión salvo aprobación directa: **el alta**, que deja la obra en `propuesta`, y **la revisión**, que decide su destino.

## El alta

1. **Situarte.** Trabaja en un clon al día de website, con el árbol limpio. Hecho cuando `git status` no muestra cambios.

2. **Los pasos de `CLAUDE.md`.** Sigue sus nueve pasos en orden, de los duplicados a la comprobación con `refs.R`. Para elegir `cuelga`, lee la ficha de las candidatas (`mecanismo`, `aparato`, `funcion`) y las obras que ya cuelgan de cada una: el motivo tiene que decir algo que las hermanas no digan ya. Hecho cuando la entrada está al final de `biblioteca.bib` con `estado = {propuesta}` y `refs.R` la carga sin error.

3. **El commit.** Uno por alta o por tanda, sin tocar el registro de cambios ni las rutas. El mensaje empieza por «Propuesta:» y dice qué cuelga de qué, con qué papel y por qué: «Propuesta: Boserup (1965) cuelga de Clark como contraste y crítica: la presión demográfica impulsa la intensificación agrícola». Sin firma ni `Co-Authored-By`. El push, solo si lo piden.

**Aprobación directa.** Si el responsable dice que aprueba el alta «directamente», la obra entra ya `curada`: haz la revisión de abajo sobre ella en la misma sesión, y el commit dice «curada por aprobación directa».

## La revisión

La abre el responsable de forma explícita. Lista las propuestas con la orden de `CLAUDE.md` y pasa cada una por los ocho criterios. Ninguno se da por bueno porque lo dijera el alta: se comprueba otra vez.

| # | Criterio | Pasa si |
|---|---|---|
| 1 | Duplicado | No está ya en el núcleo ni en el área secundaria, tampoco en otra edición o traducción. |
| 2 | Identificador | El doi responde en Crossref, o el isbn en Open Library, con el mismo título, año y autores; o la entrada va sin enlace porque no hay ninguno. |
| 3 | Edición | Es la más reciente de la versión que se recomienda, y `origdate` guarda la original si difiere. |
| 4 | Cuelga | Ninguna otra obra del núcleo deja un motivo más concreto. |
| 5 | Papel | Cumple la definición de `CLAUDE.md`: *fuente original* solo si la idea nació ahí, *contraste* solo frente a la obra o su rama. |
| 6 | Motivo | Una frase en castellano que nombra la relación concreta, no repite el papel y es texto plano. |
| 7 | Aporte | Añade un mecanismo, un aparato, un caso o un contraste que ni la obra del núcleo ni sus hermanas curadas dan ya. Describir sin mecanismo no basta. |
| 8 | Nivel y descriptor | El nivel es coherente con las hermanas, y el descriptor reutiliza uno existente si encaja. |

El destino sale de la tabla:

- **Curada**, si pasa los ocho.
- **Corregida y curada**, si solo falla en 3, 4, 5, 6 u 8: corrige la entrada y anota qué cambió.
- **Borrada**, si falla en 1 o en 7. Si falla en 2 y el identificador no se puede arreglar, la obra se cura sin enlace, y el registro de cambios lo dice.

Antes de escribir nada, presenta al responsable una tabla por propuesta, con los ocho criterios, un «sí» o la razón del «no», y el destino propuesto. Él decide; aplica solo lo que apruebe.

Por cada obra curada:

1. `estado = {curada}` en `biblioteca.bib`.
2. Una viñeta al final de «Desde v1.1» en `biblioteca-cambios.qmd`, con este orden: autores y año, *título* en cursiva, la edición si no es la original («en la reedición de Routledge de 2017»), «cuelga de Apellido como papel», dos puntos, lo que aporta; después la ruta en la que entra, si entra; y al final el identificador: «Va con su DOI, comprobado en Crossref», «Va con su ISBN, comprobado en Open Library» o «va sin enlace», con la razón.
3. El recuento de la primera línea de «Desde v1.1» igual a `n_secundarias`.
4. Las rutas de `biblioteca-rutas.qmd` cuyo tema toca la obra: si entra en una, su clave va en el orden de lectura y su papel en el párrafo. Una ruta nueva solo con las condiciones de `CLAUDE.md`.

La sesión está cerrada cuando la orden de listado no devuelve nada y `Rscript biblioteca-secundaria/obras.R && Rscript -e 'source("refs.R")'` termina sin error. Si renderizas en local, restaura `_site/` como dice `CLAUDE.md`.

El commit empieza por «Curada:» si es una obra, o por «Sesión de revisión:» si son varias, y dice cuántas se curaron, cuáles se corrigieron y cuáles se borraron, y el nuevo recuento del área secundaria. Sin firma ni `Co-Authored-By`. El push, solo si lo piden.

## Estilo

- Coma decimal: 0,65. Porcentajes pegados: 50%. Millares con punto: 20.000 euros; los años sin punto.
- El motivo y la viñeta nombran la obra del núcleo por su autor («cuelga de Clark»), no por su clave.
- Los títulos en la lengua de la edición que entra; la original, en `origtitle`.
