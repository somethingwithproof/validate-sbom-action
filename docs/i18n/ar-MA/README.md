<!-- translations:start -->
**Languages:** [English](../../../README.md) · **العربية (المغرب)** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · **العربية (المغرب)** · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

تحقق من ملفات SBOM مقابل مخططات JSON الرسمية ديال CycloneDX وSPDX. بلا أنترنت. بلا أي اتصالات بالشبكة وقت التحقق.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## الاستعمال

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

هاد الإجراء (action) كيكتشف تلقائياً الصيغة (CycloneDX ولا SPDX) وإصدار المواصفات من الملف. كيخرج برمز غير صفري إلى فشل التحقق.

## المدخلات

| المدخل | إجباري | الافتراضي | الوصف |
|-------|----------|---------|-------------|
| `input-file` | نعم | -- | المسار ديال ملف SBOM بصيغة JSON |
| `format` | لا | `auto` | `cyclonedx`، أو `spdx`، أو `auto` (اكتشاف تلقائي من الملف) |
| `version` | لا | `auto` | إصدار المواصفات (مثلاً، `1.6`، `2.3`) ولا `auto` (اكتشاف تلقائي من الملف) |

## المخرجات

| المخرج | الوصف |
|--------|-------------|
| `valid` | `true` إلى داز الـ SBOM التحقق ديال المخطط بنجاح، و`false` فالحالة الأخرى |
| `format` | الصيغة المكتشفة: `cyclonedx` ولا `spdx` |
| `spec-version` | إصدار المواصفات المكتشف (مثلاً، `1.6`، `2.3`) |
| `error-count` | العدد التقريبي ديال أخطاء التحقق (0 ملي يكون صالح) |

## الصيغ المدعومة

| الصيغة | الإصدارات |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON بوحدو. ملفات XML SBOM ما مدعوماش.

## حالات الفشل

الإجراء كيخرج بالرمز 1 وكيضبط `valid=false` فهاد الحالات:

| الحالة | رسالة الخطأ |
|-----------|---------------|
| الملف ما كاينش | `Input file not found: <path>` |
| الملف ماشي JSON صالح | `Input file is not valid JSON: <path>` |
| ما قدرش يكتشف الصيغة | `Unable to detect SBOM format` |
| ما قدرش يكتشف الإصدار | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| ما كاين حتى مخطط للإصدار المكتشف | `Schema file not found for <format> <version>` |
| فشل التحقق من المخطط | مخرجات خطأ ajv-cli مع التفاصيل |

جميع مسارات الفشل كيكتبو المخرجات (`valid=false`، `error-count=1`) قبل الخروج، باش الخطوات اللي جاية من بعد تقدر تقراهم حتى فحالة الفشل مع `continue-on-error: true`.

## أمثلة

### تحديد الصيغة والإصدار بشكل صريح

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### قراءة المخرجات

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

### التحقق من عدة ملفات

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

### تصفية طلبات الدمج (PR gating)

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

## نموذج الأمان

- **بلا اتصالات بالشبكة وقت التحقق.** المخططات مدمجة (vendored) داخل المستودع. الاتصال الوحيد بالشبكة هو `npm install ajv-cli ajv-formats` أثناء الإعداد.
- **بلا تتبع (telemetry).** الإجراء ما كيصيفط حتى بيانات للخارج وما كيجمع حتى معلومات.
- **كيخدم داخل حاوية المهمة.** بلا تحميل Docker، بلا خدمات خارجية.
- **أقل صلاحيات ممكنة.** كيحتاج غير `contents: read`.

باش تكون عندك ضمانة أكبر، ثبت النسخة على commit SHA كامل:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## التوافق

- كيخدم على `ubuntu-latest`، و`ubuntu-22.04`، و`ubuntu-24.04`.
- كيحتاج Node.js (مثبت مسبقاً على جميع المشغلات المستضافة من GitHub).
- كيحتاج `jq` (مثبت مسبقاً على جميع المشغلات المستضافة من GitHub).
- المشغلات المستضافة ذاتياً (self-hosted runners) خاصهم Node.js >= 18 وjq فـ PATH.

## تحديثات المخططات

باش تحدث المخططات المدمجة من المصدر الأصلي (upstream):

```bash
./scripts/update-schemas.sh
```

## الرخصة

Apache-2.0 -- شوف [LICENSE](../../../LICENSE).
