# Antipatrones Comunes en Svelte/SvelteKit

## 1. Estado Global sin Stores

**Problema**: Usar variables de módulo o imports compartidos como estado mutable.
**Detección**: Módulos `.ts` o `.js` que exportan variables mutables usadas en múltiples componentes.
**Solución**: Migrar a `writable` store con `export const myStore = writable(initialValue)`.

## 2. Acceso DOM en SSR

**Problema**: Llamadas a `window.scrollY`, `document.querySelector()`, etc. en el cuerpo de `<script>`.
**Detección**: Referencias directas a `window`, `document`, `navigator` sin `if (browser)` o `onMount`.
**Solución**: Envolver en `import { browser } from '$app/environment'; if (browser) { ... }` o mover a `onMount`.

## 3. Props sin Tipado

**Problema**: Props declaradas sin tipo TypeScript en proyectos con TS habilitado.
**Detección**: `export let propName;` sin anotación de tipo en archivos `.svelte` con `lang="ts"`.
**Solución**: `export let propName: string;` o el tipo correspondiente.

## 4. Load Functions con Side Effects

**Problema**: Mutaciones o escrituras en `+page.server.ts` load functions (deben ser read-only).
**Detección**: Llamadas a operaciones de escritura dentro de funciones `load()`.
**Solución**: Mover a `+server.ts` como endpoints POST/PUT o usar form actions.

## 5. Componentes Monolíticos

**Problema**: Componentes `.svelte` de más de 250 líneas con múltiples responsabilidades.
**Detección**: Archivos `.svelte` que superan el umbral de líneas.
**Solución**: Extraer subcomponentes y lógica a stores o módulos `.ts`.
