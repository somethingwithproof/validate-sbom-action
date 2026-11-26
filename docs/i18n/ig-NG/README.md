<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Igbo** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · **Igbo** · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Nyochaa faịlụ SBOM megide schema JSON e kwadoro nke CycloneDX na SPDX. Na-enweghị ịntanetị. Enweghị oku netwọk n'oge nnyocha.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Ojiji

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Action ahụ na-achọpụta ọdịdị (CycloneDX ma ọ bụ SPDX) na ụdị nkọwapụta n'akpaghị aka site na faịlụ ahụ. Ọ na-apụ na koodu na-abụghị efu ma ọ bụrụ na nnyocha adaa.

## Ntinye

| Ntinye | A chọrọ ya | Ndabara | Nkọwa |
|-------|----------|---------|-------------|
| `input-file` | ee | -- | Ụzọ gaa na faịlụ SBOM JSON |
| `format` | mba | `auto` | `cyclonedx`, `spdx`, ma ọ bụ `auto` (chọpụta site na faịlụ) |
| `version` | mba | `auto` | Ụdị nkọwapụta (dị ka `1.6`, `2.3`) ma ọ bụ `auto` (chọpụta site na faịlụ) |

## Nsonaazụ

| Nsonaazụ | Nkọwa |
|--------|-------------|
| `valid` | `true` ma ọ bụrụ na SBOM agafee nnyocha schema, `false` ma ọ bụghị ya |
| `format` | Ọdịdị a chọpụtara: `cyclonedx` ma ọ bụ `spdx` |
| `spec-version` | Ụdị nkọwapụta a chọpụtara (dị ka `1.6`, `2.3`) |
| `error-count` | Ọnụọgụgụ e mere atụmatụ nke njehie nnyocha (0 mgbe ọ ziri ezi) |

## Ọdịdị A Kwadoro

| Ọdịdị | Ụdị |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON naanị. A naghị akwado XML SBOM.

## Ọnọdụ Ọdịda

Action ahụ na-apụ na koodu 1 ma tọọ `valid=false` n'ọnọdụ ndị a:

| Ọnọdụ | Ozi njehie |
|-----------|---------------|
| Faịlụ adịghị | `Input file not found: <path>` |
| Faịlụ abụghị JSON ziri ezi | `Input file is not valid JSON: <path>` |
| Enweghị ike ịchọpụta ọdịdị | `Unable to detect SBOM format` |
| Enweghị ike ịchọpụta ụdị | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Enweghị schema maka ụdị a chọpụtara | `Schema file not found for <format> <version>` |
| Nnyocha schema dara | Nsonaazụ njehie ajv-cli nwere nkọwa zuru ezu |

Ụzọ ọdịda niile na-ede nsonaazụ (`valid=false`, `error-count=1`) tupu ha apụọ, ka nzọụkwụ ndị na-esote wee nwee ike ịgụ ha ọbụna mgbe ọdịda mere site na `continue-on-error: true`.

## Ihe Atụ

### Ọdịdị na ụdị doro anya

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Gụọ nsonaazụ

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

### Nyochaa ọtụtụ faịlụ

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

### Nnyocha nnabata PR

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

## Ụdị Nchekwa

- **Enweghị oku netwọk n'oge nnyocha.** E tinyere schema ndị ahụ n'ime ebe nchekwa ahụ. Naanị oku netwọk bụ `npm install ajv-cli ajv-formats` n'oge nhazi.
- **Enweghị telemetry.** Action ahụ anaghị eziga ozi azụ ma ọ bụ achịkọta data.
- **Na-agba n'ime container nke job.** Enweghị ndọta Docker, enweghị ọrụ mpụga.
- **Ikike kacha nta.** Chọrọ naanị `contents: read`.

Maka nkwenye dị elu karịa, kegide ya na commit SHA zuru oke:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Ndakọrịta

- Na-agba na `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Chọrọ Node.js (a wụnyebuola ya na runner niile nke GitHub na-elekọta).
- Chọrọ `jq` (a wụnyebuola ya na runner niile nke GitHub na-elekọta).
- Runner nke onwe chọrọ Node.js >= 18 na jq n'ime PATH.

## Mmelite Schema

Iji mee ka schema e tinyere n'ebe nchekwa dị ọhụrụ site na upstream:

```bash
./scripts/update-schemas.sh
```

## Ikikere

Apache-2.0 -- hụ [LICENSE](../../../LICENSE).
