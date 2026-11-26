<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Nederlands** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · **Nederlands** · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Valideer SBOM-bestanden tegen officiële CycloneDX- en SPDX-JSON-schema's. Offline. Geen netwerkaanroepen tijdens validatie.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Gebruik

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

De actie detecteert automatisch het formaat (CycloneDX of SPDX) en de specificatieversie uit het bestand. De actie sluit af met een foutcode ongelijk aan nul als de validatie mislukt.

## Invoer

| Invoer | Vereist | Standaard | Beschrijving |
|-------|----------|---------|-------------|
| `input-file` | ja | -- | Pad naar het SBOM-JSON-bestand |
| `format` | nee | `auto` | `cyclonedx`, `spdx` of `auto` (detecteren uit bestand) |
| `version` | nee | `auto` | Specificatieversie (bijv. `1.6`, `2.3`) of `auto` (detecteren uit bestand) |

## Uitvoer

| Uitvoer | Beschrijving |
|--------|-------------|
| `valid` | `true` als de SBOM slaagt voor schemavalidatie, anders `false` |
| `format` | Gedetecteerd formaat: `cyclonedx` of `spdx` |
| `spec-version` | Gedetecteerde specificatieversie (bijv. `1.6`, `2.3`) |
| `error-count` | Geschat aantal validatiefouten (0 indien geldig) |

## Ondersteunde formaten

| Formaat | Versies |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Alleen JSON. XML-SBOM's worden niet ondersteund.

## Foutscenario's

De actie sluit af met code 1 en stelt `valid=false` in bij de volgende gevallen:

| Conditie | Foutmelding |
|-----------|---------------|
| Bestand bestaat niet | `Input file not found: <path>` |
| Bestand is geen geldige JSON | `Input file is not valid JSON: <path>` |
| Formaat kan niet worden gedetecteerd | `Unable to detect SBOM format` |
| Versie kan niet worden gedetecteerd | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Geen schema voor gedetecteerde versie | `Schema file not found for <format> <version>` |
| Schemavalidatie mislukt | ajv-cli-foutuitvoer met details |

Alle foutpaden schrijven uitvoerwaarden (`valid=false`, `error-count=1`) weg voordat ze afsluiten, zodat volgende stappen deze ook bij fouten kunnen uitlezen met `continue-on-error: true`.

## Voorbeelden

### Expliciet formaat en versie

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Uitvoerwaarden uitlezen

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

### Meerdere bestanden valideren

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

### PR-gating

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

## Beveiligingsmodel

- **Geen netwerkaanroepen tijdens validatie.** Schema's worden in de repository meegeleverd. De enige netwerkaanroep is `npm install ajv-cli ajv-formats` tijdens de installatie.
- **Geen telemetrie.** De actie stuurt geen gegevens naar buiten en verzamelt geen data.
- **Draait in de jobcontainer.** Geen Docker pull, geen externe services.
- **Minimale rechten.** Vereist alleen `contents: read`.

Zet voor hogere zekerheid vast op een volledige commit-SHA:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Compatibiliteit

- Draait op `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Vereist Node.js (vooraf geïnstalleerd op alle GitHub-hosted runners).
- Vereist `jq` (vooraf geïnstalleerd op alle GitHub-hosted runners).
- Self-hosted runners hebben Node.js >= 18 en jq in PATH nodig.

## Schema-updates

Om meegeleverde schema's vanuit upstream te vernieuwen:

```bash
./scripts/update-schemas.sh
```

## Licentie

Apache-2.0 -- zie [LICENSE](../../../LICENSE).
