<!-- translations:start -->
**Languages:** [English](../../../README.md) · **தமிழ்** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · **தமிழ்** · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

அதிகாரப்பூர்வ CycloneDX மற்றும் SPDX JSON திட்டவரைவுகளுக்கு (schemas) எதிராக SBOM கோப்புகளைச் சரிபார்க்கவும். ஆஃப்லைன். சரிபார்ப்பு நேரத்தில் பிணைய அழைப்புகள் எதுவும் இல்லை.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## பயன்பாடு

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

இந்தச் செயல் கோப்பிலிருந்து வடிவம் (CycloneDX அல்லது SPDX) மற்றும் விவரக்குறிப்புப் பதிப்பைத் தானாகவே கண்டறிகிறது. சரிபார்ப்பு தோல்வியடைந்தால் இது பூஜ்ஜியமற்ற குறியீட்டுடன் வெளியேறும்.

## உள்ளீடுகள்

| உள்ளீடு | கட்டாயம் | இயல்புநிலை | விளக்கம் |
|-------|----------|---------|-------------|
| `input-file` | ஆம் | -- | SBOM JSON கோப்பிற்கான பாதை |
| `format` | இல்லை | `auto` | `cyclonedx`, `spdx`, அல்லது `auto` (கோப்பிலிருந்து கண்டறியவும்) |
| `version` | இல்லை | `auto` | விவரக்குறிப்புப் பதிப்பு (எ.கா., `1.6`, `2.3`) அல்லது `auto` (கோப்பிலிருந்து கண்டறியவும்) |

## வெளியீடுகள்

| வெளியீடு | விளக்கம் |
|--------|-------------|
| `valid` | SBOM திட்டவரைவுச் சரிபார்ப்பில் தேர்ச்சி பெற்றால் `true`, இல்லையெனில் `false` |
| `format` | கண்டறியப்பட்ட வடிவம்: `cyclonedx` அல்லது `spdx` |
| `spec-version` | கண்டறியப்பட்ட விவரக்குறிப்புப் பதிப்பு (எ.கா., `1.6`, `2.3`) |
| `error-count` | சரிபார்ப்புப் பிழைகளின் தோராயமான எண்ணிக்கை (செல்லுபடியாகும்போது 0) |

## ஆதரிக்கப்படும் வடிவங்கள்

| வடிவம் | பதிப்புகள் |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON மட்டும். XML SBOM-கள் ஆதரிக்கப்படவில்லை.

## தோல்வி நிலைகள்

பின்வரும் சந்தர்ப்பங்களில் இந்தச் செயல் குறியீடு 1 உடன் வெளியேறி `valid=false` என அமைக்கிறது:

| நிபந்தனை | பிழைச் செய்தி |
|-----------|---------------|
| கோப்பு இல்லை | `Input file not found: <path>` |
| கோப்பு செல்லுபடியாகும் JSON அல்ல | `Input file is not valid JSON: <path>` |
| வடிவத்தைக் கண்டறிய முடியவில்லை | `Unable to detect SBOM format` |
| பதிப்பைக் கண்டறிய முடியவில்லை | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| கண்டறியப்பட்ட பதிப்பிற்கான திட்டவரைவு இல்லை | `Schema file not found for <format> <version>` |
| திட்டவரைவுச் சரிபார்ப்பு தோல்வியடைந்தது | விவரங்களுடன் கூடிய ajv-cli பிழை வெளியீடு |

அனைத்து தோல்விப் பாதைகளும் வெளியேறுவதற்கு முன்பு வெளியீடுகளை (`valid=false`, `error-count=1`) எழுதுகின்றன; இதனால் `continue-on-error: true` உடன் தோல்வியடைந்தாலும் அடுத்தடுத்த படிகள் அவற்றைப் படிக்க முடியும்.

## எடுத்துக்காட்டுகள்

### வெளிப்படையான வடிவம் மற்றும் பதிப்பு

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### வெளியீடுகளைப் படித்தல்

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

### பல கோப்புகளைச் சரிபார்த்தல்

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

### PR நுழைவாயில் கட்டுப்பாடு

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

## பாதுகாப்பு மாதிரி

- **சரிபார்ப்பு நேரத்தில் பிணைய அழைப்புகள் இல்லை.** திட்டவரைவுகள் களஞ்சியத்திலேயே உள்ளடக்கப்பட்டுள்ளன (vendored). அமைப்பின்போது செய்யப்படும் `npm install ajv-cli ajv-formats` மட்டுமே ஒரே பிணைய அழைப்பாகும்.
- **தொலை அளவீடு (telemetry) இல்லை.** இந்தச் செயல் எந்தத் தகவலையும் வெளிப்புறத்திற்கு அனுப்புவதில்லை அல்லது தரவைச் சேகரிப்பதில்லை.
- **பணிக் கொள்கலனில் இயங்குகிறது.** Docker பதிவிறக்கமோ வெளிப்புறச் சேவைகளோ இல்லை.
- **குறைந்தபட்ச அனுமதி.** `contents: read` மட்டுமே தேவை.

கூடுதல் நம்பகத்தன்மைக்கு, முழு commit SHA-உடன் பொருத்தவும்:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## இணக்கத்தன்மை

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04` ஆகியவற்றில் இயங்கும்.
- Node.js தேவை (அனைத்து GitHub-ஹோஸ்ட் செய்யப்பட்ட இயக்கிகளிலும் முன்பே நிறுவப்பட்டுள்ளது).
- `jq` தேவை (அனைத்து GitHub-ஹோஸ்ட் செய்யப்பட்ட இயக்கிகளிலும் முன்பே நிறுவப்பட்டுள்ளது).
- சுயமாக ஹோஸ்ட் செய்யப்பட்ட இயக்கிகளுக்கு PATH-இல் Node.js >= 18 மற்றும் jq தேவை.

## திட்டவரைவுப் புதுப்பிப்புகள்

மேல்நிலையிலிருந்து உள்ளடக்கப்பட்ட திட்டவரைவுகளைப் புதுப்பிக்க:

```bash
./scripts/update-schemas.sh
```

## உரிமம்

Apache-2.0 -- [LICENSE](../../../LICENSE)-ஐப் பார்க்கவும்.
