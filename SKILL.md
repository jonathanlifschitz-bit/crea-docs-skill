---
name: crea-docs
description: >
  Crea la carpeta docs/ con cuatro archivos markdown para un nuevo proyecto de cliente:
  contexto.md (quién es el cliente, el problema, el negocio), progreso.md (historial
  de sesiones y pendientes), roadmap.md (fases a largo plazo) y proximos-pasos.md
  (tareas concretas e inmediatas en orden de prioridad).
  Usar cuando el usuario diga "crea los docs", "genera la documentación del proyecto",
  "crea-docs" o inicie un nuevo proyecto de cliente.
---

# Skill: crea-docs

Crea la estructura de documentación estándar para un proyecto de cliente nuevo.

## Cuándo activar

Cuando el usuario diga "crea los docs", "/crea-docs", "genera la documentación", "arma los docs del proyecto" o similar. También cuando se inicie un nuevo proyecto y el usuario quiera documentarlo.

## Lo que genera

Crea `docs/` en el directorio del proyecto actual con cuatro archivos:

| Archivo | Contenido |
|---|---|
| `contexto.md` | Quién es el cliente, su negocio, el problema que resuelve el agente, el flujo deseado, acuerdos económicos |
| `progreso.md` | Historial de sesiones con fecha y lo que se hizo, tabla de estado actual y pendientes con responsable |
| `roadmap.md` | Visión a largo plazo organizada en fases numeradas (incluye mejoras futuras post-lanzamiento) |
| `proximos-pasos.md` | Tareas concretas e inmediatas en orden de prioridad, con responsable y checklist de testing |

## Flujo de ejecución

### Paso 1 — Recopilar información

Si el usuario ya pegó una transcripción de videollamada o pasó contexto del cliente, usarlo directamente.

Si no, preguntar todo junto en un solo mensaje:

> Para armar los docs necesito:
> 1. ¿Quién es el cliente? (nombre, negocio, rubro)
> 2. ¿Qué problema resuelve el agente/automatización?
> 3. ¿Qué se acordó en términos económicos? (setup + mensual)
> 4. ¿Hay una transcripción o notas de la reunión inicial para pegar?
> 5. ¿Cuál es la fecha de hoy / del primer contacto?

### Paso 2 — Leer el estado actual del código

Antes de escribir `progreso.md`, revisar qué archivos existen en el proyecto:

```bash
find . -type f -not -path './.git/*' -not -name '.DS_Store'
```

Así `progreso.md` refleja con precisión lo que ya está construido.

### Paso 3 — Crear los archivos

```bash
mkdir -p docs
```

Luego escribir los cuatro archivos con el contenido extraído.

---

## Estructura de cada archivo

### contexto.md

```markdown
# Contexto del Proyecto — [Nombre Cliente]

## El cliente
[Quién es, qué hace, rubro, años en el negocio]

## El problema
[Qué proceso tiene hoy, por qué es un problema, escala del problema]

## Lo que automatiza este agente
[El flujo concreto: entrada → procesamiento → salida]

## Acuerdos económicos
| Concepto | Monto |
|---|---|
| Setup | $X USD |
| Mensual | $X USD/mes |

## Primer contacto
- Fecha: [fecha]
- Participantes: [quiénes estuvieron]
```

### progreso.md

```markdown
# Progreso del Proyecto — [Nombre Cliente]

## Historial de sesiones

### Sesión 1 — [fecha]
**[Título descriptivo]**
- [bullet de lo que se hizo]
- [bullet de lo que se hizo]

---

## Estado actual
**[Área]**: [estado] ✅ / ⏳

---

## Pendientes

| Tarea | Responsable | Estado |
|---|---|---|
| [tarea] | [quién] | ⏳ Pendiente |
```

### roadmap.md

```markdown
# Roadmap — [Nombre Cliente]

## Fase 1 — [Nombre de la fase]
- [ ] Tarea 1
- [ ] Tarea 2

## Fase 2 — [Nombre de la fase]
- [ ] Tarea 1
...

## Fase N — Mejoras futuras (post-lanzamiento)
- [ ] Mejora 1
```

### proximos-pasos.md

Tareas concretas e inmediatas, en orden de prioridad. Cada paso tiene:
- Número y título claro
- Responsable (Jonathan / cliente / ambos)
- Detalle accionable (pasos exactos, comandos, URLs)
- Checklist de testing cuando aplica

```markdown
# Próximos Pasos — [Nombre Cliente]

Tareas concretas para dejar el proyecto operativo. En orden.

---

## 1. [Título de la tarea]
**Responsable: [quién]**

[Descripción y pasos concretos]

---

## 2. [Título de la tarea]
**Responsable: [quién]**

[Descripción y pasos concretos]

---

## N. Testing end-to-end
**Responsable: Jonathan + [cliente]**

- [ ] Flujo A — verificar que [resultado esperado]
- [ ] Flujo B — verificar que [resultado esperado]
```

---

## Cómo actualizar los docs

Cuando el usuario diga **"actualiza los docs"** al final de una sesión:

1. Leer el estado actual de los cuatro archivos en `docs/`
2. Agregar una nueva entrada en `progreso.md` con la fecha de hoy y las tareas completadas
3. Tachar o mover a completado los ítems del roadmap que se terminaron
4. Actualizar `proximos-pasos.md`: marcar completados, ajustar prioridades, agregar nuevos pasos si surgieron
5. Actualizar la tabla de estado en `progreso.md`

No crear archivos nuevos — solo editar los existentes con `Edit`.
