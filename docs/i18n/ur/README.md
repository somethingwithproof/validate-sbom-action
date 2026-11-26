<!-- translations:start -->
**Languages:** [English](../../../README.md) · **اردو** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · **اردو** · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

آفیشل CycloneDX اور SPDX JSON اسکیماز کے مقابلے میں SBOM فائلوں کی توثیق کریں۔ آف لائن۔ توثیق کے وقت کوئی نیٹ ورک کال نہیں۔

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## استعمال

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

یہ ایکشن فائل سے فارمیٹ (CycloneDX یا SPDX) اور اسپیک ورژن کی خودکار شناخت کرتا ہے۔ اگر توثیق ناکام ہو جائے تو یہ غیر صفر (non-zero) کوڈ کے ساتھ باہر نکلتا ہے۔

## ان پٹس

| ان پٹ | لازمی | ڈیفالٹ | تفصیل |
|-------|----------|---------|-------------|
| `input-file` | ہاں | -- | SBOM JSON فائل کا پاتھ |
| `format` | نہیں | `auto` | `cyclonedx`، `spdx`، یا `auto` (فائل سے شناخت) |
| `version` | نہیں | `auto` | اسپیک ورژن (مثلاً، `1.6`، `2.3`) یا `auto` (فائل سے شناخت) |

## آؤٹ پٹس

| آؤٹ پٹ | تفصیل |
|--------|-------------|
| `valid` | اگر SBOM اسکیما توثیق پاس کر لے تو `true`، بصورتِ دیگر `false` |
| `format` | شناخت شدہ فارمیٹ: `cyclonedx` یا `spdx` |
| `spec-version` | شناخت شدہ اسپیک ورژن (مثلاً، `1.6`، `2.3`) |
| `error-count` | توثیقی غلطیوں کی تخمینی تعداد (درست ہونے پر 0) |

## سپورٹ شدہ فارمیٹس

| فارمیٹ | ورژنز |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

صرف JSON۔ XML SBOMs سپورٹ شدہ نہیں ہیں۔

## ناکامی کی صورتیں

یہ ایکشن درج ذیل صورتوں میں کوڈ 1 کے ساتھ باہر نکلتا ہے اور `valid=false` سیٹ کرتا ہے:

| شرط | خرابی کا پیغام |
|-----------|---------------|
| فائل موجود نہیں ہے | `Input file not found: <path>` |
| فائل درست JSON نہیں ہے | `Input file is not valid JSON: <path>` |
| فارمیٹ کی شناخت نہیں ہو سکی | `Unable to detect SBOM format` |
| ورژن کی شناخت نہیں ہو سکی | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| شناخت شدہ ورژن کے لیے کوئی اسکیما نہیں ہے | `Schema file not found for <format> <version>` |
| اسکیما توثیق ناکام ہو گئی | تفصیلات کے ساتھ ajv-cli خرابی کا آؤٹ پٹ |

## مثالیں

### واضح فارمیٹ اور ورژن

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### آؤٹ پٹس پڑھنا

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  id: sbom
  with:
    input-file: sbom.json
  continue-on-error: true

- env:
    SBOM_VALID: ${{ steps.sbom.outputs.valid }}
    SBOM_FORMAT: ${{ steps.sbom.outputs.format }}
    SBOM_SPEC_VERSION: ${{ steps.sbom.outputs.spec-version }}
    SBOM_ERROR_COUNT: ${{ steps.sbom.outputs.error-count }}
  run: |
    echo "Valid: $SBOM_VALID"
    echo "Format: $SBOM_FORMAT"
    echo "Version: $SBOM_SPEC_VERSION"
    echo "Errors: $SBOM_ERROR_COUNT"
```

### متعدد فائلوں کی توثیق کرنا

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

### PR گیٹنگ

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
        env:
          SBOM_VALID: ${{ steps.sbom.outputs.valid }}
          SBOM_FORMAT: ${{ steps.sbom.outputs.format }}
          SBOM_SPEC_VERSION: ${{ steps.sbom.outputs.spec-version }}
        run: |
          echo "### SBOM Validation" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Valid:** $SBOM_VALID" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Format:** $SBOM_FORMAT" >> "$GITHUB_STEP_SUMMARY"
          echo "- **Version:** $SBOM_SPEC_VERSION" >> "$GITHUB_STEP_SUMMARY"
```

## سیکیورٹی ماڈل

- **توثیق کے وقت کوئی نیٹ ورک کال نہیں۔** اسکیماز ریپوزیٹری میں شامل (vendored) ہیں۔ واحد نیٹ ورک کال سیٹ اپ کے دوران `npm install ajv-cli ajv-formats` ہے۔
- **کوئی ٹیلی میٹری نہیں۔** یہ ایکشن کہیں ڈیٹا نہیں بھیجتا اور نہ ہی جمع کرتا ہے۔
- **جاب کنٹینر میں چلتا ہے۔** کوئی Docker pull نہیں، کوئی بیرونی سروسز نہیں۔
- **کم از کم استحقاق (Least privilege)۔** صرف `contents: read` درکار ہے۔

زیادہ یقین دہانی کے لیے، مکمل کمٹ SHA پر پن (pin) کریں:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## مطابقت

- `ubuntu-latest`، `ubuntu-22.04`، `ubuntu-24.04` پر چلتا ہے۔
- Node.js درکار ہے (تمام GitHub ہوسٹڈ رنرز پر پہلے سے انسٹال ہوتا ہے)۔
- `jq` درکار ہے (تمام GitHub ہوسٹڈ رنرز پر پہلے سے انسٹال ہوتا ہے)۔
- سیلف ہوسٹڈ رنرز کے لیے PATH میں Node.js >= 18 اور jq درکار ہیں۔

## اسکیما اپ ڈیٹس

اپ اسٹریم سے شامل کردہ (vendored) اسکیماز کو ریفریش کرنے کے لیے:

```bash
./scripts/update-schemas.sh
```

## لائسنس

Apache-2.0 -- [LICENSE](../../../LICENSE) دیکھیں۔
