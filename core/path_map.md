# 🗺️ Mapa de Rutas Svelte & SvelteKit

## Proyectos SvelteKit
- `src/routes/`: Estructura de rutas basadas en sistema de carpetas (`+page.svelte`, `+page.server.ts`, `+layout.svelte`).
- `src/lib/`: Módulos, utilidades y componentes UI compartidos accesibles mediante `$lib`.
- `src/lib/components/`: Componentes `.svelte` reutilizables.
- `src/lib/server/`: Código exclusivo de servidor (Base de datos, tokens, secretos).

## Arquitectura Limpia (`web-agent-rules` Integration)
- `src/lib/domain/`: Entidades y Value Objects de negocio en TypeScript estricto.
- `src/lib/use_cases/`: Lógica de aplicación pura desvinculada del framework.
