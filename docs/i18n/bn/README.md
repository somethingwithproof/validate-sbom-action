<!-- translations:start -->
**Languages:** [English](../../../README.md) · **বাংলা** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** **বাংলা** · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

অফিশিয়াল CycloneDX এবং SPDX JSON স্কিমার বিপরীতে SBOM ফাইল যাচাই করুন। অফলাইন। যাচাইকরণের সময় কোনো নেটওয়ার্ক কল হয় না।

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## ব্যবহার

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

অ্যাকশনটি ফাইল থেকে স্বয়ংক্রিয়ভাবে ফরম্যাট (CycloneDX বা SPDX) এবং স্পেক সংস্করণ শনাক্ত করে। যাচাইকরণ ব্যর্থ হলে এটি নন-জিরো কোডসহ প্রস্থান করে।

## ইনপুটসমূহ

| ইনপুট | বাধ্যতামূলক | ডিফল্ট | বিবরণ |
|-------|----------|---------|-------------|
| `input-file` | হ্যাঁ | -- | SBOM JSON ফাইলের পথ |
| `format` | না | `auto` | `cyclonedx`, `spdx`, অথবা `auto` (ফাইল থেকে শনাক্ত) |
| `version` | না | `auto` | স্পেক সংস্করণ (যেমন, `1.6`, `2.3`) অথবা `auto` (ফাইল থেকে শনাক্ত) |

## আউটপুটসমূহ

| আউটপুট | বিবরণ |
|--------|-------------|
| `valid` | SBOM স্কিমা যাচাইকরণে উত্তীর্ণ হলে `true`, অন্যথায় `false` |
| `format` | শনাক্তকৃত ফরম্যাট: `cyclonedx` বা `spdx` |
| `spec-version` | শনাক্তকৃত স্পেক সংস্করণ (যেমন, `1.6`, `2.3`) |
| `error-count` | যাচাইকরণ ত্রুটির আনুমানিক সংখ্যা (বৈধ হলে 0) |

## সমর্থিত ফরম্যাটসমূহ

| ফরম্যাট | সংস্করণসমূহ |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

শুধুমাত্র JSON। XML SBOM সমর্থিত নয়।

## ব্যর্থতার ধরনসমূহ

নিম্নলিখিত ক্ষেত্রগুলোতে অ্যাকশনটি কোড 1 সহ প্রস্থান করে এবং `valid=false` সেট করে:

| শর্ত | ত্রুটি বার্তা |
|-----------|---------------|
| ফাইল বিদ্যমান নেই | `Input file not found: <path>` |
| ফাইলটি বৈধ JSON নয় | `Input file is not valid JSON: <path>` |
| ফরম্যাট শনাক্ত করা যায়নি | `Unable to detect SBOM format` |
| সংস্করণ শনাক্ত করা যায়নি | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| শনাক্তকৃত সংস্করণের জন্য কোনো স্কিমা নেই | `Schema file not found for <format> <version>` |
| স্কিমা যাচাইকরণ ব্যর্থ | বিস্তারিতসহ ajv-cli ত্রুটি আউটপুট |

সব ব্যর্থতার পথ প্রস্থান করার আগে আউটপুট (`valid=false`, `error-count=1`) লেখে, যাতে `continue-on-error: true` থাকলে ব্যর্থতার ক্ষেত্রেও পরবর্তী ধাপগুলো সেগুলো পড়তে পারে।

## উদাহরণসমূহ

### সুস্পষ্ট ফরম্যাট এবং সংস্করণ

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### আউটপুট পড়া

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

### একাধিক ফাইল যাচাই করা

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

### PR গেটিং

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

## নিরাপত্তা মডেল

- **যাচাইকরণের সময় কোনো নেটওয়ার্ক কল নেই।** স্কিমাগুলো রিপোজিটরিতে ভেন্ডর করা আছে। একমাত্র নেটওয়ার্ক কল হলো সেটআপের সময় `npm install ajv-cli ajv-formats`।
- **কোনো টেলিমেট্রি নেই।** অ্যাকশনটি বাইরে কোনো যোগাযোগ করে না বা ডেটা সংগ্রহ করে না।
- **জব কন্টেইনারে চলে।** কোনো Docker পুল বা বাহ্যিক সার্ভিস নেই।
- **ন্যূনতম অধিকার।** শুধুমাত্র `contents: read` প্রয়োজন।

অধিকতর নিশ্চয়তার জন্য একটি সম্পূর্ণ কমিট SHA-তে পিন করুন:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## সামঞ্জস্যতা

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`-এ চলে।
- Node.js প্রয়োজন (সকল GitHub-হোস্টেড রানারে আগে থেকেই ইনস্টল করা থাকে)।
- `jq` প্রয়োজন (সকল GitHub-হোস্টেড রানারে আগে থেকেই ইনস্টল করা থাকে)।
- সেলফ-হোস্টেড রানারে PATH-এ Node.js >= 18 এবং jq থাকা প্রয়োজন।

## স্কিমা আপডেট

আপস্ট্রিম থেকে ভেন্ডর করা স্কিমাগুলো রিফ্রেশ করতে:

```bash
./scripts/update-schemas.sh
```

## লাইসেন্স

Apache-2.0 -- [LICENSE](../../../LICENSE) দেখুন।
