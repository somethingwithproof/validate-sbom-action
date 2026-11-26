<!-- translations:start -->
**Languages:** [English](../../../README.md) · **isiXhosa** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · **isiXhosa** · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Qinisekisa iifayile ze-SBOM ngokuchasene neeschema ze-JSON ezisemthethweni ze-CycloneDX ne-SPDX. Ngaphandle kweintanethi. Akukho zicelo zenethiwekhi ngexesha loqinisekiso.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Ukusetyenziswa

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Esi senzo sibhaqa ngokuzenzekelayo ifomathi (i-CycloneDX okanye i-SPDX) kunye nenguqulelo yenkcazo ukusuka kwifayile. Siphuma ngekhowudi engeyiyo u-zero ukuba uqinisekiso luyasilela.

## Igalelo

| Igalelo | Kuyimfuneko | Isisiseko | Inkcazo |
|-------|----------|---------|-------------|
| `input-file` | ewe | -- | Indlela eya kwifayile ye-SBOM JSON |
| `format` | hayi | `auto` | `cyclonedx`, `spdx`, okanye `auto` (bhaqa kwifayile) |
| `version` | hayi | `auto` | Inguqulelo yenkcazo (umz., `1.6`, `2.3`) okanye `auto` (bhaqa kwifayile) |

## Iziphumo

| Isiphumo | Inkcazo |
|--------|-------------|
| `valid` | `true` ukuba i-SBOM iyaphumelela uqinisekiso lweschema, `false` kungenjalo |
| `format` | Ifomathi ebhaqiweyo: `cyclonedx` okanye `spdx` |
| `spec-version` | Inguqulelo yenkcazo ebhaqiweyo (umz., `1.6`, `2.3`) |
| `error-count` | Inani eliqikelelwayo leempazamo zoqinisekiso (0 xa isemthethweni) |

## Iifomathi ezixhaswayo

| Ifomathi | Iinguqulelo |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

I-JSON kuphela. Ii-SBOM ze-XML azixhaswa.

## Iimeko zokusilela

Esi senzo siphuma ngekhowudi 1 kwaye simisela `valid=false` kwezi meko:

| Imeko | Umyalezo wempazamo |
|-----------|---------------|
| Ifayile ayikho | `Input file not found: <path>` |
| Ifayile ayisiyo i-JSON esebenzayo | `Input file is not valid JSON: <path>` |
| Ifomathi ayikwazi ukubhaqwa | `Unable to detect SBOM format` |
| Inguqulelo ayikwazi ukubhaqwa | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Akukho schema yenguqulelo ebhaqiweyo | `Schema file not found for <format> <version>` |
| Uqinisekiso lweschema luyasilela | Isiphumo sempazamo se-ajv-cli esineenkcukacha |

Zonke iindlela zokusilela zibhala iziphumo (`valid=false`, `error-count=1`) phambi kokuphuma, ukuze amanyathelo alandelayo akwazi ukuzifunda nangona kusilele nge-`continue-on-error: true`.

## Imizekelo

### Ifomathi nenguqulelo ecacileyo

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Funda iziphumo

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

### Qinisekisa iifayile ezininzi

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

### Ukulawula ii-PR

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

## Imodeli yokhuseleko

- **Akukho zicelo zenethiwekhi ngexesha loqinisekiso.** Iischema zigcinwe kwi-repository. Isicelo senethiwekhi kuphela yi-`npm install ajv-cli ajv-formats` ngexesha loseto.
- **Akukho telemetry.** Esi senzo asinxibelelani neeseva zangaphandle okanye siqokelele idatha.
- **Siqhutywa kwisikhongozeli somsebenzi.** Akukho kutsala kwe-Docker, akukho nkonzo zangaphandle.
- **Ilungelo elincinci.** Sifuna kuphela i-`contents: read`.

Ngokuqiniseka okuphezulu, qinisa kwi-SHA epheleleyo ye-commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Ukuhambelana

- Siqhutywa kwi-`ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Sifuna i-Node.js (ifakwe kwangaphambili kubo bonke abaqhubi abasingathwe yi-GitHub).
- Sifuna i-`jq` (ifakwe kwangaphambili kubo bonke abaqhubi abasingathwe yi-GitHub).
- Abaqhubi abazisingathileyo bafuna i-Node.js >= 18 kunye ne-jq kwi-PATH.

## Uhlaziyo lweSchema

Ukuhlaziya iischema ezigcinwe kwi-repository ukusuka kumthombo oyintloko:

```bash
./scripts/update-schemas.sh
```

## Ilayisenisi

Apache-2.0 -- jonga i-[LICENSE](../../../LICENSE).
