<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Italiano** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · **Italiano** · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Valida i file SBOM rispetto agli schemi JSON ufficiali CycloneDX e SPDX. Offline. Nessuna chiamata di rete al momento della validazione.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Utilizzo

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

L'action rileva automaticamente il formato (CycloneDX o SPDX) e la versione della specifica dal file. Termina con un codice di uscita diverso da zero se la validazione fallisce.

## Input

| Input | Obbligatorio | Predefinito | Descrizione |
|-------|----------|---------|-------------|
| `input-file` | sì | -- | Percorso del file SBOM JSON |
| `format` | no | `auto` | `cyclonedx`, `spdx` o `auto` (rileva dal file) |
| `version` | no | `auto` | Versione della specifica (es. `1.6`, `2.3`) o `auto` (rileva dal file) |

## Output

| Output | Descrizione |
|--------|-------------|
| `valid` | `true` se lo SBOM supera la validazione dello schema, `false` altrimenti |
| `format` | Formato rilevato: `cyclonedx` o `spdx` |
| `spec-version` | Versione della specifica rilevata (es. `1.6`, `2.3`) |
| `error-count` | Numero approssimativo di errori di validazione (0 quando è valido) |

## Formati supportati

| Formato | Versioni |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Solo JSON. Gli SBOM in formato XML non sono supportati.

## Modalità di errore

L'action termina con codice 1 e imposta `valid=false` nei seguenti casi:

| Condizione | Messaggio di errore |
|-----------|---------------|
| Il file non esiste | `Input file not found: <path>` |
| Il file non è un JSON valido | `Input file is not valid JSON: <path>` |
| Impossibile rilevare il formato | `Unable to detect SBOM format` |
| Impossibile rilevare la versione | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Nessuno schema per la versione rilevata | `Schema file not found for <format> <version>` |
| Validazione dello schema fallita | Output di errore di ajv-cli con i dettagli |

Tutti i percorsi di errore scrivono gli output (`valid=false`, `error-count=1`) prima di terminare, così i passaggi successivi possono leggerli anche in caso di errore con `continue-on-error: true`.

## Esempi

### Formato e versione espliciti

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Lettura degli output

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

### Validazione di più file

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

### Gating delle PR

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

## Modello di sicurezza

- **Nessuna chiamata di rete al momento della validazione.** Gli schemi sono inclusi (vendored) nel repository. L'unica chiamata di rete è `npm install ajv-cli ajv-formats` durante la configurazione.
- **Nessuna telemetria.** L'action non invia dati verso l'esterno né raccoglie informazioni.
- **Esecuzione nel container del job.** Nessun pull Docker, nessun servizio esterno.
- **Privilegio minimo.** Richiede solo `contents: read`.

Per una maggiore garanzia, fissa il riferimento a uno SHA di commit completo:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Compatibilità

- Viene eseguita su `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Richiede Node.js (preinstallato su tutti i runner ospitati da GitHub).
- Richiede `jq` (preinstallato su tutti i runner ospitati da GitHub).
- I runner self-hosted richiedono Node.js >= 18 e jq nel PATH.

## Aggiornamenti degli schemi

Per aggiornare gli schemi inclusi dalla sorgente upstream:

```bash
./scripts/update-schemas.sh
```

## Licenza

Apache-2.0 -- vedi [LICENSE](../../../LICENSE).
