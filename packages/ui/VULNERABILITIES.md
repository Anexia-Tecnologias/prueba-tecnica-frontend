# Vulnerabilidades

<!-- Mantenido por la skill dependabot-auto. «Majors pendientes» y «Paquetes» se regeneran en cada ejecución; «Registro» solo crece. No editar a mano. -->

## Majors pendientes

| Paquete | Instalada | Corrige | Última | Decisión | Motivo | Alertas |
|---|---|---|---|---|---|---|
| `minimatch` | 3.1.5 / 9.0.9 | 11.0.1 | 11.0.3 (8 y 2 majors) | ⚪ No se actualiza (propuesta) | Solo herramientas de desarrollo (`eslint`, `typescript-eslint`, `eslint-plugin-react`, `glob` del docgen de Storybook) con patrones escritos en el repo; nada de `apps/` ni `packages/` lo importa. Premisa: [`packages/eslint-config/package.json`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/packages/eslint-config/package.json), busca:'minimatch' en `apps` y `packages` | [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249) |

## Registro

### 2026-10-31

Repo sin alertas de Dependabot: hallazgos de `npm audit` sobre `package-lock.json` de la raíz.

#### ✅ Actualizadas
- 🟠 `vite` 6.4.1 → 6.4.5 (patch, transitiva, copia de la raíz que usan `astro` y `vitest`; sin cambios de rango). Antes 🛠️ por `ERESOLVE` en `npm update vite`; al instalar `vite@6.4.5` en `apps/docs` npm la deduplica en la raíz sin conflictos. (npm audit) [GHSA-8g5g-mxqh-grgj](https://github.com/advisories/GHSA-8g5g-mxqh-grgj) [GHSA-4w7w-66w2-5vf9](https://github.com/advisories/GHSA-4w7w-66w2-5vf9) [GHSA-587h-7wmj-h5pm](https://github.com/advisories/GHSA-587h-7wmj-h5pm) [GHSA-698v-4r3x-3vcv](https://github.com/advisories/GHSA-698v-4r3x-3vcv) [GHSA-9jrq-w75r-8gcw](https://github.com/advisories/GHSA-9jrq-w75r-8gcw) [GHSA-fx2h-pf6j-xcff](https://github.com/advisories/GHSA-fx2h-pf6j-xcff) [GHSA-p9ff-h696-f583](https://github.com/advisories/GHSA-p9ff-h696-f583) [GHSA-r825-w8mm-5pxw](https://github.com/advisories/GHSA-r825-w8mm-5pxw) [GHSA-rq7h-c2jc-7f22](https://github.com/advisories/GHSA-rq7h-c2jc-7f22) [GHSA-v6wh-96g9-6wx3](https://github.com/advisories/GHSA-v6wh-96g9-6wx3)

#### ⚪ Propuestas para descartar
- 🟡→⚪ `minimatch` 3.1.5 / 9.0.9, 1 advisory (DoS por amplificación de patrones). No aplica: hace falta un patrón controlado por un atacante, y solo lo usan `eslint`, `typescript-eslint`, `eslint-plugin-react` y el `glob` del docgen de Storybook, devDependencies que procesan patrones escritos en el repo (config de ESLint, `tsconfig`, `stories` de [`apps/docs/.storybook/main.ts`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/apps/docs/.storybook/main.ts#L4)). Ningún fichero de `apps/` ni `packages/` lo importa. Arreglo solo en 11.0.1 (major). Premisa: packages/eslint-config/package.json@ba541f5, busca:'minimatch' en apps@e69de29, busca:'minimatch' en packages@e69de29. (npm audit) [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249)

### 2026-10-29

Repo sin alertas de Dependabot: hallazgos de `npm audit` sobre `package-lock.json` de la raíz.

#### ✅ Actualizadas
- 🔵 `@babel/core` 7.29.0 → 7.29.7 (minor/patch, transitiva). (npm audit) [GHSA-4x5r-pxfx-6jf8](https://github.com/advisories/GHSA-4x5r-pxfx-6jf8)

#### 🛠️ Requieren actualización manual
- 🔴→🟠 `vitest` 4.0.18 → 4.1.12. Motivo: minor, pero `npm install vitest@4.1.12 -w @repo/ui` falla en npm 10.9.7 con `npm error Cannot read properties of null (reading 'edgesOut')` (arborist `#loadPeerSet`), también sobre el lockfile limpio de `main`. (npm audit) [GHSA-5xrq-8626-4rwp](https://github.com/advisories/GHSA-5xrq-8626-4rwp) [GHSA-82fw-gwwq-j7x9](https://github.com/advisories/GHSA-82fw-gwwq-j7x9) [GHSA-qxg6-89mg-rqv8](https://github.com/advisories/GHSA-qxg6-89mg-rqv8)
  - Subir `vitest` 4.0.18 → 4.1.12 en `packages/ui` y `packages/area-privada` (pin exacto). Probar con otra versión de npm o regenerando la entrada de `vitest` del lockfile.
  - Cambios: [vitest 4.1.12](https://github.com/vitest-dev/vitest/releases/tag/v4.1.12)
  - Afecta a este proyecto: solo tests y máquina del desarrollador (UI server, mocks).
- 🟠 `vite` 6.4.1 → 6.4.4. Motivo: copia de la raíz, la que usan `astro` y `vitest`. `npm update vite` intenta vite 7 (vitest admite `^6 || ^7`) y choca con el peer `^4 || ^5 || ^6` de `@storybook/react-vite`: `ERESOLVE ... While resolving: @storybook/react-vite@8.6.19 Found: vite@6.4.1`. `npm dedupe` falla igual. (npm audit) [GHSA-4w7w-66w2-5vf9](https://github.com/advisories/GHSA-4w7w-66w2-5vf9) [GHSA-587h-7wmj-h5pm](https://github.com/advisories/GHSA-587h-7wmj-h5pm) [GHSA-698v-4r3x-3vcv](https://github.com/advisories/GHSA-698v-4r3x-3vcv) [GHSA-9jrq-w75r-8gcw](https://github.com/advisories/GHSA-9jrq-w75r-8gcw) [GHSA-fx2h-pf6j-xcff](https://github.com/advisories/GHSA-fx2h-pf6j-xcff) [GHSA-p9ff-h696-f583](https://github.com/advisories/GHSA-p9ff-h696-f583) [GHSA-r825-w8mm-5pxw](https://github.com/advisories/GHSA-r825-w8mm-5pxw) [GHSA-rq7h-c2jc-7f22](https://github.com/advisories/GHSA-rq7h-c2jc-7f22) [GHSA-v6wh-96g9-6wx3](https://github.com/advisories/GHSA-v6wh-96g9-6wx3)
  - Dejar la raíz en vite ≥6.4.4 sin flags: probablemente se resuelve sola al subir `vitest` (fila anterior) o `astro`.
  - Cambios: [CHANGELOG de vite 6.4.4](https://github.com/vitejs/vite/blob/v6.4.4/packages/vite/CHANGELOG.md)
  - Afecta a este proyecto: dev server de Astro y de vitest, máquina del desarrollador.
