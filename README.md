<!-- translations:start -->
**Languages:** **English** · [Deutsch](docs/i18n/de/README.md) · [Español](docs/i18n/es/README.md) · [Français](docs/i18n/fr/README.md) · [Português (BR)](docs/i18n/pt-BR/README.md) · [Русский](docs/i18n/ru/README.md) · [日本語](docs/i18n/ja/README.md) · [한국어](docs/i18n/ko/README.md) · [简体中文](docs/i18n/zh-CN/README.md) · [العربية](docs/i18n/ar/README.md) · [हिन्दी](docs/i18n/hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** **English** · [Deutsch](docs/i18n/de/README.md) · [Español](docs/i18n/es/README.md) · [Français](docs/i18n/fr/README.md) · [Italiano](docs/i18n/it/README.md) · [Português (BR)](docs/i18n/pt-BR/README.md) · [Nederlands](docs/i18n/nl/README.md) · [Русский](docs/i18n/ru/README.md) · [Українська](docs/i18n/uk/README.md) · [日本語](docs/i18n/ja/README.md) · [한국어](docs/i18n/ko/README.md) · [简体中文](docs/i18n/zh-CN/README.md) · [繁體中文](docs/i18n/zh-TW/README.md) · [العربية](docs/i18n/ar/README.md) · [हिन्दी](docs/i18n/hi/README.md) · [Polski](docs/i18n/pl/README.md) · [Türkçe](docs/i18n/tr/README.md) · [Svenska](docs/i18n/sv/README.md) · [Tiếng Việt](docs/i18n/vi/README.md) · [Bahasa Indonesia](docs/i18n/id/README.md)
- **Africa:** [Afrikaans](docs/i18n/af-ZA/README.md) · [አማርኛ](docs/i18n/am-ET/README.md) · [العربية (مصر)](docs/i18n/ar-EG/README.md) · [العربية (المغرب)](docs/i18n/ar-MA/README.md) · [Français (Maroc)](docs/i18n/fr-MA/README.md) · [Français (Sénégal)](docs/i18n/fr-SN/README.md) · [Hausa](docs/i18n/ha-NG/README.md) · [Igbo](docs/i18n/ig-NG/README.md) · [Malagasy](docs/i18n/mg-MG/README.md) · [Kinyarwanda](docs/i18n/rw-RW/README.md) · [Soomaali](docs/i18n/so-SO/README.md) · [Kiswahili](docs/i18n/sw-KE/README.md) · [isiXhosa](docs/i18n/xh-ZA/README.md) · [Yorùbá](docs/i18n/yo-NG/README.md) · [isiZulu](docs/i18n/zu-ZA/README.md)
- **Asia:** [বাংলা](docs/i18n/bn/README.md) · [فارسی](docs/i18n/fa/README.md) · [עברית](docs/i18n/he/README.md) · [मराठी](docs/i18n/mr/README.md) · [தமிழ்](docs/i18n/ta/README.md) · [తెలుగు](docs/i18n/te/README.md) · [ไทย](docs/i18n/th/README.md) · [اردو](docs/i18n/ur/README.md) · [Bahasa Melayu](docs/i18n/ms/README.md) · [Filipino](docs/i18n/fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Validate SBOM files against official CycloneDX and SPDX JSON schemas. Offline. No network calls at validation time.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Usage

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

The action auto-detects format (CycloneDX or SPDX) and spec version from the file. It exits non-zero if validation fails.

## Inputs

| Input | Required | Default | Description |
|-------|----------|---------|-------------|
| `input-file` | yes | -- | Path to the SBOM JSON file |
| `format` | no | `auto` | `cyclonedx`, `spdx`, or `auto` (detect from file) |
| `version` | no | `auto` | Spec version (e.g., `1.6`, `2.3`) or `auto` (detect from file) |

## Outputs

| Output | Description |
|--------|-------------|
| `valid` | `true` if the SBOM passes schema validation, `false` otherwise |
| `format` | Detected format: `cyclonedx` or `spdx` |
| `spec-version` | Detected spec version (e.g., `1.6`, `2.3`) |
| `error-count` | Approximate number of validation errors (0 when valid) |

## Supported Formats

| Format | Versions |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON only. XML SBOMs are not supported.

## Failure Modes

The action exits with code 1 and sets `valid=false` in these cases:

| Condition | Error message |
|-----------|---------------|
| File does not exist | `Input file not found: <path>` |
| File is not valid JSON | `Input file is not valid JSON: <path>` |
| Format cannot be detected | `Unable to detect SBOM format` |
| Version cannot be detected | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| No schema for detected version | `Schema file not found for <format> <version>` |
| Schema validation fails | ajv-cli error output with details |

All failure paths write outputs (`valid=false`, `error-count=1`) before exiting, so downstream steps can read them even on failure with `continue-on-error: true`.

## Examples

### Explicit format and version

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Read outputs

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

### Validate multiple files

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

### PR gating

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

## Security Model

- **No network calls at validation time.** Schemas are vendored in the repository. The only network call is `npm install ajv-cli ajv-formats` during setup.
- **No telemetry.** The action does not phone home or collect data.
- **Runs in the job container.** No Docker pull, no external services.
- **Least privilege.** Requires only `contents: read`.

For higher assurance, pin to a full commit SHA:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Compatibility

- Runs on `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Requires Node.js (pre-installed on all GitHub-hosted runners).
- Requires `jq` (pre-installed on all GitHub-hosted runners).
- Self-hosted runners need Node.js >= 18 and jq in PATH.

## Schema Updates

To refresh vendored schemas from upstream:

```bash
./scripts/update-schemas.sh
```

## License

Apache-2.0 -- see [LICENSE](LICENSE).
