<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · **العربية** · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · **العربية** · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

التحقق من ملفات SBOM وفق مخططات JSON الرسمية لكل من CycloneDX وSPDX. دون اتصال بالشبكة، ومن دون أي استدعاءات شبكية وقت التحقق.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## الاستخدام

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

يكتشف الإجراء تلقائياً الصيغة (CycloneDX أو SPDX) وإصدار المواصفة من الملف، ويخرج برمز غير صفري في حال فشل التحقق.

## المدخلات

| المدخل | مطلوب | القيمة الافتراضية | الوصف |
|-------|----------|---------|-------------|
| `input-file` | نعم | -- | مسار ملف SBOM بصيغة JSON |
| `format` | لا | `auto` | `cyclonedx` أو `spdx` أو `auto` (الاكتشاف من الملف) |
| `version` | لا | `auto` | إصدار المواصفة (مثل `1.6` أو `2.3`) أو `auto` (الاكتشاف من الملف) |

## المخرجات

| المخرج | الوصف |
|--------|-------------|
| `valid` | `true` إذا اجتاز ملف SBOM التحقق من المخطط، و`false` خلاف ذلك |
| `format` | الصيغة المكتشفة: `cyclonedx` أو `spdx` |
| `spec-version` | إصدار المواصفة المكتشف (مثل `1.6` أو `2.3`) |
| `error-count` | العدد التقريبي لأخطاء التحقق (0 عندما يكون الملف صالحاً) |

## الصيغ المدعومة

| الصيغة | الإصدارات |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

صيغة JSON فقط. ملفات SBOM بصيغة XML غير مدعومة.

## حالات الفشل

يخرج الإجراء برمز 1 ويضبط `valid=false` في الحالات التالية:

| الحالة | رسالة الخطأ |
|-----------|---------------|
| الملف غير موجود | `Input file not found: <path>` |
| الملف ليس JSON صالحاً | `Input file is not valid JSON: <path>` |
| تعذّر اكتشاف الصيغة | `Unable to detect SBOM format` |
| تعذّر اكتشاف الإصدار | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| لا يوجد مخطط للإصدار المكتشف | `Schema file not found for <format> <version>` |
| فشل التحقق من المخطط | مخرجات أخطاء ajv-cli مع التفاصيل |

تكتب جميع مسارات الفشل المخرجات (`valid=false` و`error-count=1`) قبل الخروج، حتى تتمكن الخطوات اللاحقة من قراءتها حتى عند الفشل مع تفعيل `continue-on-error: true`.

## أمثلة

### صيغة وإصدار صريحان

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### قراءة المخرجات

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
  - uses: somethingwithproof/validate-sbom-action@v1
    with:
      input-file: ${{ matrix.sbom.path }}
      format: ${{ matrix.sbom.format }}
```

### التحقق في طلبات الدمج (PR)

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

## نموذج الأمان

- **دون استدعاءات شبكية وقت التحقق.** المخططات مدمجة داخل المستودع. الاستدعاء الشبكي الوحيد هو `npm install ajv-cli ajv-formats` أثناء الإعداد.
- **دون تتبّع أو قياس عن بُعد (telemetry).** لا يتصل الإجراء بأي خادم خارجي ولا يجمع بيانات.
- **يعمل داخل حاوية المهمة.** دون سحب صور Docker أو الاعتماد على خدمات خارجية.
- **أقل قدر من الصلاحيات.** يتطلب فقط `contents: read`.

لضمان أعلى، ثبّت الإصدار على معرّف SHA كامل للإيداع:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## التوافق

- يعمل على `ubuntu-latest` و`ubuntu-22.04` و`ubuntu-24.04`.
- يتطلب Node.js (مثبّت مسبقاً على جميع مشغّلات GitHub المستضافة).
- يتطلب `jq` (مثبّت مسبقاً على جميع مشغّلات GitHub المستضافة).
- تحتاج المشغّلات ذاتية الاستضافة إلى Node.js >= 18 وتوفّر jq ضمن PATH.

## تحديثات المخططات

لتحديث المخططات المدمجة من المصدر الأصلي:

```bash
./scripts/update-schemas.sh
```

## الترخيص

Apache-2.0 -- راجع [LICENSE](../../../LICENSE).
