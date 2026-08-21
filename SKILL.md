---
name: web-svelte-patterns-agent-skill
description: Patrones arquitectónicos de Svelte/SvelteKit: stores, SSR/SSG, layout system, routing y buenas prácticas de componentes.
---

# WebSveltePatterns Skill Matrix

## Capacidades de la Habilidad

```mermaid
graph LR
    A[SVELTE] --> B[Auditoría de Dominio]
    A --> C[Patrones y Buenas Prácticas]
    A --> D[Detección de Antipatrones]
    A --> E[Refactorización Guiada]
```

## Protocolo de Auditoría (`$svelte:audit`)

1. Detectar archivos del dominio en el proyecto
2. Evaluar cumplimiento de patrones canónicos
3. Identificar antipatrones y deuda técnica específica del dominio
4. Generar reporte de hallazgos clasificados por severidad (Alta / Media / Baja)
5. Proponer remediaciones concretas y ejecutarlas con `$svelte:fix`
