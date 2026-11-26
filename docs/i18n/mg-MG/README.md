<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Malagasy** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · **Malagasy** · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Manamarina rakitra SBOM manaraka ny schema JSON ofisialy CycloneDX sy SPDX. Tsy mila tambajotra (offline). Tsy misy antso tambajotra amin'ny fotoana fanamarinana.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Fampiasana

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Mamantatra ho azy ny endrika (CycloneDX na SPDX) sy ny dika famaritana (spec version) avy amin'ny rakitra ny action. Mivoaka amin'ny kaody tsy aotra izy raha tsy mahomby ny fanamarinana.

## Fampidirana (Inputs)

| Fampidirana | Takiana | Safidy fototra | Famaritana |
|-------|----------|---------|-------------|
| `input-file` | eny | -- | Lalana mankany amin'ny rakitra SBOM JSON |
| `format` | tsia | `auto` | `cyclonedx`, `spdx`, na `auto` (fantatra avy amin'ny rakitra) |
| `version` | tsia | `auto` | Dika famaritana (ohatra, `1.6`, `2.3`) na `auto` (fantatra avy amin'ny rakitra) |

## Vokatra (Outputs)

| Vokatra | Famaritana |
|--------|-------------|
| `valid` | `true` raha mandalo ny fanamarinana schema ny SBOM, `false` raha tsy izany |
| `format` | Endrika hita: `cyclonedx` na `spdx` |
| `spec-version` | Dika famaritana hita (ohatra, `1.6`, `2.3`) |
| `error-count` | Tomban'ny isan'ny lesoka fanamarinana (0 rehefa marina) |

## Endrika tohanana

| Endrika | Dika |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON ihany. Tsy tohanana ny SBOM amin'ny endrika XML.

## Fomba tsy fahombiazana

Mivoaka amin'ny kaody 1 ny action ary mametraka `valid=false` amin'ireto tranga ireto:

| Fepetra | Hafatra lesoka |
|-----------|---------------|
| Tsy misy ny rakitra | `Input file not found: <path>` |
| Tsy JSON manan-kery ny rakitra | `Input file is not valid JSON: <path>` |
| Tsy hita ny endrika | `Unable to detect SBOM format` |
| Tsy hita ny dika | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Tsy misy schema ho an'ny dika hita | `Schema file not found for <format> <version>` |
| Tsy mahomby ny fanamarinana schema | vokatra lesoka ajv-cli miaraka amin'ny antsipiriany |

Ny lalana tsy fahombiazana rehetra dia manoratra vokatra (`valid=false`, `error-count=1`) alohan'ny hivoahana, ka afaka mamaky azy ireo ny dingana manaraka na dia misy tsy fahombiazana aza miaraka amin'ny `continue-on-error: true`.

## Ohatra

### Endrika sy dika voatondro mazava

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Famakiana vokatra

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  id: sbom
  with:
    input-file: sbom.json
  continue-on-error: true

- run: |
    echo "Valid: ${{ steps.sbom.outputs.valid }}"
    echo "Format: ${{ steps.sbom.outputs.format }}"
    echo "Version: ${{ steps.sbom.outputs.spec-version }}"
    echo "Errors: ${{ steps.sbom.outputs.error-count }}"
```

### Fanamarinana rakitra maromaro

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

### Fanakanana PR (PR gating)

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
        run: |
          echo "### SBOM Validation" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Valid:** ${{ steps.sbom.outputs.valid }}" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Format:** ${{ steps.sbom.outputs.format }}" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Version:** ${{ steps.sbom.outputs.spec-version }}" >> "$GITHUB_STEP_SUMMARY"
```

## Modely fiarovana

- **Tsy misy antso tambajotra amin'ny fotoana fanamarinana.** Tafiditra mivantana ao amin'ny tahiry ny schema. Ny hany antso tambajotra dia `npm install ajv-cli ajv-formats` mandritra ny fanomanana.
- **Tsy misy telemetria.** Tsy mandefa fampahalalana any ivelany na manangona angon-drakitra ny action.
- **Mandeha ao anatin'ny kaonteneran'ny asa.** Tsy misy fakana Docker, tsy misy tolotra ivelany.
- **Alalana farany kely indrindra.** Tsy mila afa-tsy `contents: read`.

Ho an'ny antoka ambony kokoa, apetraho amin'ny SHA commit feno:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Fifanarahana

- Mandeha amin'ny `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Mila Node.js (efa napetraka mialoha amin'ny runner rehetra ampian'ny GitHub).
- Mila `jq` (efa napetraka mialoha amin'ny runner rehetra ampian'ny GitHub).
- Ny runner ampian'ny tena manokana (self-hosted) dia mila Node.js >= 18 sy jq ao amin'ny PATH.

## Fanavaozana schema

Hanavaozana ny schema ao amin'ny tahiry avy amin'ny loharano ambony:

```bash
./scripts/update-schemas.sh
```

## Fahazoan-dalana

Apache-2.0 -- jereo ny [LICENSE](../../../LICENSE).
