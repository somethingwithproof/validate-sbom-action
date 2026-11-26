<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Soomaali** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · **Soomaali** · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Ku xaqiiji faylasha SBOM shaxda (JSON schemas) rasmiga ah ee CycloneDX iyo SPDX. Offline. Wax wicitaan shabakadeed ah ma jiro wakhtiga xaqiijinta.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Isticmaalka

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Tallaabadu waxay si toos ah uga ogaataa qaabka (CycloneDX ama SPDX) iyo nooca qeexidda faylka gudihiisa. Waxay ku baxdaa koodh aan eber ahayn haddii xaqiijintu fashilanto.

## Gelinta

| Gelinta | Waajib | Qiimaha caadiga ah | Sharaxaad |
|-------|----------|---------|-------------|
| `input-file` | haa | -- | Marinka faylka SBOM JSON |
| `format` | maya | `auto` | `cyclonedx`, `spdx`, ama `auto` (ka ogoow faylka) |
| `version` | maya | `auto` | Nooca qeexidda (tusaale, `1.6`, `2.3`) ama `auto` (ka ogoow faylka) |

## Natiijooyinka

| Natiijada | Sharaxaad |
|--------|-------------|
| `valid` | `true` haddii SBOM ku guulaysto xaqiijinta shaxda, `false` haddii kale |
| `format` | Qaabka la ogaaday: `cyclonedx` ama `spdx` |
| `spec-version` | Nooca qeexidda ee la ogaaday (tusaale, `1.6`, `2.3`) |
| `error-count` | Tirada qiyaasta ah ee khaladaadka xaqiijinta (0 marka uu sax yahay) |

## Qaababka La Taageero

| Qaabka | Noocyada |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON kaliya. XML SBOM-yada lama taageero.

## Hababka Fashilka

Tallaabadu waxay ku baxdaa koodhka 1 waxayna dejisaa `valid=false` xaaladahan:

| Xaaladda | Farriinta khaladka |
|-----------|---------------|
| Faylku ma jiro | `Input file not found: <path>` |
| Faylku ma aha JSON sax ah | `Input file is not valid JSON: <path>` |
| Qaabka lama ogaan karo | `Unable to detect SBOM format` |
| Nooca lama ogaan karo | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Ma jiro shax u dhigma nooca la ogaaday | `Schema file not found for <format> <version>` |
| Xaqiijinta shaxdu way fashilantay | Natiijada khaladka ee ajv-cli oo faahfaahsan |

Dhammaan marinnada fashilku waxay qoraan natiijooyinka (`valid=false`, `error-count=1`) ka hor inta aanay bixin, si tallaabooyinka dambe u akhriyi karaan xitaa marka fashil dhaco iyadoo la isticmaalayo `continue-on-error: true`.

## Tusaalooyinka

### Qaab iyo nooc cad

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Akhrinta natiijooyinka

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

### Xaqiijinta faylal badan

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

### Xakamaynta PR (PR gating)

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

## Qaabka Amniga

- **Wax wicitaan shabakadeed ah ma jiro wakhtiga xaqiijinta.** Shaxaha waxaa lagu dhex keydiyay kaydka. Wicitaanka shabakadeed ee kaliya waa `npm install ajv-cli ajv-formats` inta lagu jiro dejinta.
- **Ma jiro telemetry.** Tallaabadu dib uma dirto xog mana ururiso macluumaad.
- **Waxay ka dhex shaqaysaa koonteenarka shaqada.** Ma jiro soo-jiid Docker ah, mana jiraan adeegyo dibadda ah.
- **Mudnaanta ugu yar.** Waxay u baahan tahay kaliya `contents: read`.

Si aad u hesho hubanti sare, ku xidh SHA-ga commit-ka oo dhammaystiran:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Iswaafaqsanaanta

- Waxay ku shaqaysaa `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Waxay u baahan tahay Node.js (horay ugu rakiban dhammaan runner-rada GitHub martigeliyo).
- Waxay u baahan tahay `jq` (horay ugu rakiban dhammaan runner-rada GitHub martigeliyo).
- Runner-rada is-martigeliya (self-hosted) waxay u baahan yihiin Node.js >= 18 iyo jq oo ku jira PATH.

## Cusboonaysiinta Shaxda

Si aad dib ugu cusboonaysiiso shaxaha kaydka ku jira ee laga keenay isha sare:

```bash
./scripts/update-schemas.sh
```

## Shatiga

Apache-2.0 -- eeg [LICENSE](../../../LICENSE).
