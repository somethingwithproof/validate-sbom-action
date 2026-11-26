<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · **Español** · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · **Español** · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Valida archivos SBOM frente a los esquemas JSON oficiales de CycloneDX y SPDX. Sin conexión. Sin llamadas de red durante la validación.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Uso

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

La acción detecta automáticamente el formato (CycloneDX o SPDX) y la versión de la especificación a partir del archivo. Finaliza con un código distinto de cero si la validación falla.

## Entradas

| Entrada | Requerida | Valor predeterminado | Descripción |
|-------|----------|---------|-------------|
| `input-file` | sí | -- | Ruta al archivo SBOM en formato JSON |
| `format` | no | `auto` | `cyclonedx`, `spdx` o `auto` (detectar desde el archivo) |
| `version` | no | `auto` | Versión de la especificación (p. ej., `1.6`, `2.3`) o `auto` (detectar desde el archivo) |

## Salidas

| Salida | Descripción |
|--------|-------------|
| `valid` | `true` si el SBOM supera la validación de esquema, `false` en caso contrario |
| `format` | Formato detectado: `cyclonedx` o `spdx` |
| `spec-version` | Versión de la especificación detectada (p. ej., `1.6`, `2.3`) |
| `error-count` | Número aproximado de errores de validación (0 cuando es válido) |

## Formatos compatibles

| Formato | Versiones |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Solo JSON. No se admiten SBOM en formato XML.

## Modos de fallo

La acción finaliza con código 1 y establece `valid=false` en los siguientes casos:

| Condición | Mensaje de error |
|-----------|---------------|
| El archivo no existe | `Input file not found: <path>` |
| El archivo no es JSON válido | `Input file is not valid JSON: <path>` |
| No se puede detectar el formato | `Unable to detect SBOM format` |
| No se puede detectar la versión | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| No hay esquema para la versión detectada | `Schema file not found for <format> <version>` |
| Falla la validación del esquema | Salida de error de ajv-cli con detalles |

## Ejemplos

### Formato y versión explícitos

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Lectura de salidas

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  id: sbom
  with:
    input-file: sbom.json
  continue-on-error: true

- env:
    SBOM_VALID: ${{ steps.sbom.outputs.valid }}
    SBOM_FORMAT: ${{ steps.sbom.outputs.format }}
    SBOM_SPEC_VERSION: ${{ steps.sbom.outputs.spec-version }}
    SBOM_ERROR_COUNT: ${{ steps.sbom.outputs.error-count }}
  run: |
    echo "Valid: $SBOM_VALID"
    echo "Format: $SBOM_FORMAT"
    echo "Version: $SBOM_SPEC_VERSION"
    echo "Errors: $SBOM_ERROR_COUNT"
```

### Validación de múltiples archivos

```yaml
strategy:
  fail-fast: false
  matrix:
    sbom:
      - path: sbom-backend.json
        format: cyclonedx
      - path: sbom-frontend.json
        format: spdx
steps:
  - uses: actions/checkout@v4
  - uses: somethingwithproof/validate-sbom-action@v1
    with:
      input-file: ${{ matrix.sbom.path }}
      format: ${{ matrix.sbom.format }}
```

### Control de validación en PR

```yaml
name: SBOM Gate

on:
  pull_request:
    branches: [main]

permissions:
  contents: read

jobs:
  validate-sbom:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - uses: actions/checkout@v4
      - uses: somethingwithproof/validate-sbom-action@v1
        id: sbom
        with:
          input-file: sbom.json
      - name: Summary
        if: always()
        env:
          SBOM_VALID: ${{ steps.sbom.outputs.valid }}
          SBOM_FORMAT: ${{ steps.sbom.outputs.format }}
          SBOM_SPEC_VERSION: ${{ steps.sbom.outputs.spec-version }}
        run: |
          echo "### SBOM Validation" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Valid:** $SBOM_VALID" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Format:** $SBOM_FORMAT" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Version:** $SBOM_SPEC_VERSION" >> "$GITHUB_STEP_SUMMARY"
```

## Modelo de seguridad

- **Sin llamadas de red durante la validación.** Los esquemas están incluidos directamente en el repositorio. La única llamada de red es `npm install ajv-cli ajv-formats` durante la configuración.
- **Sin telemetría.** La acción no envía datos externos ni recopila información.
- **Se ejecuta en el contenedor del trabajo.** Sin descargas de Docker ni servicios externos.
- **Mínimo privilegio.** Solo requiere `contents: read`.

Para mayor garantía, fije la acción a un SHA de commit completo:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Compatibilidad

- Se ejecuta en `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Requiere Node.js (preinstalado en todos los runners alojados en GitHub).
- Requiere `jq` (preinstalado en todos los runners alojados en GitHub).
- Los runners autoalojados necesitan Node.js >= 18 y jq en el PATH.

## Actualizaciones de esquemas

Para actualizar los esquemas incluidos desde upstream:

```bash
./scripts/update-schemas.sh
```

## Licencia

Apache-2.0 -- consulte [LICENSE](../../../LICENSE).
