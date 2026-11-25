# Nueva Somosaguas

La carpeta raíz agrupa los quince repositorios de la Nueva Somosaguas. No es un repositorio Git; cada subcarpeta lo es. El archivo canónico vive en `nuevasomosaguas-skills/AGENTS.md` y se enlaza desde la raíz como `AGENTS.md` y `CLAUDE.md`.

## Repositorios

| Carpeta | Contenido |
|---|---|
| `website` | Web principal en Quarto (`nuevasomosaguas.github.io`), biblioteca viva (`biblioteca.bib`, `refs.R`), rutas de lectura y manual de bolsillo. |
| `laboratorios-y-simulaciones` | Problemas interactivos de R en el navegador (Quarto Live y webR), en `problemas/NN-slug/`, con `probar.R` y `_plantilla/`. |
| `bootcamp` | Web en Hugo (`themes/somosaguas`) y doce guías semanales de Julia, terminal y Typst (`semana-01/` a `semana-12/`) con sus pruebas. |
| `bootcamp-soluciones` | **Privado.** Soluciones de referencia del bootcamp y `./comprobar.sh ../bootcamp`. Prohibido filtrar su contenido a repositorios públicos. |
| `entorno` | Imagen Debian 13 (Codespaces, devcontainer e ISO en vivo en `distribucion/`), dependencias congeladas y `./verificar_entorno.sh`. |
| `corpus-rag-biblioteca` | Consulta local de la biblioteca viva con Ollama, `sqlite-vec` y `sympy` (`inventariar.py`, `rag.py`, `comprobar.py`, `test_rag.py`). |
| `nuevasomosaguas-skills` | Este archivo y las guías de tareas (`skills/alta-biblioteca/SKILL.md`, `skills/nuevo-laboratorio/SKILL.md`). |
| `somosaguas-quarto-theme` | Extensión de Quarto (HTML y Typst) con la tipografía y estilos de la facultad. |
| `somosaguas-typst-template` | Paquete de Typst con EB Garamond, notas al margen y diseño de Nueva Somosaguas. |
| `somosaguas-hugo-theme` | Tema de Hugo para webs personales y el bootcamp. |
| `somosaguas-ggplot2` | Paquete de R con `theme_somosaguas()` y la paleta gráfica. |
| `somosaguas-makie` | Paquete de Julia con `tema_somosaguas()` y la misma paleta. |
| `somosaguas-vscode` | Extensión de VS Code para citar con `@` desde todas las bibliotecas y usar fragmentos de Typst. |
| `fdrmania` | Micrositio satírico en HTML 3.2 sobre control de tasa de falsos descubrimientos. |
| `ns-for-ie` | Micrositio estático con cinco preguntas de acceso inverso. |

### Fuentes de verdad y guías detalladas

- **Biblioteca:** `website/biblioteca.bib` manda sobre todo el catálogo. El núcleo tiene tope de 150 obras (con campo `estrato`) y es la única capa con ancla propia (`biblioteca.html#<clave>`). Una obra del área secundaria (`propuesta` o `curada`) enlaza a la ficha de la obra del núcleo de la que cuelga.
- **Dependencias del entorno:** `entorno/.devcontainer/Dockerfile` (con `ARG SNAPSHOT` para CRAN), `entorno/.devcontainer/julia/Manifest.toml` y `entorno/.devcontainer/python/uv.lock` congelan las versiones del semestre. Ningún proyecto instala paquetes flotantes.
- **Procedimientos específicos:** no dupliques ni improvises los pasos de tareas regladas. Lee antes `website/CLAUDE.md` (biblioteca, revisión y rutas), `nuevasomosaguas-skills/skills/alta-biblioteca/SKILL.md`, `nuevasomosaguas-skills/skills/nuevo-laboratorio/SKILL.md`, `laboratorios-y-simulaciones/_plantilla/` y `laboratorios-y-simulaciones/.github/pull_request_template.md`.

## Voz y estilo editorial

### Muestras de referencia

