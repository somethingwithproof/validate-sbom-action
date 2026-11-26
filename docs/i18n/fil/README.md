<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Filipino** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · **Filipino**
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Patunayan ang mga SBOM file laban sa mga opisyal na JSON schema ng CycloneDX at SPDX. Offline. Walang network call sa oras ng pagpapatunay.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Paggamit

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Awtomatikong tinutukoy ng action ang format (CycloneDX o SPDX) at ang spec version mula sa file. Nag-e-exit ito nang hindi zero kung mabigo ang pagpapatunay.

## Mga Input

| Input | Kinakailangan | Default | Paglalarawan |
|-------|----------|---------|-------------|
| `input-file` | oo | -- | Path patungo sa SBOM JSON file |
| `format` | hindi | `auto` | `cyclonedx`, `spdx`, o `auto` (tukuyin mula sa file) |
| `version` | hindi | `auto` | Spec version (hal., `1.6`, `2.3`) o `auto` (tukuyin mula sa file) |

## Mga Output

| Output | Paglalarawan |
|--------|-------------|
| `valid` | `true` kung pumasa ang SBOM sa pagpapatunay ng schema, `false` kung hindi |
| `format` | Natukoy na format: `cyclonedx` o `spdx` |
| `spec-version` | Natukoy na spec version (hal., `1.6`, `2.3`) |
| `error-count` | Tinatayang bilang ng mga error sa pagpapatunay (0 kapag wasto) |

## Mga Sinusuportahang Format

| Format | Mga Bersyon |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON lamang. Hindi sinusuportahan ang mga XML SBOM.

## Mga Paraan ng Pagkabigo

Nag-e-exit ang action na may code 1 at nagtatakda ng `valid=false` sa mga kasong ito:

| Kondisyon | Mensahe ng error |
|-----------|---------------|
| Walang ganoong file | `Input file not found: <path>` |
| Hindi wastong JSON ang file | `Input file is not valid JSON: <path>` |
| Hindi matukoy ang format | `Unable to detect SBOM format` |
| Hindi matukoy ang bersyon | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Walang schema para sa natukoy na bersyon | `Schema file not found for <format> <version>` |
| Nabigo ang pagpapatunay ng schema | Error output ng ajv-cli na may mga detalye |

Nagsusulat ang lahat ng failure path ng mga output (`valid=false`, `error-count=1`) bago mag-exit, kaya mababasa pa rin ng mga susunod na hakbang ang mga ito kahit mabigo kapag may `continue-on-error: true`.

## Mga Halimbawa

### Tahasang format at bersyon

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Pagbabasa ng mga output

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

### Pagpapatunay ng maramihang file

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

### PR gating

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

## Modelo ng Seguridad

- **Walang network call sa oras ng pagpapatunay.** Naka-vendor ang mga schema sa repository. Ang tanging network call ay `npm install ajv-cli ajv-formats` habang nagse-setup.
- **Walang telemetry.** Hindi nakikipag-ugnayan sa panlabas na server o nangongolekta ng datos ang action.
- **Tumatakbo sa loob ng job container.** Walang Docker pull, walang panlabas na serbisyo.
- **Pinakamababang pribilehiyo.** Nangangailangan lamang ng `contents: read`.

Para sa mas mataas na katiyakan, i-pin sa buong commit SHA:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Pagiging Tugma

- Tumatakbo sa `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Nangangailangan ng Node.js (paunang naka-install sa lahat ng runner na naka-host sa GitHub).
- Nangangailangan ng `jq` (paunang naka-install sa lahat ng runner na naka-host sa GitHub).
- Kailangan ng mga self-hosted runner ng Node.js >= 18 at jq sa PATH.

## Mga Update sa Schema

Upang i-refresh ang mga naka-vendor na schema mula sa upstream:

```bash
./scripts/update-schemas.sh
```

## Lisensya

Apache-2.0 -- tingnan ang [LICENSE](../../../LICENSE).
