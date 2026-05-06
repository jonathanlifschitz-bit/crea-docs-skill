# crea-docs — Claude Code Skill

Skill para Claude Code que crea automáticamente la carpeta `docs/` con los tres archivos de documentación estándar para cualquier proyecto de cliente nuevo.

## Qué genera

| Archivo | Contenido |
|---|---|
| `docs/contexto.md` | Quién es el cliente, su negocio, el problema, el flujo acordado, precios |
| `docs/progreso.md` | Historial de sesiones con fechas, y tabla de pendientes con responsables |
| `docs/roadmap.md` | Próximos pasos organizados en fases, con checkboxes |

## Instalación

```bash
mkdir -p ~/.claude/skills/crea-docs
curl -sL https://raw.githubusercontent.com/jonathanlifschitz-bit/crea-docs-skill/main/SKILL.md \
  -o ~/.claude/skills/crea-docs/SKILL.md
```

## Cómo usarlo

En cualquier proyecto de cliente, escribir en Claude Code:

```
/crea-docs
```

O simplemente: `"crea los docs del proyecto"`, `"arma la documentación"`.

Si tenés una transcripción de la reunión inicial, pegarla directamente — el skill extrae el contexto solo.

## Actualizar los docs al final de cada sesión

```
actualiza los docs
```

Claude agrega la sesión al historial en `progreso.md`, tacha los ítems completados en `roadmap.md` y actualiza la tabla de pendientes.
