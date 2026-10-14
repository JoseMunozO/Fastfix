# Flujo de trabajo

## Ramas

```
feature/<nombre>  ──PR──▶  staging  ──PR──▶  main
```

- `main`: versión estable. **Nunca** se hace push directo.
- `staging`: integración y pruebas. Todo cambio entra aquí primero.
- `feature/*`, `fix/*`: ramas de trabajo, creadas desde `staging`.

## Reglas

1. Crea tu rama desde `staging`: `git checkout staging && git pull && git checkout -b feature/mi-cambio`
2. Abre el PR hacia `staging`. El CI (lint, typecheck, build) debe pasar.
3. Cuando `staging` esté estable, se abre un PR `staging → main`.
4. El CI rechaza cualquier PR a `main` que no venga de `staging`.

## Comandos

```bash
npm install
npm run dev        # servidor de desarrollo
npm run lint       # oxlint
npm run typecheck  # tsc
npm run build      # build de producción
```
