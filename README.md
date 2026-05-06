# crea-docs — Claude Code Skill

Skill para Claude Code que crea automáticamente la carpeta `docs/` con los cuatro archivos de documentación estándar para cualquier proyecto de cliente nuevo.

## Qué genera

| Archivo | Contenido |
|---|---|
| `docs/contexto.md` | Quién es el cliente, su negocio, el problema, el flujo acordado, precios |
| `docs/progreso.md` | Historial de sesiones con fechas, y tabla de estado y pendientes con responsables |
| `docs/roadmap.md` | Visión a largo plazo organizada en fases, con checkboxes (incluye mejoras futuras) |
| `docs/proximos-pasos.md` | Tareas concretas e inmediatas en orden de prioridad, con responsable y checklist de testing |

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

Claude agrega la sesión al historial en `progreso.md`, tacha los ítems completados en `roadmap.md`, actualiza la tabla de pendientes y ajusta las prioridades en `proximos-pasos.md`.
