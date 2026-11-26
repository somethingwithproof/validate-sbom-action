<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Yorùbá** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · **Yorùbá** · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Jẹ́rìísí àwọn fáìlì SBOM ní ìbámu pẹ̀lú àwọn àtòjọ-ìṣètò JSON tí a fọwọ́sí fún CycloneDX àti SPDX. Láìsí íńtánẹ́ẹ̀tì. Kò sí ìpè nẹ́tíwọ́ọ̀kì nígbà ìjẹ́rìísí.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Ìlò

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Ìṣe náà máa ń ṣàwárí ọ̀nà-ìṣètò (CycloneDX tàbí SPDX) àti ẹ̀yà àlàyé-ìlànà láti inú fáìlì náà fúnra rẹ̀. Ó máa ń jáde pẹ̀lú kóòdù tí kì í ṣe òdo tí ìjẹ́rìísí bá kùnà.

## Àwọn Ìtẹ̀wọlé

| Ìtẹ̀wọlé | Pọn dandan | Àṣàyàn àkọ́kọ́ | Àpèjúwe |
|-------|----------|---------|-------------|
| `input-file` | bẹ́ẹ̀ ni | -- | Ọ̀nà sí fáìlì SBOM JSON |
| `format` | bẹ́ẹ̀ kọ́ | `auto` | `cyclonedx`, `spdx`, tàbí `auto` (ṣàwárí láti inú fáìlì) |
| `version` | bẹ́ẹ̀ kọ́ | `auto` | Ẹ̀yà àlàyé-ìlànà (fún àpẹẹrẹ, `1.6`, `2.3`) tàbí `auto` (ṣàwárí láti inú fáìlì) |

## Àwọn Èsì-ìjáde

| Èsì-ìjáde | Àpèjúwe |
|--------|-------------|
| `valid` | `true` tí SBOM bá kọjá ìjẹ́rìísí àtòjọ-ìṣètò, `false` bí bẹ́ẹ̀ kọ́ |
| `format` | Ọ̀nà-ìṣètò tí a ṣàwárí: `cyclonedx` tàbí `spdx` |
| `spec-version` | Ẹ̀yà àlàyé-ìlànà tí a ṣàwárí (fún àpẹẹrẹ, `1.6`, `2.3`) |
| `error-count` | Ìṣirò súnmọ́ iye àwọn àṣìṣe ìjẹ́rìísí (0 nígbà tí ó bá tọ́) |

## Àwọn Ọ̀nà-ìṣètò Tí A Ṣètìlẹ́yìn Fún

| Ọ̀nà-ìṣètò | Àwọn Ẹ̀yà |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON nìkan. A kò ṣètìlẹ́yìn fún àwọn SBOM XML.

## Àwọn Ipò Ìkùnà

Ìṣe náà máa ń jáde pẹ̀lú kóòdù 1, ó sì ń ṣètò `valid=false` nínú àwọn ọ̀ràn wọ̀nyí:

| Ipò | Ìfìránṣẹ́ àṣìṣe |
|-----------|---------------|
| Fáìlì kò sí | `Input file not found: <path>` |
| Fáìlì kì í ṣe JSON tí ó tọ́ | `Input file is not valid JSON: <path>` |
| A kò lè ṣàwárí ọ̀nà-ìṣètò | `Unable to detect SBOM format` |
| A kò lè ṣàwárí ẹ̀yà | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Kò sí àtòjọ-ìṣètò fún ẹ̀yà tí a ṣàwárí | `Schema file not found for <format> <version>` |
| Ìjẹ́rìísí àtòjọ-ìṣètò kùnà | Èsì àṣìṣe ajv-cli pẹ̀lú àwọn àlàyé |

## Àwọn Àpẹẹrẹ

### Ọ̀nà-ìṣètò àti ẹ̀yà pàtó

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Ka àwọn èsì-ìjáde

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

### Jẹ́rìísí ọ̀pọ̀lọpọ̀ fáìlì

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

### Ìṣọ́-ẹnu-ọ̀nà PR

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

## Àwòṣe Ààbò

- **Kò sí ìpè nẹ́tíwọ́ọ̀kì nígbà ìjẹ́rìísí.** Àwọn àtòjọ-ìṣètò ti wà nínú ibi-ìpamọ́ náà. Ìpè nẹ́tíwọ́ọ̀kì kan ṣoṣo ni `npm install ajv-cli ajv-formats` nígbà ìṣètò.
- **Kò sí ìkójọ-dátà àṣírí.** Ìṣe náà kì í pè sí ilé tàbí kó dátà jọ.
- **Ó ń ṣiṣẹ́ nínú àpótí-ẹ̀rọ iṣẹ́.** Kò sí fífà Docker, kò sí àwọn iṣẹ́-ìpèsè ìta.
- **Àṣẹ tó kéré jùlọ.** Ó nílò `contents: read` nìkan.

Fún ìdánilójú tí ó ga jù, so ó mọ́ commit SHA pípé:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Ìbáramu

- Ó ń ṣiṣẹ́ lórí `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Ó nílò Node.js (tí a ti fi sórí ẹ̀rọ tẹ́lẹ̀ lórí gbogbo àwọn olùṣiṣẹ́ tí GitHub ń gbàlejò).
- Ó nílò `jq` (tí a ti fi sórí ẹ̀rọ tẹ́lẹ̀ lórí gbogbo àwọn olùṣiṣẹ́ tí GitHub ń gbàlejò).
- Àwọn olùṣiṣẹ́ tí o gbàlejò fúnra rẹ nílò Node.js >= 18 àti jq nínú PATH.

## Àwọn Àtúnṣe Àtòjọ-ìṣètò

Láti sọ àwọn àtòjọ-ìṣètò tí a fi sínú ibi-ìpamọ́ di tuntun láti orísun-òkè:

```bash
./scripts/update-schemas.sh
```

## Ìwé-àṣẹ

Apache-2.0 -- wo [LICENSE](../../../LICENSE).
