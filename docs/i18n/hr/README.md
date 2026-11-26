<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Hrvatski** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · **Hrvatski** · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Provjeravajte SBOM datoteke prema službenim CycloneDX i SPDX JSON shemama. Izvanmrežno. Bez mrežnih poziva tijekom provjere valjanosti.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Upotreba

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Radnja automatski prepoznaje format (CycloneDX ili SPDX) i inačicu specifikacije iz datoteke. Ako provjera valjanosti ne uspije, završava s izlaznim kodom različitim od nule.

## Ulazni parametri

| Ulaz | Obvezno | Zadano | Opis |
|-------|----------|---------|-------------|
| `input-file` | da | -- | Putanja do SBOM JSON datoteke |
| `format` | ne | `auto` | `cyclonedx`, `spdx` ili `auto` (prepoznaj iz datoteke) |
| `version` | ne | `auto` | Inačica specifikacije (npr. `1.6`, `2.3`) ili `auto` (prepoznaj iz datoteke) |

## Izlazni parametri

| Izlaz | Opis |
|--------|-------------|
| `valid` | `true` ako SBOM prođe provjeru sheme, inače `false` |
| `format` | Prepoznati format: `cyclonedx` ili `spdx` |
| `spec-version` | Prepoznata inačica specifikacije (npr. `1.6`, `2.3`) |
| `error-count` | Približan broj pogrešaka provjere valjanosti (0 kada je valjano) |

## Podržani formati

| Format | Inačice |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Samo JSON. XML SBOM datoteke nisu podržane.

## Načini pogrešaka

Radnja završava s kodom 1 i postavlja `valid=false` u sljedećim slučajevima:

| Uvjet | Poruka pogreške |
|-----------|---------------|
| Datoteka ne postoji | `Input file not found: <path>` |
| Datoteka nije valjani JSON | `Input file is not valid JSON: <path>` |
| Format se ne može prepoznati | `Unable to detect SBOM format` |
| Inačica se ne može prepoznati | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Nema sheme za prepoznatu inačicu | `Schema file not found for <format> <version>` |
| Provjera sheme nije uspjela | Izlaz pogreške alata ajv-cli s pojedinostima |

## Primjeri

### Izričito navođenje formata i inačice

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Čitanje izlaza

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

### Provjera više datoteka

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

### Provjera zahtjeva za spajanje (PR)

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

## Sigurnosni model

- **Bez mrežnih poziva tijekom provjere valjanosti.** Sheme su pohranjene izravno u repozitoriju. Jedini mrežni poziv jest `npm install ajv-cli ajv-formats` tijekom pripreme okruženja.
- **Bez telemetrije.** Radnja ne šalje podatke vanjskim poslužiteljima niti ih prikuplja.
- **Izvodi se u spremniku posla.** Bez preuzimanja Docker slika i bez vanjskih servisa.
- **Najmanje ovlasti.** Zahtijeva samo `contents: read`.

Za višu razinu pouzdanosti prikvačite radnju na puni SHA sažetak commita:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Kompatibilnost

- Izvodi se na `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Zahtijeva Node.js (unaprijed instaliran na svim GitHubovim poslužiteljima za izvođenje).
- Zahtijeva `jq` (unaprijed instaliran na svim GitHubovim poslužiteljima za izvođenje).
- Samostalno udomljeni poslužitelji zahtijevaju Node.js >= 18 i `jq` u varijabli `PATH`.

## Ažuriranje shema

Za osvježavanje pohranjenih shema iz uzvodnog izvora:

```bash
./scripts/update-schemas.sh
```

## Licenca

Apache-2.0 -- pogledajte [LICENSE](../../../LICENSE).