- **Explicación conceptual:** «El mecanismo es cómo ocurre algo, no sólo qué ocurre. Es la diferencia entre saber que la aspirina quita el dolor de cabeza y saber cómo actúa en el cuerpo. La Nueva Somosaguas enseña a hacer tres cosas con cada mecanismo: formularlo con precisión, contrastarlo con datos y reconstruirlo con código.»
- **Honestidad y escala:** «El grado completo no es para todos: pide años de trabajo, una base matemática que se construye con esfuerzo y mucha disciplina. Pero no hace falta cursarlo íntegro para aprovecharlo. Una ruta de lectura te da en pocas semanas una visión seria de un tema como la demografía, un laboratorio te enseña en una tarde cómo funciona un mecanismo y el manual de bolsillo te sirve mañana mismo para detectar un mal argumento. Elige lo que se ajuste a tu tiempo y tus ganas.»
- **Instrucciones directas:** «Doce semanas de nivelación, a guía por semana. Todo se hace con Julia y la terminal: entregas un script que debe pasar limpio las pruebas automáticas y lo defiendes en la pizarra.»
- **Microcopy:** «Destruyendo el p-hacking desde 1995» / «La prueba de acceso inversa: optimizado para IE, elija usted cuál».

### Reglas de redacción

1. **Arranca por lo concreto.** Empieza por la pregunta, el problema o la acción del estudiante, nunca por definiciones previas ni etiquetas burocráticas («bootcamp propedéutico»).
2. **Frases cortas.** Si una oración encadena más de dos subordinadas o incisos, pártela en dos frases seguidas.
3. **Castellano natural de aula y taller.** Usa verbos cotidianos («pasar limpio las pruebas», «coger músculo», «echar un ojo») en lugar de calcos del inglés («canalización», «comprometer», «gates»).
4. **Honestidad sin humo.** Reconoce la dificultad real antes de explicar cómo abordarla. Cierra con apelaciones directas y sobrias, nunca con eslóganes motivacionales.
5. **Economía verbal.** Aplica los principios de George Orwell en *Politics and the English Language*: prefiere la palabra corta a la larga, corta toda palabra que sobre, usa la voz activa y rompe cualquier regla antes que escribir una frase artificial.
6. **Comentarios de código secos.** En R, Julia, Python o shell, deja solo comentarios breves y útiles. Borra lo obvio o solemne que repite el código. En los bloques `#| solution: true` de `laboratorios-y-simulaciones` no escribas comentarios `# ` dentro del código (en `#| caption: "Tu código"` sí caben notas breves).

### Qué cortar al editar

- Fórmulas de contraste artificial como «no es X, sino Y» o «no solo X, sino también Y».
- Relleno burocrático: «de forma/de manera», «a través de», «en términos de», «con X como único entorno» o «integración continua» en prosa corriente.
- Adverbios en `-mente` que no añadan precisión técnica.
- Rayas explicativas (`—`) heredadas del inglés cuando basta con una coma, dos puntos o un punto.
- Subordinadas encadenadas que obligan a releer la frase.

### Cifras, citas y temas políticos

- **Decimales:** coma en prosa y en mensajes al estudiante (`0,65`); punto en literales de código (`0.65`, `20000`). En mensajes de R usa `format(x, big.mark = ".", decimal.mark = ",")`.
- **Porcentajes:** pegados al número (`50%`, `4,4%`). En R, `paste0(round(x), "%")`.
- **Millares, años y dinero:** millares con punto (`20.000 euros`, `4.000 personas`), años sin punto (`1977`) y cantidades de dinero con «euros».
- **Referencias en prosa:** `Apellido, A. y Apellido, B. (año). Título. *Revista*, volumen(número), páginas.`
- **Neutralidad política:** no nombres partidos y presenta los argumentos de ambos lados (pobreza relativa y anclada, recaudación estática y dinámica).

## Rigor, fuentes e invariantes

