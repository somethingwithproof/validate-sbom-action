<!-- translations:start -->
**Languages:** [English](../../../README.md) · **मराठी** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · **मराठी** · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

अधिकृत CycloneDX आणि SPDX JSON स्कीमांनुसार SBOM फाइल्सची वैधता तपासा. ऑफलाइन. पडताळणीच्या वेळी कोणतेही नेटवर्क कॉल्स नाहीत.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## वापर

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

ही अ‍ॅक्शन फाइलमधून फॉरमॅट (CycloneDX किंवा SPDX) आणि स्पेक आवृत्ती आपोआप ओळखते. पडताळणी अयशस्वी झाल्यास ती शून्येतर (non-zero) एक्झिट कोडसह बाहेर पडते.

## इनपुट्स

| इनपुट | आवश्यक | डीफॉल्ट | वर्णन |
|-------|----------|---------|-------------|
| `input-file` | होय | -- | SBOM JSON फाइलचा मार्ग |
| `format` | नाही | `auto` | `cyclonedx`, `spdx`, किंवा `auto` (फाइलमधून ओळखा) |
| `version` | नाही | `auto` | स्पेक आवृत्ती (उदा. `1.6`, `2.3`) किंवा `auto` (फाइलमधून ओळखा) |

## आउटपुट्स

| आउटपुट | वर्णन |
|--------|-------------|
| `valid` | SBOM स्कीमा पडताळणीत उत्तीर्ण झाल्यास `true`, अन्यथा `false` |
| `format` | ओळखलेला फॉरमॅट: `cyclonedx` किंवा `spdx` |
| `spec-version` | ओळखलेली स्पेक आवृत्ती (उदा. `1.6`, `2.3`) |
| `error-count` | पडताळणी त्रुटींची अंदाजे संख्या (वैध असल्यास 0) |

## समर्थित फॉरमॅट्स

| फॉरमॅट | आवृत्त्या |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

फक्त JSON. XML SBOMs समर्थित नाहीत.

## अयशस्वी होण्याचे प्रकार

पुढील प्रकरणांमध्ये अ‍ॅक्शन कोड 1 सह बाहेर पडते आणि `valid=false` सेट करते:

| स्थिती | त्रुटी संदेश |
|-----------|---------------|
| फाइल अस्तित्वात नाही | `Input file not found: <path>` |
| फाइल वैध JSON नाही | `Input file is not valid JSON: <path>` |
| फॉरमॅट ओळखता येत नाही | `Unable to detect SBOM format` |
| आवृत्ती ओळखता येत नाही | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| ओळखलेल्या आवृत्तीसाठी स्कीमा नाही | `Schema file not found for <format> <version>` |
| स्कीमा पडताळणी अयशस्वी होते | तपशीलांसह ajv-cli त्रुटी आउटपुट |

सर्व अयशस्वी मार्ग बाहेर पडण्यापूर्वी आउटपुट्स (`valid=false`, `error-count=1`) लिहितात, ज्यामुळे पुढील टप्पे `continue-on-error: true` सह अयशस्वी झाल्यानंतरही ते वाचू शकतात.

## उदाहरणे

### स्पष्ट फॉरमॅट आणि आवृत्ती

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### आउटपुट्स वाचा

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

### अनेक फाइल्सची पडताळणी करा

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

### PR गेटिंग

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

## सुरक्षा मॉडेल

- **पडताळणीच्या वेळी कोणतेही नेटवर्क कॉल्स नाहीत.** स्कीमा रिपॉझिटरीमध्येच समाविष्ट (vendored) केलेले आहेत. एकमेव नेटवर्क कॉल सेटअप दरम्यान `npm install ajv-cli ajv-formats` हा आहे.
- **टेलिमेट्री नाही.** ही अ‍ॅक्शन बाहेर माहिती पाठवत नाही किंवा डेटा संकलित करत नाही.
- **जॉब कंटेनरमध्ये चालते.** कोणतेही Docker pull नाही, कोणतीही बाह्य सर्व्हिस नाही.
- **किमान अधिकार.** फक्त `contents: read` आवश्यक आहे.

अधिक सुरक्षिततेसाठी, पूर्ण कमिट SHA वर पिन करा:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## सुसंगतता

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04` वर चालते.
- Node.js आवश्यक आहे (सर्व GitHub-होस्टेड रनर्सवर आधीच इन्स्टॉल केलेले असते).
- `jq` आवश्यक आहे (सर्व GitHub-होस्टेड रनर्सवर आधीच इन्स्टॉल केलेले असते).
- सेल्फ-होस्टेड रनर्ससाठी Node.js >= 18 आणि PATH मध्ये jq आवश्यक आहे.

## स्कीमा अपडेट्स

अपस्ट्रीमवरून समाविष्ट स्कीमा रिफ्रेश करण्यासाठी:

```bash
./scripts/update-schemas.sh
```

## परवाना

Apache-2.0 -- [LICENSE](../../../LICENSE) पहा.
