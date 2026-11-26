<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Bosanski** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** **Bosanski** · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Provjeravajte SBOM datoteke u odnosu na zvanične CycloneDX i SPDX JSON šeme. Van mreže. Bez mrežnih poziva tokom provjere.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Korištenje

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Akcija automatski prepoznaje format (CycloneDX ili SPDX) i verziju specifikacije iz datoteke. Ako provjera ne uspije, završava s izlaznim kodom različitim od nule.

## Ulazni parametri

| Ulaz | Obavezno | Zadano | Opis |
|-------|----------|---------|-------------|
| `input-file` | da | -- | Putanja do SBOM JSON datoteke |
| `format` | ne | `auto` | `cyclonedx`, `spdx` ili `auto` (prepoznaj iz datoteke) |
| `version` | ne | `auto` | Verzija specifikacije (npr. `1.6`, `2.3`) ili `auto` (prepoznaj iz datoteke) |

## Izlazni parametri

| Izlaz | Opis |
|--------|-------------|
| `valid` | `true` ako SBOM prođe provjeru šeme, inače `false` |
| `format` | Prepoznati format: `cyclonedx` ili `spdx` |
| `spec-version` | Prepoznata verzija specifikacije (npr. `1.6`, `2.3`) |
| `error-count` | Približan broj grešaka pri provjeri (0 kada je ispravno) |

## Podržani formati

| Format | Verzije |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Samo JSON. XML SBOM datoteke nisu podržane.

## Načini grešaka

Akcija završava s kodom 1 i postavlja `valid=false` u sljedećim slučajevima:

| Uslov | Poruka greške |
|-----------|---------------|
| Datoteka ne postoji | `Input file not found: <path>` |
| Datoteka nije ispravan JSON | `Input file is not valid JSON: <path>` |
| Format se ne može prepoznati | `Unable to detect SBOM format` |
| Verzija se ne može prepoznati | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Nema šeme za prepoznatu verziju | `Schema file not found for <format> <version>` |
| Provjera šeme nije uspjela | ajv-cli izlaz greške s detaljima |

## Primjeri

### Izričito zadavanje formata i verzije

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Čitanje izlaza

```yaml
- uses: thomasvincent/validate-sbom-action@v1
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
  - uses: thomasvincent/validate-sbom-action@v1
    with:
      input-file: ${{ matrix.sbom.path }}
      format: ${{ matrix.sbom.format }}
```

### Provjera za Pull Request

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

- **Bez mrežnih poziva tokom provjere.** Šeme su uključene direktno u repozitorij. Jedini mrežni poziv je `npm install ajv-cli ajv-formats` tokom postavljanja.
- **Bez telemetrije.** Akcija ne šalje podatke na udaljene servere niti ih prikuplja.
- **Pokreće se u kontejneru posla.** Bez preuzimanja Docker slika i bez vanjskih servisa.
- **Najmanje privilegije.** Zahtijeva samo `contents: read`.

Za viši nivo sigurnosti vežite akciju za puni SHA sažetak commita:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Kompatibilnost

- Radi na `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Zahtijeva Node.js (unaprijed instaliran na svim runnerima koje hostuje GitHub).
- Zahtijeva `jq` (unaprijed instaliran na svim runnerima koje hostuje GitHub).
- Vlastiti (self-hosted) runneri zahtijevaju Node.js >= 18 i `jq` u `PATH`.

## Ažuriranje šema

Za osvježavanje uključenih šema iz uzvodnih izvora:

```bash
./scripts/update-schemas.sh
```

## Licenca

Apache-2.0 -- pogledajte [LICENSE](../../../LICENSE).
