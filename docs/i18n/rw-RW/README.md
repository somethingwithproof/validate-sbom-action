<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Kinyarwanda** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · **Kinyarwanda** · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Genzura amadosiye ya SBOM ugendeye ku nyandiko z'imiterere (schemas) za JSON zemewe za CycloneDX na SPDX. Bikorwa nta murandasi. Nta guhamagara umuyoboro mu gihe cy'igenzura.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Uko bikoreshwa

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Iki gikorwa cyimenyera uburyo bw'idosiye (CycloneDX cyangwa SPDX) na verisiyo y'amabwiriza uhereye ku idosiye. Kiva mu gikorwa gifite kode itari zeru iyo igenzura ritsinzwe.

## Ibishyirwamo

| Icyinjizwa | Bisabwa | Mbanziriza | Ibisobanuro |
|-------|----------|---------|-------------|
| `input-file` | yego | -- | Inzira y'idosiye ya JSON ya SBOM |
| `format` | oya | `auto` | `cyclonedx`, `spdx`, cyangwa `auto` (kwimenyera uhereye ku idosiye) |
| `version` | oya | `auto` | Verisiyo y'amabwiriza (urugero, `1.6`, `2.3`) cyangwa `auto` (kwimenyera uhereye ku idosiye) |

## Ibisohoka

| Igisohoka | Ibisobanuro |
|--------|-------------|
| `valid` | `true` iyo SBOM yatsinze igenzura rya schema, `false` iyo bitabaye ibyo |
| `format` | Uburyo bwamenyekanye: `cyclonedx` cyangwa `spdx` |
| `spec-version` | Verisiyo y'amabwiriza yamenyekanye (urugero, `1.6`, `2.3`) |
| `error-count` | Umubare ugereranyije w'amakosa y'igenzura (0 iyo byemewe) |

## Uburyo bwemewe

| Uburyo | Verisiyo |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON gusa. Amadosiye ya SBOM ya XML ntashyigikiwe.

## Uburyo bwo gutsindwa

Iki gikorwa gisohoka gifite kode 1 kandi kigashyiraho `valid=false` muri ibi bihe:

| Imiterere | Ubutumwa bw'ikosa |
|-----------|---------------|
| Idosiye ntibaho | `Input file not found: <path>` |
| Idosiye si JSON yemewe | `Input file is not valid JSON: <path>` |
| Uburyo ntibushobora kumenyekana | `Unable to detect SBOM format` |
| Verisiyo ntishobora kumenyekana | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Nta schema ya verisiyo yamenyekanye | `Schema file not found for <format> <version>` |
| Igenzura rya schema riratsinzwe | Ibisohoka by'ikosa bya ajv-cli bifite ibisobanuro birambuye |

Inzira zose zitsinzwe zandika ibisohoka (`valid=false`, `error-count=1`) mbere yo gusohoka, kugira ngo intambwe zikurikira zishobore kubisoma n'igihe habayeho gutsindwa hakoreshejwe `continue-on-error: true`.

## Ingero

### Uburyo na verisiyo bigaragajwe ku mugaragaro

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Gusoma ibisohoka

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

### Kugenzura amadosiye menshi

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

### Igenzura rya PR

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

## Imiterere y'umutekano

- **Nta guhamagara umuyoboro mu gihe cy'igenzura.** Schema zibitswe mu bubiko. Guhamagara umuyoboro kumwe gusa ni `npm install ajv-cli ajv-formats` mu gihe cyo gutegura.
- **Nta telemetry.** Iki gikorwa ntikohereza amakuru hanze cyangwa ngo gikusanye amakuru.
- **Gikorera muri container y'umurimo.** Nta gukurura Docker, nta serivisi zo hanze.
- **Uburenganzira buke bushoboka.** Bisaba `contents: read` gusa.

Kugira ngo ugire icyizere cyisumbuye, shyiraho SHA yuzuye ya commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Imikoranire

- Gikorera kuri `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Bisaba Node.js (isanzwe ishyizweho kuri runner zose zicumbikiwe na GitHub).
- Bisaba `jq` (isanzwe ishyizweho kuri runner zose zicumbikiwe na GitHub).
- Runner zicumbikiwe ku giti cyazo zikeneye Node.js >= 18 na jq muri PATH.

## Ivugurura rya Schema

Kugira ngo uvugurure schema zibitswe mu bubiko uhereye ku isoko y'ibanze:

```bash
./scripts/update-schemas.sh
```

## Uruhushya

Apache-2.0 -- reba [LICENSE](../../../LICENSE).
