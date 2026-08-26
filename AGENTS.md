---
name: web-svelte-agent-skill
description: Svelte 5 Runes, SvelteKit (SSR/SSG/Form Actions) y Clean Architecture Skill para Agentes IA.
---

# 🧡 Svelte Agent Skill Directive

## Bootstrap de la Habilidad

Al detectar `$svelte` o tareas relacionadas con Svelte, Svelte 5, Runes, SvelteKit, Stores o componentes `.svelte`:

1. `.skill/web-svelte-agent-skill/SKILL.md` ← **Directiva principal**
2. `.skill/web-svelte-agent-skill/core/commands.md`
3. `.skill/web-svelte-agent-skill/core/brain.md`
4. `.skill/web-svelte-agent-skill/core/path_map.md`

## Reglas Canónicas de Svelte & SvelteKit

- **Uso de Runes en Svelte 5**: Preferir `$state`, `$derived`, `$effect` sobre la reactividad antigua `$:`.
- **SSR-Safety Obligatorio**: Proteger acceso a `window`, `document` o APIs de navegador dentro de `onMount` o verificaciones de entorno `browser`.
- **Form Actions para Mutaciones**: Utilizar Form Actions de SvelteKit para mutaciones de servidor con soporte de fallbacks progresivos.
- **Tipado TypeScript Estricto**: Definir props y tipos de datos explícitos en componentes `.svelte`.
