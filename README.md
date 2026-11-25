# nuevasomosaguas-skills

Skills de [Claude Code](https://claude.com/claude-code) para trabajar en los repositorios de la Nueva Somosaguas.

| Skill | Para qué |
|---|---|
| [`nuevo-laboratorio`](skills/nuevo-laboratorio/SKILL.md) | Un problema nuevo en [laboratorios-y-simulaciones](https://github.com/nuevasomosaguas/laboratorios-y-simulaciones) |
| [`alta-biblioteca`](skills/alta-biblioteca/SKILL.md) | Una obra nueva en el área secundaria de la [biblioteca](https://nuevasomosaguas.github.io/biblioteca.html), como propuesta, y la sesión de revisión que la cura |

## Instalar

Dentro de Claude Code:

```
/plugin marketplace add nuevasomosaguas/nuevasomosaguas-skills
/plugin install nuevasomosaguas@nuevasomosaguas
```

Para probar cambios sin publicarlos, el primer comando acepta también la ruta de un clon local.

## Añadir una skill

Una carpeta `skills/nombre/` con su `SKILL.md`, y una fila en la tabla de arriba.

## Reglas globales

[`AGENTS.md`](AGENTS.md) reúne el mapa de repositorios, la guía de estilo, los criterios de rigor y las órdenes de comprobación para todo el proyecto. En la carpeta raíz que agrupa los repositorios, enlázalo para que cualquier agente lo cargue al abrirla:

```sh
ln -s nuevasomosaguas-skills/AGENTS.md AGENTS.md
ln -s AGENTS.md CLAUDE.md
```
