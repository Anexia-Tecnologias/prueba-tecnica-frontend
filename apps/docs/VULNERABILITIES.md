# Vulnerabilidades

<!-- Mantenido por la skill dependabot-auto. «Majors pendientes» y «Paquetes» se regeneran en cada ejecución; «Registro» solo crece. No editar a mano. -->

## Majors pendientes

| Paquete | Instalada | Corrige | Última | Decisión | Motivo | Alertas |
|---|---|---|---|---|---|---|
| `uuid` | 9.0.1 | 11.1.1 | storybook 10.6.5 (2 majors) | 🛠️ Hay que actualizar | major: `@storybook/addon-actions` 8.x pide `uuid` ^9; hay que subir Storybook a 9 o superior (`addon-essentials` desaparece) | [GHSA-w5hq-g745-h8pq](https://github.com/advisories/GHSA-w5hq-g745-h8pq) |
| `glob` | 10.5.0 | 14.0.2 | 14.0.3 (4 majors) | ⚪ No se actualiza (propuesta) | Solo lo usa `@joshwooding/vite-plugin-react-docgen-typescript` 0.5.0 (vía `@storybook/react-vite`) con `globSync`, sin `AbortSignal`; el fallo solo afecta al recorrido asíncrono cancelado. Premisa: [`apps/docs/package.json`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/apps/docs/package.json) | [GHSA-3g3m-2fjr-6pw4](https://github.com/advisories/GHSA-3g3m-2fjr-6pw4) |
| `minimatch` | 3.1.5 / 9.0.9 | 11.0.1 | 11.0.3 (8 y 2 majors) | ⚪ No se actualiza (propuesta) | Solo herramientas de desarrollo (`eslint`, `typescript-eslint`, `eslint-plugin-react`, `glob` del docgen de Storybook) con patrones escritos en el repo; nada de `apps/` ni `packages/` lo importa. Premisa: [`packages/eslint-config/package.json`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/packages/eslint-config/package.json), busca:'minimatch' en `apps` y `packages` | [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249) |

## Registro

### 2026-10-31

Repo sin alertas de Dependabot: hallazgos de `npm audit` sobre `package-lock.json` de la raíz.

#### ✅ Actualizadas
- 🟡 `vite` 6.4.4 → 6.4.5 (patch, directa en `apps/docs`, rango `^6.4.4` → `^6.4.5`; se deduplica con la copia de la raíz). `server.fs.deny` se salta con queries en el dev server de Storybook, máquina del desarrollador. (npm audit) [GHSA-8g5g-mxqh-grgj](https://github.com/advisories/GHSA-8g5g-mxqh-grgj)
- 🟡 `ws` 8.19.0 → 8.22.0 (minor, transitiva vía `@storybook/core` 8.6.19, rango `^8.2.3` sin cambios). Antes 🛠️: con npm 10.9.7 `npm update ws` no movía el lockfile; con npm 11.19.1 sí. Dev server de Storybook, máquina del desarrollador. (npm audit) [GHSA-58qx-3vcg-4xpx](https://github.com/advisories/GHSA-58qx-3vcg-4xpx) [GHSA-96hv-2xvq-fx4p](https://github.com/advisories/GHSA-96hv-2xvq-fx4p)

#### ⚪ Propuestas para descartar
- 🟡→⚪ `glob` 10.5.0, 1 advisory (el recorrido sigue tras abortar con `AbortSignal`). No aplica: solo lo usa `@joshwooding/vite-plugin-react-docgen-typescript` 0.5.0 (vía `@storybook/react-vite` de [`apps/docs/package.json`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/apps/docs/package.json)), que llama a `globSync` sin `signal` (`dist/index.mjs`, líneas 49-53); el fallo es del recorrido asíncrono cancelado. Arreglo solo en 14.0.2 (major). Premisa: apps/docs/package.json@4dd9cab. (npm audit) [GHSA-3g3m-2fjr-6pw4](https://github.com/advisories/GHSA-3g3m-2fjr-6pw4)
- 🟡→⚪ `minimatch` 3.1.5 / 9.0.9, 1 advisory (DoS por amplificación de patrones). No aplica: hace falta un patrón controlado por un atacante, y solo lo usan `eslint`, `typescript-eslint`, `eslint-plugin-react` y el `glob` del docgen de Storybook, devDependencies que procesan patrones escritos en el repo (config de ESLint, `tsconfig`, `stories` de [`apps/docs/.storybook/main.ts`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/apps/docs/.storybook/main.ts#L4)). Ningún fichero de `apps/` ni `packages/` lo importa. Arreglo solo en 11.0.1 (major). Premisa: packages/eslint-config/package.json@ba541f5, busca:'minimatch' en apps@e69de29, busca:'minimatch' en packages@e69de29. (npm audit) [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249)

### 2026-10-29

Repo sin alertas de Dependabot: hallazgos de `npm audit` sobre `package-lock.json` de la raíz.

#### ✅ Actualizadas
- 🔴→🟠 `storybook` 8.6.15 → 8.6.19 (patch, directa, con todos los `@storybook/*` a 8.6.19). Solo dev server de Storybook: afecta a la máquina del desarrollador, no a producción. (npm audit) [GHSA-f2ph-cmg5-wxc8](https://github.com/advisories/GHSA-f2ph-cmg5-wxc8) [GHSA-mjf5-7g4m-gx5w](https://github.com/advisories/GHSA-mjf5-7g4m-gx5w) [GHSA-px85-f4q5-jh77](https://github.com/advisories/GHSA-px85-f4q5-jh77)
- 🟠 `vite` 6.4.1 → 6.4.4 (patch, directa en `apps/docs`, rango `^6.3.5` → `^6.4.4`). Solo la copia de `apps/docs`; la de la raíz sigue en 6.4.1, ver 🛠️. (npm audit) [GHSA-4w7w-66w2-5vf9](https://github.com/advisories/GHSA-4w7w-66w2-5vf9) [GHSA-587h-7wmj-h5pm](https://github.com/advisories/GHSA-587h-7wmj-h5pm) [GHSA-698v-4r3x-3vcv](https://github.com/advisories/GHSA-698v-4r3x-3vcv) [GHSA-9jrq-w75r-8gcw](https://github.com/advisories/GHSA-9jrq-w75r-8gcw) [GHSA-fx2h-pf6j-xcff](https://github.com/advisories/GHSA-fx2h-pf6j-xcff) [GHSA-p9ff-h696-f583](https://github.com/advisories/GHSA-p9ff-h696-f583) [GHSA-r825-w8mm-5pxw](https://github.com/advisories/GHSA-r825-w8mm-5pxw) [GHSA-rq7h-c2jc-7f22](https://github.com/advisories/GHSA-rq7h-c2jc-7f22) [GHSA-v6wh-96g9-6wx3](https://github.com/advisories/GHSA-v6wh-96g9-6wx3)
- 🟠 `brace-expansion` 1.1.12 / 2.0.2 → 1.1.21 / 2.1.7 (minor/patch, transitiva). (npm audit) [GHSA-3jxr-9vmj-r5cp](https://github.com/advisories/GHSA-3jxr-9vmj-r5cp) [GHSA-6j4f-fj2g-mc7p](https://github.com/advisories/GHSA-6j4f-fj2g-mc7p) [GHSA-f886-m6hf-6m8v](https://github.com/advisories/GHSA-f886-m6hf-6m8v) [GHSA-mh99-v99m-4gvg](https://github.com/advisories/GHSA-mh99-v99m-4gvg) [GHSA-q2hr-2g5m-vwhr](https://github.com/advisories/GHSA-q2hr-2g5m-vwhr) [GHSA-qhr7-859c-m2p7](https://github.com/advisories/GHSA-qhr7-859c-m2p7) [GHSA-rgw5-rvv9-x895](https://github.com/advisories/GHSA-rgw5-rvv9-x895)
- 🟠 `minimatch` 3.1.2 / 9.0.5 → 3.1.5 / 9.0.9 (minor/patch, transitiva). (npm audit) [GHSA-23c5-xmqv-rm74](https://github.com/advisories/GHSA-23c5-xmqv-rm74) [GHSA-3ppc-4f35-3m26](https://github.com/advisories/GHSA-3ppc-4f35-3m26) [GHSA-7r86-cg39-jmmj](https://github.com/advisories/GHSA-7r86-cg39-jmmj)
- 🟠 `nanoid` 3.3.11 → 3.3.20 (minor/patch, transitiva). (npm audit) [GHSA-28wg-ghj8-5hjv](https://github.com/advisories/GHSA-28wg-ghj8-5hjv) [GHSA-2v37-7h3g-55p8](https://github.com/advisories/GHSA-2v37-7h3g-55p8) [GHSA-xwg4-73v4-xw9w](https://github.com/advisories/GHSA-xwg4-73v4-xw9w)
- 🟠 `picomatch` 2.3.1 / 4.0.3 → 2.3.2 / 4.0.7 (minor/patch, transitiva). (npm audit) [GHSA-3v7f-55p6-f55p](https://github.com/advisories/GHSA-3v7f-55p6-f55p) [GHSA-c2c7-rcm5-vvqj](https://github.com/advisories/GHSA-c2c7-rcm5-vvqj)
- 🟠 `postcss` 8.5.6 → 8.5.32 (minor/patch, transitiva). (npm audit) [GHSA-6g55-p6wh-862q](https://github.com/advisories/GHSA-6g55-p6wh-862q) [GHSA-fxqj-rqcc-2cmp](https://github.com/advisories/GHSA-fxqj-rqcc-2cmp) [GHSA-qx2v-qp2m-jg93](https://github.com/advisories/GHSA-qx2v-qp2m-jg93) [GHSA-r28c-9q8g-f849](https://github.com/advisories/GHSA-r28c-9q8g-f849)
- 🟠 `rollup` 4.57.1 → 4.65.1 (minor/patch, transitiva). (npm audit) [GHSA-mw96-cpmx-2vgc](https://github.com/advisories/GHSA-mw96-cpmx-2vgc)
- 🟠 `source-map-js` 1.2.1 → 1.2.2 (minor/patch, transitiva). (npm audit) [GHSA-68fv-2mgg-jv7q](https://github.com/advisories/GHSA-68fv-2mgg-jv7q)
- 🔵 `@babel/core` 7.29.0 → 7.29.7 (minor/patch, transitiva). (npm audit) [GHSA-4x5r-pxfx-6jf8](https://github.com/advisories/GHSA-4x5r-pxfx-6jf8)

#### 🛠️ Requieren actualización manual
- 🟠→🟡 `lodash` 4.17.23 → 4.18.0. Motivo: el `overrides` de la raíz (`"lodash": "4.17.23"`) fija la versión vulnerable y la skill no toca overrides. Arrastra los hallazgos de `@testing-library/jest-dom`, `@storybook/test`, `@storybook/addon-interactions`, `@storybook/react` y `@storybook/react-vite`. (npm audit) [GHSA-f23m-r3pf-42rh](https://github.com/advisories/GHSA-f23m-r3pf-42rh) [GHSA-r5fr-rjxr-66jc](https://github.com/advisories/GHSA-r5fr-rjxr-66jc)
  - Cambiar el override de `package.json` a `"lodash": "4.18.1"` (o quitarlo si ya no hace falta) y `npm install`.
  - Cambios: [releases de lodash](https://github.com/lodash/lodash/releases)
  - Afecta a este proyecto: solo Storybook (`@storybook/test` → `@testing-library/jest-dom`), desarrollo.
- 🟠→🟡 `ws` 8.19.0 → 8.21.0. Motivo: `npm update ws` (también con `-w docs`) termina en `up to date` sin cambiar el lockfile, aunque `@storybook/core` declara `^8.2.3`. (npm audit) [GHSA-58qx-3vcg-4xpx](https://github.com/advisories/GHSA-58qx-3vcg-4xpx) [GHSA-96hv-2xvq-fx4p](https://github.com/advisories/GHSA-96hv-2xvq-fx4p)
  - Refrescar `ws` a ≥8.21.0 en el lockfile; investigar por qué npm no lo mueve.
  - Cambios: [ws 8.21.0](https://github.com/websockets/ws/releases/tag/8.21.0)
  - Afecta a este proyecto: websocket del dev server de Storybook, desarrollo.
- 🟡→🔵 `uuid` 9.0.1 → 11.1.1. Motivo: major: `@storybook/addon-actions` 8.x pide `uuid` ^9; hay que subir Storybook a 9 o superior (`addon-essentials` desaparece). (npm audit) [GHSA-w5hq-g745-h8pq](https://github.com/advisories/GHSA-w5hq-g745-h8pq)
  - Subir Storybook 8.6.19 → 10.x en `apps/docs`.
  - Breaking changes: [guía de migración de Storybook](https://storybook.js.org/docs/releases/migration-guide)
  - Afecta a este proyecto: el fallo exige llamar a `v3/v5/v6` con `buf`; solo en Storybook, desarrollo.
