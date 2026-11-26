<!-- translations:start -->
**Languages:** [English](../../../README.md) · **ไทย** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · **ไทย** · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

ตรวจสอบความถูกต้องของไฟล์ SBOM กับ JSON schema อย่างเป็นทางการของ CycloneDX และ SPDX ทำงานแบบออฟไลน์ ไม่มีการเรียกใช้เครือข่ายในขณะตรวจสอบ

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## การใช้งาน

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

action จะตรวจจับรูปแบบ (CycloneDX หรือ SPDX) และเวอร์ชันข้อกำหนด (spec version) จากไฟล์โดยอัตโนมัติ และจะจบการทำงานด้วยรหัสสถานะที่ไม่ใช่ศูนย์หากการตรวจสอบล้มเหลว

## อินพุต

| อินพุต | จำเป็น | ค่าเริ่มต้น | คำอธิบาย |
|-------|----------|---------|-------------|
| `input-file` | ใช่ | -- | พาธไปยังไฟล์ SBOM JSON |
| `format` | ไม่ | `auto` | `cyclonedx`, `spdx` หรือ `auto` (ตรวจจับจากไฟล์) |
| `version` | ไม่ | `auto` | เวอร์ชันข้อกำหนด (เช่น `1.6`, `2.3`) หรือ `auto` (ตรวจจับจากไฟล์) |

## เอาต์พุต

| เอาต์พุต | คำอธิบาย |
|--------|-------------|
| `valid` | `true` หาก SBOM ผ่านการตรวจสอบตาม schema และ `false` ในกรณีอื่น |
| `format` | รูปแบบที่ตรวจพบ: `cyclonedx` หรือ `spdx` |
| `spec-version` | เวอร์ชันข้อกำหนดที่ตรวจพบ (เช่น `1.6`, `2.3`) |
| `error-count` | จำนวนข้อผิดพลาดจากการตรวจสอบโดยประมาณ (เป็น 0 เมื่อผ่านการตรวจสอบ) |

## รูปแบบที่รองรับ

| รูปแบบ | เวอร์ชัน |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

รองรับเฉพาะรูปแบบ JSON เท่านั้น ไม่รองรับไฟล์ SBOM แบบ XML

## กรณีความล้มเหลว

action จะจบการทำงานด้วยรหัส 1 และกำหนดค่า `valid=false` ในกรณีต่อไปนี้:

| เงื่อนไข | ข้อความแสดงข้อผิดพลาด |
|-----------|---------------|
| ไม่พบไฟล์ | `Input file not found: <path>` |
| ไฟล์ไม่ใช่ JSON ที่ถูกต้อง | `Input file is not valid JSON: <path>` |
| ไม่สามารถตรวจจับรูปแบบได้ | `Unable to detect SBOM format` |
| ไม่สามารถตรวจจับเวอร์ชันได้ | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| ไม่มี schema สำหรับเวอร์ชันที่ตรวจพบ | `Schema file not found for <format> <version>` |
| การตรวจสอบ schema ล้มเหลว | ข้อความแสดงข้อผิดพลาดจาก ajv-cli พร้อมรายละเอียด |

ทุกเส้นทางที่เกิดความล้มเหลวจะเขียนค่าเอาต์พุต (`valid=false`, `error-count=1`) ก่อนจบการทำงาน เพื่อให้ขั้นตอนถัดไปสามารถอ่านค่าได้แม้จะเกิดข้อผิดพลาดเมื่อตั้งค่า `continue-on-error: true`

## ตัวอย่าง

### การระบุรูปแบบและเวอร์ชันอย่างชัดเจน

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### การอ่านค่าเอาต์พุต

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

### การตรวจสอบหลายไฟล์

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

### การใช้เป็นเงื่อนไขตรวจสอบ PR

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

## โมเดลความปลอดภัย

- **ไม่มีการเรียกใช้เครือข่ายในขณะตรวจสอบ** ไฟล์ schema ถูกจัดเก็บรวมไว้ในรีโพซิทอรี (vendored) การเชื่อมต่อเครือข่ายเพียงอย่างเดียวคือคำสั่ง `npm install ajv-cli ajv-formats` ระหว่างขั้นตอนการติดตั้ง
- **ไม่มีการเก็บข้อมูลการใช้งาน (telemetry)** action นี้ไม่ส่งข้อมูลกลับหรือเก็บข้อมูลใด ๆ
- **ทำงานภายในคอนเทนเนอร์ของจ็อบ** ไม่มีการดึงอิมเมจ Docker และไม่พึ่งพาบริการภายนอก
- **สิทธิ์น้อยที่สุดเท่าที่จำเป็น** ต้องการเพียงสิทธิ์ `contents: read`

เพื่อความมั่นใจด้านความปลอดภัยที่สูงขึ้น ให้ปักหมุดเวอร์ชันด้วย commit SHA แบบเต็ม:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## ความเข้ากันได้

- ทำงานบน `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`
- ต้องใช้ Node.js (ติดตั้งมาล่วงหน้าบน GitHub-hosted runner ทุกเครื่อง)
- ต้องใช้ `jq` (ติดตั้งมาล่วงหน้าบน GitHub-hosted runner ทุกเครื่อง)
- สำหรับ self-hosted runner ต้องมี Node.js >= 18 และ jq อยู่ใน PATH

## การอัปเดต Schema

หากต้องการอัปเดตไฟล์ schema ที่จัดเก็บไว้จากต้นน้ำ:

```bash
./scripts/update-schemas.sh
```

## สัญญาอนุญาต

Apache-2.0 -- ดูรายละเอียดใน [LICENSE](../../../LICENSE)