- **Fuentes primarias, nada de memoria.** Verifica cada dato, cita, DOI o ISBN en su fuente: el PDF, la web oficial, Crossref (`curl -s https://api.crossref.org/works/<doi>`), Open Library (`curl -sL https://openlibrary.org/isbn/<isbn>.json`), el INE o el BOE. Si no existe identificador, la entrada va sin enlace y se deja constancia.
- **Datos externos congelados.** Guarda los datos junto al laboratorio o proyecto, con un comentario HTML arriba que indique URL, fecha de descarga, procesado y `sha256sum`. Si provienen de personas reales, anonimízalos desde el origen y deja fuera de Git la tabla de claves.
- **Cifras reproducibles.** Cada número del texto, de los mensajes y de «Qué está pasando» debe coincidir con la salida real del código tras el último cambio. Con azar, fija `set.seed()` o la semilla equivalente con un año que venga a cuento.
- **Qué no tocar en pases editoriales.** Mantén intactos los bloques YAML, las fórmulas matemáticas, el código ejecutable, los comentarios HTML de procedencia, las sumas SHA-256, las citas literales y los términos técnicos consolidados (por ejemplo, *linealmente dependientes*, *estrictamente cóncava*, *parámetros de forma*, *causas fundamentales* o *exoesqueleto cognitivo*). No mezcles cambios de código con ediciones de estilo salvo que se pida.

## Comprobación por repositorio

Quarto no está en el `PATH` por omisión de esta máquina. Antepón `PATH=/usr/lib/rstudio/resources/app/bin/quarto/bin:$PATH` en cualquier orden de `quarto` (también porque `website/biblioteca.qmd` llama a `quarto pandoc` desde R).

- **`website`**
  - Biblioteca: `Rscript biblioteca-secundaria/obras.R && Rscript -e 'source("refs.R")'`
  - Render local: `PATH=/usr/lib/rstudio/resources/app/bin/quarto/bin:$PATH quarto render`
  - Restaurar `_site/` tras render local (lo publica GitHub Actions): `git checkout -- _site && git clean -fdq _site`
- **`laboratorios-y-simulaciones`**
  - Probar un problema: `Rscript probar.R problemas/<slug>` (debe acabar en `Todo en orden.`).
  - Render local: pasa los `.qmd` **de uno en uno** en un bucle (`for f in ...; do PATH=/usr/lib/rstudio/resources/app/bin/quarto/bin:$PATH quarto render "$f" || exit 1; done && rm -rf _site`). Pasar varios archivos en una sola orden falla a partir del segundo.
  - Revisar que ningún bloque `#| solution: true` contenga comentarios `# `.
- **`bootcamp` y `bootcamp-soluciones`**
  - Compilar la web (desde `bootcamp/`): `hugo -d /tmp/bootcamp-check && rm -rf /tmp/bootcamp-check`
  - Pruebas con soluciones de referencia (desde `bootcamp-soluciones/`): `./comprobar.sh ../bootcamp` (la semana 3 falla en el ejercicio 4 por el historial Git).
- **`corpus-rag-biblioteca`**
  - Pruebas: `python3 test_rag.py` (necesita `uv`, `typst`, `pandoc` y `djvulibre`).
- **`entorno`**
  - Dentro del contenedor o la distribución: `./verificar_entorno.sh` (debe responder `Entorno calibrado. Comience a calcular.`).
- **`somosaguas-ggplot2` y `somosaguas-makie`**
  - `Rscript tests/prueba.R` (con el paquete instalado) y `julia --project=. -e 'using Pkg; Pkg.test()'`.

## Git, privacidad y límites

- **Un repo por subcarpeta.** Lanza los comandos de Git dentro de la carpeta afectada o con `git -C <repo>`.
- **Ni `git commit` ni `git push` sin permiso.** Deja los cambios listos en el árbol de trabajo para que el responsable revise el `git diff` y confirme cuando corresponda.
- **Mensajes de commit (cuando se pidan).** En castellano, concretos y sin firma de IA ni líneas `Co-Authored-By`.
- **Fronteras privadas.** Nunca copies, cites ni expongas archivos de `bootcamp-soluciones` en repositorios públicos ni en material para estudiantes. En `corpus-rag-biblioteca`, los libros, el inventario, los índices y la Trituradora quedan siempre fuera de Git.
