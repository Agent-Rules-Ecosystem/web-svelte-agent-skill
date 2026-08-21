---
name: web-svelte-patterns-agent-skill
description: Patrones arquitectónicos de Svelte/SvelteKit: stores, SSR/SSG, layout system, routing y buenas prácticas de componentes.
---

# WebSveltePatterns Skill Directive

## Bootstrap de la Habilidad

Al detectar triggers de Svelte/SvelteKit (`$svelte`, `svelte patterns`, `sveltekit audit`):

1. `.skill/web-svelte-patterns-agent-skill/SKILL.md` ← **Directiva principal de triggers y operación**
2. `.skill/web-svelte-patterns-agent-skill/core/commands.md` ← **$-Comandos disponibles**
3. `.skill/web-svelte-patterns-agent-skill/core/brain.md` ← **Motor de decisiones del dominio**

## Reglas Canónicas de Svelte/SvelteKit

- **Stores reactivos**: Todo estado compartido debe vivir en stores de Svelte (`writable`, `readable`, `derived`), nunca en variables globales.
- **Colocation**: Los estilos, lógica y markup de un componente deben estar en el mismo `.svelte` file.
- **SSR-safe**: Nunca acceder a `window`, `document` o APIs de browser fuera de `onMount` o bloques `browser`.
- **Tipado**: Usar TypeScript con `lang="ts"` en `<script>` en todos los componentes nuevos.
- **Layouts**: Usar `+layout.svelte` de SvelteKit para lógica compartida entre rutas; no duplicar en cada `+page.svelte`.
