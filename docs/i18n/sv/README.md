<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Svenska** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · **Svenska** · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Validera SBOM-filer mot officiella JSON-scheman för CycloneDX och SPDX. Offline. Inga nätverksanrop vid valideringstillfället.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Användning

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Åtgärden identifierar automatiskt format (CycloneDX eller SPDX) och specifikationsversion från filen. Den avslutas med en slutkod skild från noll om valideringen misslyckas.

## Indata

| Indata | Obligatorisk | Standardvärde | Beskrivning |
|-------|----------|---------|-------------|
| `input-file` | ja | -- | Sökväg till SBOM JSON-filen |
| `format` | nej | `auto` | `cyclonedx`, `spdx` eller `auto` (identifiera från filen) |
| `version` | nej | `auto` | Specifikationsversion (t.ex. `1.6`, `2.3`) eller `auto` (identifiera från filen) |

## Utdata

| Utdata | Beskrivning |
|--------|-------------|
| `valid` | `true` om SBOM-filen klarar schemavalideringen, annars `false` |
| `format` | Identifierat format: `cyclonedx` eller `spdx` |
| `spec-version` | Identifierad specifikationsversion (t.ex. `1.6`, `2.3`) |
| `error-count` | Ungefärligt antal valideringsfel (0 vid giltigt resultat) |

## Format som stöds

| Format | Versioner |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Endast JSON. XML-baserade SBOM-filer stöds inte.

## Fellägen

Åtgärden avslutas med kod 1 och sätter `valid=false` i följande fall:

| Villkor | Felmeddelande |
|-----------|---------------|
| Filen finns inte | `Input file not found: <path>` |
| Filen är inte giltig JSON | `Input file is not valid JSON: <path>` |
| Formatet kan inte identifieras | `Unable to detect SBOM format` |
| Versionen kan inte identifieras | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Inget schema för identifierad version | `Schema file not found for <format> <version>` |
| Schemavalideringen misslyckas | Felutdata från ajv-cli med detaljer |

Alla felvägar skriver utdata (`valid=false`, `error-count=1`) innan avslut, så att efterföljande steg kan läsa dem även vid fel med `continue-on-error: true`.

## Exempel

### Uttryckligt format och version

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Läsa utdata

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

### Validera flera filer

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

### PR-kontroll

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

## Säkerhetsmodell

- **Inga nätverksanrop vid valideringstillfället.** Scheman ingår direkt i arkivet. Det enda nätverksanropet är `npm install ajv-cli ajv-formats` under konfigurationen.
- **Ingen telemetri.** Åtgärden skickar ingen data och samlar inte in någon information.
- **Körs i jobbcontainern.** Ingen Docker-hämtning, inga externa tjänster.
- **Minsta möjliga behörighet.** Kräver endast `contents: read`.

För högre säkerhet, lås till en fullständig commit-SHA:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Kompatibilitet

- Körs på `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Kräver Node.js (förinstallerat på alla GitHub-värdade runners).
- Kräver `jq` (förinstallerat på alla GitHub-värdade runners).
- Självvärdade runners kräver Node.js >= 18 och jq i PATH.

## Schemauppdateringar

För att uppdatera de inkluderade schemana från uppströmskällan:

```bash
./scripts/update-schemas.sh
```

## Licens

Apache-2.0 -- se [LICENSE](../../../LICENSE).
