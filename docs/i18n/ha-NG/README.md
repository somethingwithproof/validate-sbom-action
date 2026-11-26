<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Hausa** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · **Hausa** · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Tantance fayilolin SBOM bisa hukuma ta tsarin JSON schemas na CycloneDX da SPDX. Ba tare da intanet ba (offline). Babu kiran hanyar sadarwa a lokacin tantancewa.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Amfani

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Aikin yana gano tsari (CycloneDX ko SPDX) da sigar ƙayyadaddun bayanai (spec version) ta atomatik daga fayil ɗin. Yana fita da lambar da ba sifili ba idan tantancewa ta gaza.

## Shigarwa

| Shigarwa | Ana buƙata | Tsoho | Bayani |
|-------|----------|---------|-------------|
| `input-file` | eh | -- | Hanyar zuwa fayil ɗin JSON na SBOM |
| `format` | a'a | `auto` | `cyclonedx`, `spdx`, ko `auto` (gano daga fayil) |
| `version` | a'a | `auto` | Sigar ƙayyadaddun bayanai (misali, `1.6`, `2.3`) ko `auto` (gano daga fayil) |

## Fitarwa

| Fitarwa | Bayani |
|--------|-------------|
| `valid` | `true` idan SBOM ya ci nasarar tantance schema, `false` in ba haka ba |
| `format` | Tsarin da aka gano: `cyclonedx` ko `spdx` |
| `spec-version` | Sigar ƙayyadaddun bayanai da aka gano (misali, `1.6`, `2.3`) |
| `error-count` | Kimanin adadin kurakuran tantancewa (0 idan yana da inganci) |

## Tsare-tsaren da Ake Goyon Baya

| Tsari | Sigogi |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON kaɗai. Ba a goyon bayan SBOMs na XML.

## Yanayin Gazawa

Aikin yana fita da lamba 1 kuma yana saita `valid=false` a cikin waɗannan yanayi:

| Yanayi | Saƙon kuskure |
|-----------|---------------|
| Fayil ba ya wanzu | `Input file not found: <path>` |
| Fayil ba ingantaccen JSON ba ne | `Input file is not valid JSON: <path>` |
| Ba za a iya gano tsari ba | `Unable to detect SBOM format` |
| Ba za a iya gano siga ba | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Babu schema don sigar da aka gano | `Schema file not found for <format> <version>` |
| Tantance schema ya gaza | fitarwar kuskuren ajv-cli tare da cikakkun bayanai |

Duk hanyoyin gazawa suna rubuta fitarwa (`valid=false`, `error-count=1`) kafin fita, don matakan gaba su iya karanta su ko da a lokacin gazawa tare da `continue-on-error: true`.

## Misalai

### Bayyanannen tsari da siga

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Karanta fitarwa

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

### Tantance fayiloli da yawa

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

### Tantancewar PR (PR gating)

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

## Tsarin Tsaro

- **Babu kiran hanyar sadarwa a lokacin tantancewa.** An haɗa schemas a cikin ma'ajiyar. Kiran hanyar sadarwa kaɗai shi ne `npm install ajv-cli ajv-formats` yayin saitawa.
- **Babu tattara bayanan amfani (telemetry).** Aikin ba ya aika bayanai waje ko tattara bayanai.
- **Yana gudana a cikin kwantenar aiki.** Babu jawo Docker, babu sabis na waje.
- **Mafi ƙarancin izini.** Yana buƙatar `contents: read` kaɗai.

Don ƙarin tabbaci, liƙa zuwa cikakken SHA na commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Dacewa

- Yana gudana a kan `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Yana buƙatar Node.js (an riga an girka a kan duk masu gudanarwa da GitHub ke ɗaukar nauyi).
- Yana buƙatar `jq` (an riga an girka a kan duk masu gudanarwa da GitHub ke ɗaukar nauyi).
- Masu gudanarwa masu zaman kansu (self-hosted runners) suna buƙatar Node.js >= 18 da jq a cikin PATH.

## Sabunta Schema

Don sabunta schemas da aka haɗa daga tushe (upstream):

```bash
./scripts/update-schemas.sh
```

## Lasisi

Apache-2.0 -- duba [LICENSE](../../../LICENSE).
