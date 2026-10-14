---
name: nuevo-laboratorio
description: Crea un problema nuevo en laboratorios-y-simulaciones, el sitio de R en el navegador de la Nueva Somosaguas. Úsala cuando pidan un laboratorio, un problema o una simulación para ese sitio.
---

# Nuevo laboratorio

Un laboratorio es una carpeta `problemas/NN-nombre-corto/` del repositorio [laboratorios-y-simulaciones](https://github.com/nuevasomosaguas/laboratorios-y-simulaciones), con `index.qmd` y `pruebas.R`. El formato lo fijan tres archivos de ese repositorio: léelos antes de empezar. `README.md` da el procedimiento, `_plantilla/` los campos y los bloques, y `.github/pull_request_template.md` la lista que tiene que cumplir el resultado. Esta guía añade lo que esos archivos no dicen.

## Pasos

1. **Situarte.** Trabaja en un clon al día de laboratorios-y-simulaciones. Lista `problemas/`: el número es el siguiente libre y el nombre corto sale del título, en minúsculas y con guiones. Si un problema ya trata el tema, propón ampliarlo antes de escribir otro. Hecho cuando tienes número, nombre y la seguridad de que el tema no está.

2. **Las fuentes.** Cada dato sobre la obra o el autor se comprueba en una fuente primaria: el PDF, la página oficial, el registro de Crossref (`curl https://api.crossref.org/works/DOI`). Nada de memoria. Los datos externos se congelan en un archivo de la carpeta. Arriba de `index.qmd`, un comentario HTML dice de dónde salen (URL y fecha de descarga), cómo se procesaron y su SHA-256 (`sha256sum`). Si los datos son de personas reales, se anonimizan desde el principio, y la clave que las identifica no entra en el repositorio. Hecho cuando cada cifra y cada cita que vas a usar tienen su fuente comprobada.

3. **La solución primero.** Escribe el código completo y ejecútalo con `Rscript`. El modelo se diseña para el mecanismo, no para el resultado: si el resultado esperado no sale, el problema cuenta lo que sale. Usa R base, o paquetes que webR sabe instalar. Tiene que tardar pocos segundos, porque webR es varias veces más lento que R nativo. Con azar, `set.seed()` con un año que venga a cuento. Hecho cuando corre rápido y tienes anotadas las cifras que da.

4. **El enunciado.** Copia `_plantilla/` y rellena `index.qmd`:
   - El título es una pregunta o una paradoja, y la `description`, una frase que dé ganas de abrirlo.
   - Enunciado: quién estudió el fenómeno, cuándo y por qué sorprende. Después el modelo o los datos, con lo justo para leer el código. **Tu tarea** va numerada: qué completar y qué mirar en el resultado.
   - Uno o dos huecos `______` en las líneas que enseñan el mecanismo. La fontanería queda escrita.
   - «Qué está pasando»: las cifras del paso 3, el mecanismo, dónde más aparece y las referencias completas.
   - `lectura`: enlaza a `https://nuevasomosaguas.github.io/biblioteca.html#clave` solo obras del núcleo de la biblioteca, las que tienen `estrato` en `website/biblioteca.bib`. Una obra del área secundaria enlaza a la clave de su campo `cuelga`, y una que no está en la biblioteca va sin enlace. Las altas en la biblioteca siguen su propio procedimiento, en `website/CLAUDE.md`.
   - `categories`: de la lista de la plantilla. `semana`, solo si el problema encaja de verdad con esa semana del bootcamp.

5. **La comprobación.** Comprueba las funciones del alumno con casos propios, a través de `.envir_result`, para que el mensaje diga qué falla sin dar la solución. En `pruebas.R` van `falla(inicio)`, un `falla()` por cada error típico que se te ocurra y al menos un `pasa()` con una variante válida. Hecho cuando `Rscript probar.R problemas/NN-nombre-corto` termina en «Todo en orden».

6. **El repaso.** Cada número del enunciado, de los mensajes y de «Qué está pasando» coincide con lo que da la solución, ejecutada de nuevo tras el último cambio. Repasa el estilo de abajo y la lista del pull request.

7. **El commit.** El mensaje va en castellano: el título del problema, dos puntos y lo que muestra, con sus cifras clave (mira `git log`). Sin firma ni `Co-Authored-By`. El push y el pull request, solo si te los piden.

## Estilo

- Coma decimal en la prosa y en los mensajes: 0,65. En el código de los mensajes, `format(x, big.mark = ".", decimal.mark = ",")`.
- Porcentajes pegados al número: 50%, 4,4%. En el código, `paste0(round(x), "%")`.
- Millares con punto: 20.000 euros, 4.000 personas. Los años van sin punto (1977), y las cantidades de dinero llevan «euros».
- Los literales del código de R se quedan como en R: `0.65`, `20000`.
- En los temas políticos, ningún partido por su nombre y los argumentos de los dos lados: pobreza relativa y anclada, recaudación estática y dinámica.
- Referencias: Apellido, A. y Apellido, B. (año). Título. *Revista*, volumen(número), páginas.
