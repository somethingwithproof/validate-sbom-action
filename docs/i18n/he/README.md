<!-- translations:start -->
**Languages:** [English](../../../README.md) · **עברית** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · **עברית** · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

אימות קובצי SBOM מול סכמות ה-JSON הרשמיות של CycloneDX ו-SPDX. באופן לא מקוון. ללא קריאות רשת בזמן האימות.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## שימוש

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

הפעולה מזהה אוטומטית את הפורמט (CycloneDX או SPDX) ואת גרסת המפרט מתוך הקובץ. היא מסתיימת עם קוד יציאה שונה מאפס אם האימות נכשל.

## קלטים

| קלט | חובה | ברירת מחדל | תיאור |
|-------|----------|---------|-------------|
| `input-file` | כן | -- | נתיב אל קובץ ה-JSON של ה-SBOM |
| `format` | לא | `auto` | `cyclonedx`, `spdx`, או `auto` (זיהוי מהקובץ) |
| `version` | לא | `auto` | גרסת מפרט (למשל `1.6`, `2.3`) או `auto` (זיהוי מהקובץ) |

## פלטים

| פלט | תיאור |
|--------|-------------|
| `valid` | `true` אם ה-SBOM עובר את אימות הסכמה, אחרת `false` |
| `format` | הפורמט שזוהה: `cyclonedx` או `spdx` |
| `spec-version` | גרסת המפרט שזוהתה (למשל `1.6`, `2.3`) |
| `error-count` | מספר משוער של שגיאות אימות (0 כאשר תקין) |

## פורמטים נתמכים

| פורמט | גרסאות |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON בלבד. קובצי SBOM בפורמט XML אינם נתמכים.

## מצבי כשל

הפעולה מסתיימת עם קוד 1 ומגדירה `valid=false` במקרים הבאים:

| תנאי | הודעת שגיאה |
|-----------|---------------|
| הקובץ אינו קיים | `Input file not found: <path>` |
| הקובץ אינו JSON תקין | `Input file is not valid JSON: <path>` |
| לא ניתן לזהות את הפורמט | `Unable to detect SBOM format` |
| לא ניתן לזהות את הגרסה | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| אין סכמה עבור הגרסה שזוהתה | `Schema file not found for <format> <version>` |
| אימות הסכמה נכשל | פלט השגיאה של ajv-cli עם פרטים |

כל נתיבי הכשל כותבים פלטים (`valid=false`, `error-count=1`) לפני היציאה, כך ששלבים המשכיים יכולים לקרוא אותם גם בעת כשל עם `continue-on-error: true`.

## דוגמאות

### פורמט וגרסה מפורשים

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### קריאת פלטים

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

### אימות מספר קבצים

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

### סינון בקשות משיכה (PR gating)

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

## מודל אבטחה

- **ללא קריאות רשת בזמן האימות.** הסכמות משולבות (vendored) בתוך המאגר. קריאת הרשת היחידה היא `npm install ajv-cli ajv-formats` בשלב ההכנה.
- **ללא טלמטריה.** הפעולה אינה שולחת דיווחים החוצה ואינה אוספת נתונים.
- **רצה בתוך מכולת המשימה.** ללא משיכת Docker וללא שירותים חיצוניים.
- **עקרון ההרשאה המינימלית.** דורשת רק `contents: read`.

לרמת ביטחון גבוהה יותר, נעצו ל-commit SHA מלא:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## תאימות

- רצה על `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- דורשת Node.js (מותקן מראש בכל הרצים המתארחים ב-GitHub).
- דורשת `jq` (מותקן מראש בכל הרצים המתארחים ב-GitHub).
- רצים באירוח עצמי דורשים Node.js >= 18 ו-jq ב-PATH.

## עדכוני סכמות

לרענון הסכמות המשולבות מ-upstream:

```bash
./scripts/update-schemas.sh
```

## רישיון

Apache-2.0 -- ראו [LICENSE](../../../LICENSE).
