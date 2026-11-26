<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Deutsch** · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · **Deutsch** · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Validiert SBOM-Dateien gegen offizielle CycloneDX- und SPDX-JSON-Schemas. Offline. Keine Netzwerkaufrufe zur Validierungszeit.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Verwendung

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Die Action erkennt Format (CycloneDX oder SPDX) und Spezifikationsversion automatisch aus der Datei. Bei fehlgeschlagener Validierung beendet sie sich mit einem Exit-Code ungleich null.

## Eingaben

| Eingabe | Erforderlich | Standard | Beschreibung |
|-------|----------|---------|-------------|
| `input-file` | ja | -- | Pfad zur SBOM-JSON-Datei |
| `format` | nein | `auto` | `cyclonedx`, `spdx` oder `auto` (aus Datei erkennen) |
| `version` | nein | `auto` | Spezifikationsversion (z. B. `1.6`, `2.3`) oder `auto` (aus Datei erkennen) |

## Ausgaben

| Ausgabe | Beschreibung |
|--------|-------------|
| `valid` | `true`, wenn die SBOM die Schemavalidierung besteht, sonst `false` |
| `format` | Erkanntes Format: `cyclonedx` oder `spdx` |
| `spec-version` | Erkannte Spezifikationsversion (z. B. `1.6`, `2.3`) |
| `error-count` | Ungefähre Anzahl der Validierungsfehler (0 bei gültiger Datei) |

## Unterstützte Formate

| Format | Versionen |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Nur JSON. XML-SBOMs werden nicht unterstützt.

## Fehlerszenarien

Die Action beendet sich mit Code 1 und setzt `valid=false` in folgenden Fällen:

| Bedingung | Fehlermeldung |
|-----------|---------------|
| Datei existiert nicht | `Input file not found: <path>` |
| Datei ist kein gültiges JSON | `Input file is not valid JSON: <path>` |
| Format kann nicht erkannt werden | `Unable to detect SBOM format` |
| Version kann nicht erkannt werden | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Kein Schema für die erkannte Version | `Schema file not found for <format> <version>` |
| Schemavalidierung schlägt fehl | ajv-cli-Fehlerausgabe mit Details |

## Beispiele

### Explizites Format und explizite Version

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Ausgaben auslesen

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

### Mehrere Dateien validieren

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

### PR-Gating

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

## Sicherheitsmodell

- **Keine Netzwerkaufrufe zur Validierungszeit.** Schemas sind direkt im Repository eingebunden. Der einzige Netzwerkaufruf ist `npm install ajv-cli ajv-formats` während der Einrichtung.
- **Keine Telemetrie.** Die Action sendet keine Daten nach außen und erfasst keine Nutzungsdaten.
- **Ausführung im Job-Container.** Kein Docker-Pull, keine externen Dienste.
- **Prinzip der minimalen Rechte.** Benötigt lediglich `contents: read`.

Für höhere Sicherheit auf einen vollständigen Commit-SHA pinnen:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Kompatibilität

- Läuft auf `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Erfordert Node.js (auf allen von GitHub gehosteten Runnern vorinstalliert).
- Erfordert `jq` (auf allen von GitHub gehosteten Runnern vorinstalliert).
- Selbst gehostete Runner benötigen Node.js >= 18 und jq im PATH.

## Schema-Aktualisierungen

Um die eingebundenen Schemas aus dem Upstream zu aktualisieren:

```bash
./scripts/update-schemas.sh
```

## Lizenz

Apache-2.0 – siehe [LICENSE](../../../LICENSE).
