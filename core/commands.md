# $-Comandos de Svelte/SvelteKit

| Comando | Acción | Descripción |
|---|---|---|
| `$svelte` | Bootstrap | Inicializa la skill y carga el contexto del dominio. |
| `$svelte:audit` | Auditoría | Escanea el proyecto y genera reporte de hallazgos del dominio. |
| `$svelte:fix` | Remediación | Aplica mejoras derivadas del último `$svelte:audit`. |
| `$svelte:fix [ruta]` | Remediación Puntual | Aplica remediación a un archivo o directorio específico. |
| `$svelte:check` | Verificación | Identifica componentes sin tipado TypeScript. |

## Reglas de parsing

- El prefijo `$svelte` debe ser el primer carácter del mensaje o estar en línea propia.
- Los comandos son **case-insensitive**.
- Si el agente no reconoce el comando, responder con la lista de comandos disponibles.
