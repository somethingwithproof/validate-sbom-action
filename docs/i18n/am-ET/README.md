<!-- translations:start -->
**Languages:** [English](../../../README.md) · **አማርኛ** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · **አማርኛ** · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

የSBOM ፋይሎችን ከይፋዊ የCycloneDX እና SPDX JSON ስኪማዎች ጋር ያረጋግጡ። ከመስመር ውጭ። በማረጋገጫ ጊዜ ምንም የአውታረ መረብ ጥሪዎች የሉም።

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## አጠቃቀም

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

ድርጊቱ ቅርጸቱን (CycloneDX ወይም SPDX) እና የዝርዝር መግለጫ ሥሪቱን ከፋይሉ በራስ-ሰር ይለያል። ማረጋገጫው ካልተሳካ ከዜሮ ውጪ በሆነ ኮድ ይወጣል።

## ግቤቶች

| ግቤት | ያስፈልጋል | ነባሪ | መግለጫ |
|-------|----------|---------|-------------|
| `input-file` | አዎ | -- | ወደ SBOM JSON ፋይሉ የሚወስድ ዱካ |
| `format` | አይ | `auto` | `cyclonedx`፣ `spdx` ወይም `auto` (ከፋይሉ ይለያል) |
| `version` | አይ | `auto` | የዝርዝር መግለጫ ሥሪት (ለምሳሌ፣ `1.6`፣ `2.3`) ወይም `auto` (ከፋይሉ ይለያል) |

## ውጤቶች

| ውጤት | መግለጫ |
|--------|-------------|
| `valid` | SBOM የስኪማ ማረጋገጫን ካለፈ `true`፣ አለበለዚያ `false` |
| `format` | የተለየው ቅርጸት፦ `cyclonedx` ወይም `spdx` |
| `spec-version` | የተለየው የዝርዝር መግለጫ ሥሪት (ለምሳሌ፣ `1.6`፣ `2.3`) |
| `error-count` | ግምታዊ የማረጋገጫ ስህተቶች ብዛት (ትክክል ሲሆን 0) |

## የሚደገፉ ቅርጸቶች

| ቅርጸት | ሥሪቶች |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON ብቻ። የXML SBOM ፋይሎች አይደገፉም።

## የብልሽት ሁኔታዎች

ድርጊቱ በእነዚህ ሁኔታዎች ውስጥ በኮድ 1 ይወጣል እንዲሁም `valid=false`ን ያዘጋጃል፦

| ሁኔታ | የስህተት መልዕክት |
|-----------|---------------|
| ፋይሉ የለም | `Input file not found: <path>` |
| ፋይሉ ትክክለኛ JSON አይደለም | `Input file is not valid JSON: <path>` |
| ቅርጸቱ ሊለይ አልቻለም | `Unable to detect SBOM format` |
| ሥሪቱ ሊለይ አልቻለም | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| ለተለየው ሥሪት ስኪማ የለም | `Schema file not found for <format> <version>` |
| የስኪማ ማረጋገጫ አልተሳካም | የajv-cli የስህተት ውጤት ከዝርዝሮች ጋር |

ሁሉም የብልሽት መንገዶች ከመውጣታቸው በፊት ውጤቶችን (`valid=false`፣ `error-count=1`) ይጽፋሉ፣ ስለዚህ ተከታይ ደረጃዎች በ`continue-on-error: true` አማካኝነት ብልሽት ሲያጋጥም እንኳ ሊያነቧቸው ይችላሉ።

## ምሳሌዎች

### ግልጽ ቅርጸት እና ሥሪት

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### ውጤቶችን ማንበብ

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

### በርካታ ፋይሎችን ማረጋገጥ

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

### የPR መቆጣጠሪያ

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

## የደህንነት ሞዴል

- **በማረጋገጫ ጊዜ ምንም የአውታረ መረብ ጥሪዎች የሉም።** ስኪማዎቹ በማከማቻው ውስጥ ተካተዋል። ብቸኛው የአውታረ መረብ ጥሪ በማዋቀር ጊዜ የሚደረገው `npm install ajv-cli ajv-formats` ነው።
- **ምንም ቴሌሜትሪ የለም።** ድርጊቱ ወደ ውጭ ምንም መረጃ አይልክም ወይም ውሂብ አይሰበስብም።
- **በሥራ ኮንቴይነሩ ውስጥ ይሠራል።** ምንም የDocker ማውረድ ወይም ውጫዊ አገልግሎቶች የሉም።
- **አነስተኛ ፈቃድ።** `contents: read`ን ብቻ ይፈልጋል።

ለከፍተኛ ዋስትና፣ ወደ ሙሉ የcommit SHA ያስሩ፦

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## ተኳሃኝነት

- በ`ubuntu-latest`፣ `ubuntu-22.04`፣ `ubuntu-24.04` ላይ ይሠራል።
- Node.jsን ይፈልጋል (በሁሉም በGitHub በሚስተናገዱ runners ላይ አስቀድሞ ተጭኗል)።
- `jq`ን ይፈልጋል (በሁሉም በGitHub በሚስተናገዱ runners ላይ አስቀድሞ ተጭኗል)።
- በራስ የሚስተናገዱ runners Node.js >= 18 እና በPATH ውስጥ jq ያስፈልጋቸዋል።

## የስኪማ ዝማኔዎች

በማከማቻው ውስጥ የተካተቱትን ስኪማዎች ከዋናው ምንጭ ለማደስ፦

```bash
./scripts/update-schemas.sh
```

## ፈቃድ

Apache-2.0 -- [LICENSE](../../../LICENSE)ን ይመልከቱ።
