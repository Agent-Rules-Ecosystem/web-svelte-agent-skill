# Plantilla: Store de Svelte con TypeScript

Plantilla canónica para crear un store de dominio en Svelte con TypeScript:

```typescript
// src/lib/stores/myDomain.store.ts
import { writable, derived } from 'svelte/store';

// Tipos del dominio
interface MyEntity {
  id: string;
  name: string;
  // ... otras propiedades
}

interface MyDomainState {
  items: MyEntity[];
  loading: boolean;
  error: string | null;
}

// Estado inicial
const initialState: MyDomainState = {
  items: [],
  loading: false,
  error: null,
};

// Store principal
const { subscribe, set, update } = writable<MyDomainState>(initialState);

// Store derivado (computed)
export const itemCount = derived(
  { subscribe },
  ($state) => $state.items.length
);

// Acciones
export const myDomainStore = {
  subscribe,
  loadItems: async () => {
    update(s => ({ ...s, loading: true, error: null }));
    try {
      // const data = await fetchItems();
      update(s => ({ ...s, items: [], loading: false }));
    } catch (err) {
      update(s => ({ ...s, error: String(err), loading: false }));
    }
  },
  reset: () => set(initialState),
};
```
