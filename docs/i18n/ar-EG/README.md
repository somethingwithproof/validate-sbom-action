<!-- translations:start -->
**Languages:** [English](../../../README.md) · **العربية (مصر)** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · **العربية (مصر)** · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

تحقق من صحة ملفات SBOM مقابل مخططات (JSON schemas) الرسمية لـ CycloneDX وSPDX. بيشتغل أوفلاين من غير أي اتصالات بالشبكة وقت التحقق.

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

الـ action بيكتشف الصيغة تلقائيًا (CycloneDX أو SPDX) وإصدار المواصفة من الملف، وبيخرج بكود غير صفري (non-zero) لو التحقق فشل.

## المدخلات

| المدخل | مطلوب | الافتراضي | الوصف |
|-------|----------|---------|-------------|
| `input-file` | نعم | -- | مسار ملف الـ SBOM بصيغة JSON |
| `format` | لا | `auto` | `cyclonedx` أو `spdx` أو `auto` (اكتشاف تلقائي من الملف) |
| `version` | لا | `auto` | إصدار المواصفة (مثل `1.6` أو `2.3`) أو `auto` (اكتشاف تلقائي من الملف) |

## المخرجات

| المخرج | الوصف |
|--------|-------------|
| `valid` | `true` لو ملف الـ SBOM عدّى التحقق من المخطط، و`false` لو فشل |
| `format` | الصيغة المكتشفة: `cyclonedx` أو `spdx` |
| `spec-version` | إصدار المواصفة المكتشف (مثل `1.6` أو `2.3`) |
| `error-count` | العدد التقريبي لأخطاء التحقق (0 لما يكون الملف سليم) |

## الصيغ المدعومة

| الصيغة | الإصدارات |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

صيغة JSON بس. ملفات SBOM بصيغة XML مش مدعومة.

## حالات الفشل

الـ action بيخرج بكود 1 وبيضبط `valid=false` في الحالات دي:

| الحالة | رسالة الخطأ |
|-----------|---------------|
| الملف مش موجود | `Input file not found: <path>` |
| الملف مش JSON سليم | `Input file is not valid JSON: <path>` |
| تعذّر اكتشاف الصيغة | `Unable to detect SBOM format` |
| تعذّر اكتشاف الإصدار | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| مفيش مخطط للإصدار المكتشف | `Schema file not found for <format> <version>` |
| فشل التحقق من المخطط | مخرجات أخطاء ajv-cli بالتفاصيل |

كل مسارات الفشل بتكتب المخرجات (`valid=false`، `error-count=1`) قبل الخروج، علشان الخطوات اللي بعدها تقدر تقراها حتى لو حصل فشل مع `continue-on-error: true`.

## أمثلة

### تحديد الصيغة والإصدار بشكل صريح

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

### التحقق من أكتر من ملف

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

### التحقق كبوابة لطلبات السحب (PR gating)

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

- **مفيش أي اتصالات بالشبكة وقت التحقق.** المخططات (schemas) مضمّنة جوه المستودع. الاتصال الوحيد بالشبكة هو `npm install ajv-cli ajv-formats` أثناء التجهيز.
- **مفيش أي قياس عن بُعد (telemetry).** الـ action مش بيبعت أي بيانات ولا بيجمع معلومات.
- **بيشتغل جوه حاوية المهمة نفسها.** مفيش سحب لصور Docker ولا خدمات خارجية.
- **أقل صلاحيات ممكنة.** بيحتاج `contents: read` بس.

لأمان أعلى، ثبّت الإصدار على commit SHA كامل:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## التوافق

- بيشتغل على `ubuntu-latest`، و`ubuntu-22.04`، و`ubuntu-24.04`.
- بيحتاج Node.js (متثبّت مسبقًا على كل GitHub-hosted runners).
- بيحتاج `jq` (متثبّت مسبقًا على كل GitHub-hosted runners).
- الـ self-hosted runners محتاجة Node.js >= 18 وjq في الـ PATH.

## تحديثات المخططات

علشان تحدّث المخططات المضمّنة من المصدر الأصلي:

```bash
./scripts/update-schemas.sh
```

## الرخصة

Apache-2.0 -- راجع [LICENSE](../../../LICENSE).
