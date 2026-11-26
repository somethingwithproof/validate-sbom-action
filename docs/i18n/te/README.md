<!-- translations:start -->
**Languages:** [English](../../../README.md) · **తెలుగు** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · **తెలుగు** · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

అధికారిక CycloneDX మరియు SPDX JSON స్కీమాలకు అనుగుణంగా SBOM ఫైళ్లను ధృవీకరించండి. ఆఫ్‌లైన్. ధృవీకరణ సమయంలో నెట్‌వర్క్ కాల్స్ ఉండవు.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## వినియోగం

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

ఈ యాక్షన్ ఫైల్ నుండి ఫార్మాట్ (CycloneDX లేదా SPDX) మరియు స్పెక్ వెర్షన్‌ను స్వయంచాలకంగా గుర్తిస్తుంది. ధృవీకరణ విఫలమైతే నాన్-జీరో ఎగ్జిట్ కోడ్‌తో ముగుస్తుంది.

## ఇన్‌పుట్‌లు

| ఇన్‌పుట్ | తప్పనిసరి | డిఫాల్ట్ | వివరణ |
|-------|----------|---------|-------------|
| `input-file` | అవును | -- | SBOM JSON ఫైల్ యొక్క పాత్ |
| `format` | కాదు | `auto` | `cyclonedx`, `spdx`, లేదా `auto` (ఫైల్ నుండి గుర్తించండి) |
| `version` | కాదు | `auto` | స్పెక్ వెర్షన్ (ఉదా., `1.6`, `2.3`) లేదా `auto` (ఫైల్ నుండి గుర్తించండి) |

## అవుట్‌పుట్‌లు

| అవుట్‌పుట్ | వివరణ |
|--------|-------------|
| `valid` | SBOM స్కీమా ధృవీకరణలో ఉత్తీర్ణమైతే `true`, లేకపోతే `false` |
| `format` | గుర్తించబడిన ఫార్మాట్: `cyclonedx` లేదా `spdx` |
| `spec-version` | గుర్తించబడిన స్పెక్ వెర్షన్ (ఉదా., `1.6`, `2.3`) |
| `error-count` | సుమారు ధృవీకరణ లోపాల సంఖ్య (చెల్లుబాటు అయినప్పుడు 0) |

## మద్దతు ఉన్న ఫార్మాట్లు

| ఫార్మాట్ | వెర్షన్లు |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON మాత్రమే. XML SBOMలకు మద్దతు లేదు.

## వైఫల్య స్థితులు

ఈ సందర్భాల్లో యాక్షన్ కోడ్ 1తో ముగిసి `valid=false`గా సెట్ చేస్తుంది:

| పరిస్థితి | లోపం సందేశం |
|-----------|---------------|
| ఫైల్ ఉనికిలో లేదు | `Input file not found: <path>` |
| ఫైల్ చెల్లుబాటు అయ్యే JSON కాదు | `Input file is not valid JSON: <path>` |
| ఫార్మాట్‌ను గుర్తించలేకపోయింది | `Unable to detect SBOM format` |
| వెర్షన్‌ను గుర్తించలేకపోయింది | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| గుర్తించబడిన వెర్షన్ కోసం స్కీమా లేదు | `Schema file not found for <format> <version>` |
| స్కీమా ధృవీకరణ విఫలమైంది | వివరాలతో కూడిన ajv-cli లోపం అవుట్‌పుట్ |

అన్ని వైఫల్య మార్గాలు నిష్క్రమించే ముందే అవుట్‌పుట్‌లను (`valid=false`, `error-count=1`) వ్రాస్తాయి, కాబట్టి `continue-on-error: true`తో వైఫల్యం జరిగినప్పటికీ డౌన్‌స్ట్రీమ్ దశలు వాటిని చదవగలవు.

## ఉదాహరణలు

### స్పష్టమైన ఫార్మాట్ మరియు వెర్షన్

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### అవుట్‌పుట్‌లను చదవడం

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

### బహుళ ఫైళ్లను ధృవీకరించడం

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

### PR గేటింగ్

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

## భద్రతా నమూనా

- **ధృవీకరణ సమయంలో నెట్‌వర్క్ కాల్స్ లేవు.** స్కీమాలు రిపోజిటరీలోనే వెండర్ చేయబడ్డాయి. సెటప్ సమయంలో `npm install ajv-cli ajv-formats` మాత్రమే ఏకైక నెట్‌వర్క్ కాల్.
- **టెలిమెట్రీ లేదు.** ఈ యాక్షన్ బయటకు సమాచారం పంపదు లేదా డేటాను సేకరించదు.
- **జాబ్ కంటైనర్‌లో నడుస్తుంది.** Docker పుల్ లేదు, బాహ్య సేవలు లేవు.
- **కనీస అధికారాలు.** కేవలం `contents: read` మాత్రమే అవసరం.

మరింత భరోసా కోసం, పూర్తి కమిట్ SHAకు పిన్ చేయండి:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## అనుకూలత

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`లో నడుస్తుంది.
- Node.js అవసరం (అన్ని GitHub-హోస్టెడ్ రన్నర్లలో ముందుగానే ఇన్‌స్టాల్ చేయబడి ఉంటుంది).
- `jq` అవసరం (అన్ని GitHub-హోస్టెడ్ రన్నర్లలో ముందుగానే ఇన్‌స్టాల్ చేయబడి ఉంటుంది).
- సెల్ఫ్-హోస్టెడ్ రన్నర్లకు Node.js >= 18 మరియు PATHలో jq అవసరం.

## స్కీమా అప్‌డేట్లు

అప్‌స్ట్రీమ్ నుండి వెండర్ చేయబడిన స్కీమాలను రిఫ్రెష్ చేయడానికి:

```bash
./scripts/update-schemas.sh
```

## లైసెన్స్

Apache-2.0 -- [LICENSE](../../../LICENSE) చూడండి.
