<!-- translations:start -->
**Languages:** [English](../../../README.md) · **فارسی** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · **فارسی** · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

اعتبارسنجی فایل‌های SBOM در برابر اسکیماهای رسمی JSON مربوط به CycloneDX و SPDX. به‌صورت آفلاین. بدون هیچ فراخوانی شبکه‌ای در زمان اعتبارسنجی.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## نحوه استفاده

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

این اکشن به‌صورت خودکار قالب (CycloneDX یا SPDX) و نسخه مشخصات را از فایل تشخیص می‌دهد. در صورت شکست اعتبارسنجی، با کد خروجی غیرصفر خارج می‌شود.

## ورودی‌ها

| ورودی | اجباری | پیش‌فرض | توضیحات |
|-------|----------|---------|-------------|
| `input-file` | بله | -- | مسیر فایل JSON مربوط به SBOM |
| `format` | خیر | `auto` | یکی از مقادیر `cyclonedx`، `spdx` یا `auto` (تشخیص از فایل) |
| `version` | خیر | `auto` | نسخه مشخصات (برای مثال، `1.6`، `2.3`) یا `auto` (تشخیص از فایل) |

## خروجی‌ها

| خروجی | توضیحات |
|--------|-------------|
| `valid` | در صورت عبور SBOM از اعتبارسنجی اسکیما برابر `true` و در غیر این صورت `false` |
| `format` | قالب تشخیص‌داده‌شده: `cyclonedx` یا `spdx` |
| `spec-version` | نسخه مشخصات تشخیص‌داده‌شده (برای مثال، `1.6`، `2.3`) |
| `error-count` | تعداد تقریبی خطاهای اعتبارسنجی (در حالت معتبر برابر 0) |

## قالب‌های پشتیبانی‌شده

| قالب | نسخه‌ها |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

فقط JSON. فایل‌های SBOM با قالب XML پشتیبانی نمی‌شوند.

## حالت‌های شکست

این اکشن در موارد زیر با کد 1 خارج می‌شود و مقدار `valid=false` را تنظیم می‌کند:

| شرط | پیام خطا |
|-----------|---------------|
| فایل وجود ندارد | `Input file not found: <path>` |
| فایل JSON معتبر نیست | `Input file is not valid JSON: <path>` |
| قالب قابل تشخیص نیست | `Unable to detect SBOM format` |
| نسخه قابل تشخیص نیست | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| اسکیما برای نسخه تشخیص‌داده‌شده وجود ندارد | `Schema file not found for <format> <version>` |
| اعتبارسنجی اسکیما شکست می‌خورد | خروجی خطای ajv-cli همراه با جزئیات |

تمام مسیرهای شکست پیش از خروج، خروجی‌ها (`valid=false`، `error-count=1`) را می‌نویسند تا مراحل بعدی حتی در صورت شکست با گزینه `continue-on-error: true` بتوانند آن‌ها را بخوانند.

## مثال‌ها

### تعیین صریح قالب و نسخه

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### خواندن خروجی‌ها

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

### اعتبارسنجی چند فایل

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

### دروازه کنترل PR

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

## مدل امنیتی

- **بدون فراخوانی شبکه در زمان اعتبارسنجی.** اسکیماها در مخزن گنجانده (vendor) شده‌اند. تنها فراخوانی شبکه اجرای `npm install ajv-cli ajv-formats` هنگام راه‌اندازی است.
- **بدون تله‌متری.** این اکشن هیچ داده‌ای ارسال یا جمع‌آوری نمی‌کند.
- **اجرا در کانتینر کار (job).** بدون دریافت تصویر Docker و بدون سرویس‌های خارجی.
- **حداقل سطح دسترسی.** تنها به `contents: read` نیاز دارد.

برای اطمینان بیشتر، نسخه را به یک SHA کامل کامیت قفل کنید:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## سازگاری

- روی `ubuntu-latest`، `ubuntu-22.04` و `ubuntu-24.04` اجرا می‌شود.
- به Node.js نیاز دارد (به‌صورت پیش‌فرض روی همه runnerهای میزبان GitHub نصب است).
- به `jq` نیاز دارد (به‌صورت پیش‌فرض روی همه runnerهای میزبان GitHub نصب است).
- runnerهای خودمیزبان به Node.js >= 18 و وجود jq در PATH نیاز دارند.

## به‌روزرسانی اسکیماها

برای به‌روزرسانی اسکیماهای گنجانده‌شده از منبع بالادستی:

```bash
./scripts/update-schemas.sh
```

## مجوز

Apache-2.0 -- فایل [LICENSE](../../../LICENSE) را ببینید.
