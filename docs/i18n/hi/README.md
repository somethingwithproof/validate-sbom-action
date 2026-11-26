<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · **हिन्दी**

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · **हिन्दी** · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

आधिकारिक CycloneDX और SPDX JSON स्कीमा के विरुद्ध SBOM फ़ाइलों को सत्यापित करें। ऑफ़लाइन। सत्यापन के समय कोई नेटवर्क कॉल नहीं।

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## उपयोग

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

यह एक्शन फ़ाइल से प्रारूप (CycloneDX या SPDX) और स्पेक संस्करण का स्वतः पता लगाता है। सत्यापन विफल होने पर यह नॉन-ज़ीरो कोड के साथ बाहर निकलता है।

## इनपुट

| इनपुट | आवश्यक | डिफ़ॉल्ट | विवरण |
|-------|----------|---------|-------------|
| `input-file` | हाँ | -- | SBOM JSON फ़ाइल का पाथ |
| `format` | नहीं | `auto` | `cyclonedx`, `spdx`, या `auto` (फ़ाइल से पता लगाएँ) |
| `version` | नहीं | `auto` | स्पेक संस्करण (जैसे, `1.6`, `2.3`) या `auto` (फ़ाइल से पता लगाएँ) |

## आउटपुट

| आउटपुट | विवरण |
|--------|-------------|
| `valid` | यदि SBOM स्कीमा सत्यापन में उत्तीर्ण होता है तो `true`, अन्यथा `false` |
| `format` | पहचाना गया प्रारूप: `cyclonedx` या `spdx` |
| `spec-version` | पहचाना गया स्पेक संस्करण (जैसे, `1.6`, `2.3`) |
| `error-count` | सत्यापन त्रुटियों की अनुमानित संख्या (वैध होने पर 0) |

## समर्थित प्रारूप

| प्रारूप | संस्करण |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

केवल JSON। XML SBOM समर्थित नहीं हैं।

## विफलता स्थितियाँ

इन स्थितियों में यह एक्शन कोड 1 के साथ बाहर निकलता है और `valid=false` सेट करता है:

| स्थिति | त्रुटि संदेश |
|-----------|---------------|
| फ़ाइल मौजूद नहीं है | `Input file not found: <path>` |
| फ़ाइल वैध JSON नहीं है | `Input file is not valid JSON: <path>` |
| प्रारूप का पता नहीं लगाया जा सकता | `Unable to detect SBOM format` |
| संस्करण का पता नहीं लगाया जा सकता | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| पहचाने गए संस्करण के लिए कोई स्कीमा नहीं है | `Schema file not found for <format> <version>` |
| स्कीमा सत्यापन विफल हो जाता है | विवरण सहित ajv-cli त्रुटि आउटपुट |

सभी विफलता मार्ग बाहर निकलने से पहले आउटपुट (`valid=false`, `error-count=1`) लिखते हैं, जिससे `continue-on-error: true` के साथ विफलता होने पर भी डाउनस्ट्रीम चरण उन्हें पढ़ सकते हैं।

## उदाहरण

### स्पष्ट प्रारूप और संस्करण

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### आउटपुट पढ़ना

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

### एकाधिक फ़ाइलों को सत्यापित करना

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

## सुरक्षा मॉडल

- **सत्यापन के समय कोई नेटवर्क कॉल नहीं।** स्कीमा रिपॉजिटरी में ही वेंडर किए गए हैं। एकमात्र नेटवर्क कॉल सेटअप के दौरान `npm install ajv-cli ajv-formats` है।
- **कोई टेलीमेट्री नहीं।** यह एक्शन कोई बाहरी संपर्क नहीं करता और न ही डेटा एकत्र करता है।
- **जॉब कंटेनर में चलता है।** कोई Docker पुल नहीं, कोई बाहरी सेवाएँ नहीं।
- **न्यूनतम विशेषाधिकार।** केवल `contents: read` की आवश्यकता है।

अधिक सुरक्षा सुनिश्चित करने के लिए, पूर्ण कमिट SHA पर पिन करें:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## संगतता

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04` पर चलता है।
- Node.js आवश्यक है (सभी GitHub-होस्टेड रनर पर पहले से इंस्टॉल)।
- `jq` आवश्यक है (सभी GitHub-होस्टेड रनर पर पहले से इंस्टॉल)।
- सेल्फ़-होस्टेड रनर को Node.js >= 18 और PATH में jq की आवश्यकता होती है।

## स्कीमा अपडेट

अपस्ट्रीम से वेंडर किए गए स्कीमा को रीफ़्रेश करने के लिए:

```bash
./scripts/update-schemas.sh
```

## लाइसेंस

Apache-2.0 -- [LICENSE](../../../LICENSE) देखें।
