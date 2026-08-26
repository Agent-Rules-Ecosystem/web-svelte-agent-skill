# Patrones y Capacidades Avanzadas de Svelte y SvelteKit

## 1. Svelte 5 Runes (Reactividad Fina de Siguiente Generación)

Svelte 5 introduce las **Runes**, reemplazando las declaraciones `let` reactivas (`$:`) y la dependencia exclusiva de stores para lógica compartida:

- **`$state(initialValue)`**: Declara estado reactivo local o profundo (objetos/arrays mutables de forma reactiva).
- **`$derived(expression)`**: Declara valores derivados/computados memoizados automáticamente.
- **`$effect(() => { ... })`**: Manejo de efectos secundarios con ciclo de vida y función de cleanup.
- **Runes en Archivos Universales (`.svelte.js` / `.svelte.ts`)**: Permite encapsular estado reactivo reutilizable fuera de componentes sin requerir stores suscritos manualmente.

```ts
// counter.svelte.ts
export function createCounter() {
    let count = $state(0);
    let double = $derived(count * 2);

    return {
        get count() { return count; },
        get double() { return double; },
        increment: () => count++
    };
}
```

---

## 2. Stores Reactivos Clásicos (Svelte 3/4 Parity & Migration)

- `writable(value)` — Estado mutable suscrito con `$` (ej. `$userStore`).
- `readable(value, start)` — Estado reactivo de solo lectura (fuentes de datos externas/EventSource/WebSockets).
- `derived(stores, fn)` — Computación reactiva multi-store.

---

## 3. SvelteKit Full-Stack Core & Routing

### Estructura de Rutas
| Archivo | Rol | Entorno |
|---|---|---|
| `+page.svelte` | Componente de UI principal | Cliente / SSR |
| `+page.ts` | Load function isomórfica | Cliente + Servidor |
| `+page.server.ts` | Load function y Form Actions exclusivas | Servidor Node/Edge |
| `+layout.svelte` | Layout heredado por subrutas | Cliente / SSR |
| `+layout.server.ts` | Carga de datos globales (auth, sesión) | Servidor Node/Edge |
| `+server.ts` | Endpoints API REST/JSON independientes | Servidor Node/Edge |

### Form Actions (Mutaciones Mixtas Progresivas)
Manejo nativo de formularios sin JS obligatorio en cliente:

```ts
// +page.server.ts
export const actions = {
    default: async ({ request }) => {
        const data = await request.formData();
        // Procesar mutación de servidor de forma segura
        return { success: true };
    }
};
```

---

## 4. Superpoderes Diferenciadores de Svelte

### A. Animaciones y Transiciones Nativas (Cero Dependencias)
Svelte incluye motores de física y animación integrados directos en el compilador:
- Directivas: `in:fly`, `out:fade`, `transition:slide`, `animate:flip`.
- Layout Animations (FLIP): Transición automática de elementos al reordenar listas.

### B. Salida Compilada Cero-Sobrecarga (No Virtual DOM)
A diferencia de React o Vue, Svelte compila a JavaScript imperativo altamente optimizado que actualiza directamente el DOM real cuando cambia el estado.

---

## 5. Integración con Clean Architecture (`web-agent-rules`)

- **Capa de Dominio:** Entidades puras y Value Objects en TypeScript estricto.
- **Capa de Casos de Uso:** Clases/Funciones puras sin acoplamiento a Svelte.
- **Capa de Presentación:** Componentes `.svelte` y Runes/Stores consumiendo Casos de Uso mediante inyección de dependencias.
