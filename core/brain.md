# 🧠 Engine de Decisiones Svelte & SvelteKit (Svelte Brain)

## Matriz de Selección Reactiva (Svelte 5 vs Legacy)

1. **Usar Svelte 5 Runes (`$state`, `$derived`, `$effect`) si**:
   - Se desarrolla un proyecto nuevo o componente moderno en Svelte 5+.
   - Se requiere compartir estado reactivo en archivos `.svelte.ts` / `.svelte.js` fuera de la jerarquía de componentes.

2. **Usar Stores Reactivos (`writable`, `derived`, `readable`) si**:
   - Se requiere retrocompatibilidad con bibliotecas o proyectos existentes de Svelte 3/4.
   - El estado debe ser consumido desde módulos JS puros sin soporte de compilador Svelte 5.

3. **Usar Form Actions en SvelteKit si**:
   - Se implementan mutaciones de datos (formularios, login, CRUD) para aprovechar el manejo de servidor sin depender de endpoints REST manuales.
