# GitHub Spec Kit — Comandos Principales

> **Spec-Driven Development (SDD)** es una metodología donde las especificaciones son ejecutables y generan implementaciones directamente, en lugar de ser solo documentación de scaffolding.

---

## Flujo de trabajo completo

```
Constitution → Specify → Clarify → Plan → Tasks → Analyze → Implement → PR
```

---

## Comandos

### 1. `/constitution`

Crea o actualiza el archivo `.specify/memory/constitution.md` con los principios fundacionales del proyecto.

- Define reglas no negociables que la IA referenciará en todas las fases
- Establece principios arquitectónicos como:
  - *Observability Over Opacity*
  - *Simplicity Over Cleverness*
  - *Integration Over Isolation*
  - *Modularity Over Monoliths*

```
Cuándo usarlo: Al inicio del proyecto o cuando cambien los principios arquitectónicos
```

---

### 2. `/specify` (alias: `/speckit.specify`)

Transforma una descripción simple de feature en una especificación estructurada completa.

- Genera numeración automática de features
- Crea la rama correspondiente en Git
- Usa templates para estructurar la spec
- Crea la estructura de directorios adecuada

```
Cuándo usarlo: Antes de empezar a desarrollar cualquier feature nueva
```

---

### 3. `/clarify`

Refina y resuelve ambigüedades de la especificación antes de pasar al planning.

- Identifica puntos incompletos o contradictorios
- Asegura que la spec sea lo suficientemente precisa para planificar
- Útil en proyectos complejos o cuando la spec tiene zonas grises

```
Cuándo usarlo: Cuando la spec tiene ambigüedades antes del plan técnico
```

---

### 4. `/plan` (alias: `/speckit.plan`)

Genera el plan técnico basado en la spec y la constitution.

- Lee el `FEATURE_SPEC` y el `constitution.md`
- Carga el template de plan de implementación
- Ejecuta el workflow de planificación técnica
- Marca incógnitas como `NEEDS CLARIFICATION`

```
Cuándo usarlo: Después de tener una spec clara, para definir el enfoque técnico
```

---

### 5. `/tasks` (alias: `/speckit.tasks`)

Desglosa el plan técnico en tareas concretas y ejecutables.

- Crea tareas específicas y accionables
- Las ordena en la secuencia correcta de ejecución
- Actualiza la memoria `.specify` con las tareas generadas

```
Cuándo usarlo: Después del plan técnico, para dividir el trabajo en pasos manejables
```

---

### 6. `/analyze`

Verifica la consistencia entre especificación, plan y tareas.

- Actúa como quality gate antes de implementar
- Asegura que las tareas estén alineadas con la spec original
- Valida que todo sea coherente con la constitution

```
Cuándo usarlo: Antes de implementar, para validar que todo es consistente
```

---

### 7. `/implement` (alias: `/speckit.implement`)

Guía a la IA en la implementación usando la lista de tareas generada.

- Usa el task list como guía de ejecución
- Aplica la constitution como contexto arquitectónico
- Genera código que respeta los principios definidos

```
Cuándo usarlo: Cuando la spec, plan y tareas estén completas y validadas
```

---

## Estructura de archivos generada

```
├── .github/
│   └── prompts/
│       ├── plan.prompt.md
│       ├── specify.prompt.md
│       └── tasks.prompt.md
└── .specify/
    ├── memory/
    │   ├── constitution.md
    │   └── constitution_update_checklist.md
    ├── scripts/
    └── templates/
        ├── agent-file-template.md
        ├── plan-template.md
        ├── spec-template.md
        └── tasks-template.md
```

---

## Configuración MCP (`.mcp.json`)

Para usar Spec Kit con Claude Code u otros clientes MCP:

```json
{
  "mcpServers": {
    "spec-kit": {
      "command": "npx",
      "args": ["-y", "@lsendel/spec-kit-mcp"],
      "env": {}
    }
  }
}
```

---

## Instalación del CLI

```bash
# Instalación global via npm
npm install -g @lsendel/spec-kit-mcp

# O ejecutar directamente con npx
npx @lsendel/spec-kit-mcp

# Alternativa via Rust/cargo
cargo install spec-kit-mcp
```

---

## Resumen de comandos

| Comando        | Alias                | Propósito                                  | Obligatorio |
|----------------|----------------------|--------------------------------------------|-------------|
| `/constitution` | —                   | Principios fundacionales del proyecto      | Sí          |
| `/specify`      | `/speckit.specify`  | Crear especificación estructurada          | Sí          |
| `/clarify`      | —                   | Resolver ambigüedades en la spec           | Opcional    |
| `/plan`         | `/speckit.plan`     | Plan técnico de implementación             | Sí          |
| `/tasks`        | `/speckit.tasks`    | Desglose en tareas ejecutables             | Sí          |
| `/analyze`      | —                   | Quality gate de consistencia               | Opcional    |
| `/implement`    | `/speckit.implement`| Guiar la implementación con la IA          | Sí          |

---

## Referencias

- [github/spec-kit — Repositorio oficial](https://github.com/github/spec-kit)
- [lsendel/spec-kit-mcp — Servidor MCP](https://github.com/lsendel/spec-kit-mcp)
- [Spec-Driven Development — Microsoft Dev Blog](https://developer.microsoft.com/blog/spec-driven-development-spec-kit)
- [Exploring Spec-Driven Development — LogRocket](https://blog.logrocket.com/github-spec-kit/)
- [Configuring toolsets — GitHub Docs](https://docs.github.com/en/copilot/how-tos/provide-context/use-mcp/configure-toolsets)
