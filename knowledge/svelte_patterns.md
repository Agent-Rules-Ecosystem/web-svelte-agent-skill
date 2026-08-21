# Patrones Canónicos de Svelte/SvelteKit

## Stores Reactivos

Los stores son la forma canónica de compartir estado entre componentes en Svelte:

- `writable(value)` — Estado mutable compartido.
- `readable(value, start)` — Estado derivado de una fuente externa (WebSocket, API, etc.).
- `derived(stores, fn)` — Estado computado desde uno o más stores.

**Antipatrón a detectar**: Variables de módulo en `<script context="module">` usadas como estado compartido entre instancias.

## SSR-Safety

En SvelteKit, el código se puede ejecutar tanto en servidor como en cliente:

- **Regla**: Nunca acceder a `window`, `document`, `navigator` o `localStorage` fuera de `onMount()` o bloques `if (browser)`.
- **Detección**: Buscar referencias directas a APIs de browser en el cuerpo de `<script>` sin protección.

## Estructura de Rutas (SvelteKit)

| Archivo | Propósito |
|---|---|
| `+page.svelte` | Componente de página |
| `+page.ts` / `+page.server.ts` | Load function (datos de la ruta) |
| `+layout.svelte` | Layout compartido entre subrutas |
| `+error.svelte` | Página de error personalizada |
| `+server.ts` | API endpoint (JSON/REST) |
