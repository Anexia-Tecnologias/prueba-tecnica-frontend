# Vulnerabilidades

<!-- Mantenido por la skill dependabot-auto. «Majors pendientes» y «Paquetes» se regeneran en cada ejecución; «Registro» solo crece. No editar a mano. -->

## Majors pendientes

| Paquete | Instalada | Corrige | Última | Decisión | Motivo | Alertas |
|---|---|---|---|---|---|---|
| `minimatch` | 3.1.5 / 9.0.9 | 11.0.1 | 11.0.3 (8 y 2 majors) | ⚪ No se actualiza (propuesta) | Solo herramientas de desarrollo (`eslint`, `typescript-eslint`, `eslint-plugin-react`, `glob` del docgen de Storybook) con patrones escritos en el repo; nada de `apps/` ni `packages/` lo importa. Premisa: [`packages/eslint-config/package.json`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/packages/eslint-config/package.json), busca:'minimatch' en `apps` y `packages` | [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249) |

## Registro

### 2026-10-31

Repo sin alertas de Dependabot: hallazgos de `npm audit` sobre `package-lock.json` de la raíz.

#### ⚪ Propuestas para descartar
- 🟡→⚪ `minimatch` 3.1.5 / 9.0.9, 1 advisory (DoS por amplificación de patrones). No aplica: hace falta un patrón controlado por un atacante, y solo lo usan `eslint`, `typescript-eslint`, `eslint-plugin-react` y el `glob` del docgen de Storybook, devDependencies que procesan patrones escritos en el repo (config de ESLint, `tsconfig`, `stories` de [`apps/docs/.storybook/main.ts`](https://github.com/Anexia-Tecnologias/prueba-tecnica-frontend/blob/1b63dbf61bfd4319e0f63d77c8e84261b6c964fd/apps/docs/.storybook/main.ts#L4)). Ningún fichero de `apps/` ni `packages/` lo importa. Arreglo solo en 11.0.1 (major). Premisa: packages/eslint-config/package.json@ba541f5, busca:'minimatch' en apps@e69de29, busca:'minimatch' en packages@e69de29. (npm audit) [GHSA-g3hv-75wg-m249](https://github.com/advisories/GHSA-g3hv-75wg-m249)

### 2026-10-29

Repo sin alertas de Dependabot: hallazgos de `npm audit` sobre `package-lock.json` de la raíz.

#### ✅ Actualizadas
- 🟠 `brace-expansion` 1.1.12 / 2.0.2 → 1.1.21 / 2.1.7 (minor/patch, transitiva). (npm audit) [GHSA-3jxr-9vmj-r5cp](https://github.com/advisories/GHSA-3jxr-9vmj-r5cp) [GHSA-6j4f-fj2g-mc7p](https://github.com/advisories/GHSA-6j4f-fj2g-mc7p) [GHSA-f886-m6hf-6m8v](https://github.com/advisories/GHSA-f886-m6hf-6m8v) [GHSA-mh99-v99m-4gvg](https://github.com/advisories/GHSA-mh99-v99m-4gvg) [GHSA-q2hr-2g5m-vwhr](https://github.com/advisories/GHSA-q2hr-2g5m-vwhr) [GHSA-qhr7-859c-m2p7](https://github.com/advisories/GHSA-qhr7-859c-m2p7) [GHSA-rgw5-rvv9-x895](https://github.com/advisories/GHSA-rgw5-rvv9-x895)
- 🟠 `minimatch` 3.1.2 / 9.0.5 → 3.1.5 / 9.0.9 (minor/patch, transitiva). (npm audit) [GHSA-23c5-xmqv-rm74](https://github.com/advisories/GHSA-23c5-xmqv-rm74) [GHSA-3ppc-4f35-3m26](https://github.com/advisories/GHSA-3ppc-4f35-3m26) [GHSA-7r86-cg39-jmmj](https://github.com/advisories/GHSA-7r86-cg39-jmmj)
- 🟠 `picomatch` 2.3.1 / 4.0.3 → 2.3.2 / 4.0.7 (minor/patch, transitiva). (npm audit) [GHSA-3v7f-55p6-f55p](https://github.com/advisories/GHSA-3v7f-55p6-f55p) [GHSA-c2c7-rcm5-vvqj](https://github.com/advisories/GHSA-c2c7-rcm5-vvqj)
