<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Afrikaans** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** **Afrikaans** · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Valideer SBOM-lêers teen amptelike CycloneDX- en SPDX-JSON-skemas. Vanlyn. Geen netwerkoproepe tydens validering nie.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Gebruik

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Die aksie bespeur outomaties die formaat (CycloneDX of SPDX) en spesifikasieweergawe vanaf die lêer. Dit sluit af met 'n nie-nul-kode indien validering misluk.

## Invoere

| Invoer | Vereis | Verstek | Beskrywing |
|-------|----------|---------|-------------|
| `input-file` | ja | -- | Pad na die SBOM-JSON-lêer |
| `format` | nee | `auto` | `cyclonedx`, `spdx` of `auto` (bespeur vanaf lêer) |
| `version` | nee | `auto` | Spesifikasieweergawe (bv. `1.6`, `2.3`) of `auto` (bespeur vanaf lêer) |

## Uitvoere

| Uitvoer | Beskrywing |
|--------|-------------|
| `valid` | `true` indien die SBOM skemavalidering slaag, andersins `false` |
| `format` | Bespeurde formaat: `cyclonedx` of `spdx` |
| `spec-version` | Bespeurde spesifikasieweergawe (bv. `1.6`, `2.3`) |
| `error-count` | Benaderde aantal valideringsfoute (0 wanneer geldig) |

## Ondersteunde formate

| Formaat | Weergawes |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Slegs JSON. XML-SBOM's word nie ondersteun nie.

## Mislukkingsmodusse

Die aksie sluit af met kode 1 en stel `valid=false` in hierdie gevalle:

| Toestand | Foutboodskap |
|-----------|---------------|
| Lêer bestaan nie | `Input file not found: <path>` |
| Lêer is nie geldige JSON nie | `Input file is not valid JSON: <path>` |
| Formaat kan nie bespeur word nie | `Unable to detect SBOM format` |
| Weergawe kan nie bespeur word nie | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Geen skema vir bespeurde weergawe nie | `Schema file not found for <format> <version>` |
| Skemavalidering misluk | ajv-cli-foutuitvoer met besonderhede |

Alle mislukkingspaaie skryf uitvoere (`valid=false`, `error-count=1`) voordat dit afsluit, sodat stroomaf-stappe dit selfs by mislukking met `continue-on-error: true` kan lees.

## Voorbeelde

### Eksplisiete formaat en weergawe

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Lees uitvoere

```yaml
- uses: thomasvincent/validate-sbom-action@v1
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

### Valideer veelvuldige lêers

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
  - uses: thomasvincent/validate-sbom-action@v1
    with:
      input-file: ${{ matrix.sbom.path }}
      format: ${{ matrix.sbom.format }}
```

### PR-hekbeheer

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
      - uses: thomasvincent/validate-sbom-action@v1
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

## Sekuriteitsmodel

- **Geen netwerkoproepe tydens validering nie.** Skemas word in die bewaarplek ingesluit. Die enigste netwerkoproep is `npm install ajv-cli ajv-formats` tydens opstelling.
- **Geen telemetrie nie.** Die aksie skakel nie huis toe of samel data in nie.
- **Loop in die taakhouer.** Geen Docker-aflaai, geen eksterne dienste nie.
- **Minste voorregte.** Vereis slegs `contents: read`.

Vir hoër versekering, pen vas aan 'n volledige commit-SHA:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Versoenbaarheid

- Loop op `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Vereis Node.js (vooraf geïnstalleer op alle GitHub-gehuisveste lopers).
- Vereis `jq` (vooraf geïnstalleer op alle GitHub-gehuisveste lopers).
- Self-gehuisveste lopers benodig Node.js >= 18 en jq in PATH.

## Skema-opdaterings

Om ingeslote skemas vanaf stroomop te verfris:

```bash
./scripts/update-schemas.sh
```

## Lisensie

Apache-2.0 -- sien [LICENSE](../../../LICENSE).
