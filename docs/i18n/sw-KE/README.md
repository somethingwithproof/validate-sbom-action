<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Kiswahili** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · **Kiswahili** · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Thibitisha faili za SBOM dhidi ya skima rasmi za JSON za CycloneDX na SPDX. Nje ya mtandao. Hakuna maombi ya mtandao wakati wa uthibitishaji.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Matumizi

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Kitendo hiki hugundua kiotomatiki muundo (CycloneDX au SPDX) na toleo la vipimo kutoka kwenye faili. Hutoka na msimbo usio sifuri iwapo uthibitishaji utashindwa.

## Data za Ingizo

| Ingizo | Inahitajika | Chaguo-msingi | Maelezo |
|-------|----------|---------|-------------|
| `input-file` | ndiyo | -- | Njia ya faili ya JSON ya SBOM |
| `format` | hapana | `auto` | `cyclonedx`, `spdx`, au `auto` (gundua kutoka faili) |
| `version` | hapana | `auto` | Toleo la vipimo (k.m., `1.6`, `2.3`) au `auto` (gundua kutoka faili) |

## Matokeo

| Tokeo | Maelezo |
|--------|-------------|
| `valid` | `true` ikiwa SBOM inafaulu uthibitishaji wa skima, `false` vinginevyo |
| `format` | Muundo uliogunduliwa: `cyclonedx` au `spdx` |
| `spec-version` | Toleo la vipimo lililogunduliwa (k.m., `1.6`, `2.3`) |
| `error-count` | Idadi ya takriban ya makosa ya uthibitishaji (0 inapokuwa sahihi) |

## Miundo Inayotumika

| Muundo | Matoleo |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON pekee. Faili za SBOM za XML hazitumiki.

## Hali za Kushindwa

Kitendo hutoka na msimbo 1 na kuweka `valid=false` katika hali hizi:

| Hali | Ujumbe wa hitilafu |
|-----------|---------------|
| Faili haipo | `Input file not found: <path>` |
| Faili si JSON sahihi | `Input file is not valid JSON: <path>` |
| Muundo hauwezi kugunduliwa | `Unable to detect SBOM format` |
| Toleo haliwezi kugunduliwa | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Hakuna skima ya toleo lililogunduliwa | `Schema file not found for <format> <version>` |
| Uthibitishaji wa skima umeshindwa | matokeo ya hitilafu ya ajv-cli yenye maelezo |

Njia zote za kushindwa huandika matokeo (`valid=false`, `error-count=1`) kabla ya kutoka, ili hatua zinazofuata ziweze kuyasoma hata wakati wa kushindwa kwa kutumia `continue-on-error: true`.

## Mifano

### Muundo na toleo la wazi

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Soma matokeo

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

### Thibitisha faili nyingi

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

### Uthibitishaji wa lazima wa PR

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

## Mfumo wa Usalama

- **Hakuna maombi ya mtandao wakati wa uthibitishaji.** Skima zimehifadhiwa moja kwa moja katika hazina. Ombi pekee la mtandao ni `npm install ajv-cli ajv-formats` wakati wa maandalizi.
- **Hakuna telemetri.** Kitendo hakitumi taarifa nje wala hakikusanyi data.
- **Huendeshwa ndani ya kontena ya kazi.** Hakuna upakuaji wa Docker, hakuna huduma za nje.
- **Ruhusa za chini kabisa.** Inahitaji `contents: read` pekee.

Kwa uhakika wa juu zaidi, funga kwenye SHA kamili ya commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Uoanifu

- Huendeshwa kwenye `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Inahitaji Node.js (imesakinishwa tayari kwenye runners zote zinazopangishwa na GitHub).
- Inahitaji `jq` (imesakinishwa tayari kwenye runners zote zinazopangishwa na GitHub).
- Runners zinazopangishwa kibinafsi zinahitaji Node.js >= 18 na jq katika PATH.

## Masasisho ya Skima

Ili kusasisha skima zilizohifadhiwa kutoka chanzo kikuu:

```bash
./scripts/update-schemas.sh
```

## Leseni

Apache-2.0 -- tazama [LICENSE](../../../LICENSE).
