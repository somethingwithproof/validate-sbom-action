<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · **Français** · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · **Français** · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Validez des fichiers SBOM par rapport aux schémas JSON officiels CycloneDX et SPDX. Hors ligne. Aucun appel réseau au moment de la validation.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Utilisation

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

L'action détecte automatiquement le format (CycloneDX ou SPDX) et la version de spécification à partir du fichier. Elle renvoie un code de sortie non nul en cas d'échec de validation.

## Entrées

| Entrée | Obligatoire | Par défaut | Description |
|-------|----------|---------|-------------|
| `input-file` | oui | -- | Chemin vers le fichier SBOM JSON |
| `format` | non | `auto` | `cyclonedx`, `spdx` ou `auto` (détection depuis le fichier) |
| `version` | non | `auto` | Version de spécification (par exemple, `1.6`, `2.3`) ou `auto` (détection depuis le fichier) |

## Sorties

| Sortie | Description |
|--------|-------------|
| `valid` | `true` si le SBOM réussit la validation par schéma, `false` sinon |
| `format` | Format détecté : `cyclonedx` ou `spdx` |
| `spec-version` | Version de spécification détectée (par exemple, `1.6`, `2.3`) |
| `error-count` | Nombre approximatif d'erreurs de validation (0 lorsque valide) |

## Formats pris en charge

| Format | Versions |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON uniquement. Les SBOM au format XML ne sont pas pris en charge.

## Modes d'échec

L'action se termine avec le code 1 et définit `valid=false` dans les cas suivants :

| Condition | Message d'erreur |
|-----------|---------------|
| Le fichier n'existe pas | `Input file not found: <path>` |
| Le fichier n'est pas du JSON valide | `Input file is not valid JSON: <path>` |
| Le format ne peut pas être détecté | `Unable to detect SBOM format` |
| La version ne peut pas être détectée | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Aucun schéma pour la version détectée | `Schema file not found for <format> <version>` |
| La validation par schéma échoue | Sortie d'erreur d'ajv-cli avec détails |

## Exemples

### Format et version explicites

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Lecture des sorties

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

### Validation de plusieurs fichiers

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

### Contrôle des pull requests

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

## Modèle de sécurité

- **Aucun appel réseau au moment de la validation.** Les schémas sont intégrés directement dans le dépôt. Le seul appel réseau est `npm install ajv-cli ajv-formats` lors de l'initialisation.
- **Aucune télémétrie.** L'action n'envoie aucune donnée et ne collecte aucune information.
- **Exécution dans le conteneur du job.** Aucun téléchargement d'image Docker, aucun service externe.
- **Moindre privilège.** Nécessite uniquement `contents: read`.

Pour un niveau d'assurance accru, épinglez un SHA de commit complet :

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Compatibilité

- Fonctionne sur `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Nécessite Node.js (préinstallé sur tous les runners hébergés par GitHub).
- Nécessite `jq` (préinstallé sur tous les runners hébergés par GitHub).
- Les runners auto-hébergés nécessitent Node.js >= 18 et jq dans le PATH.

## Mise à jour des schémas

Pour actualiser les schémas intégrés depuis les sources amont :

```bash
./scripts/update-schemas.sh
```

## Licence

Apache-2.0 -- voir [LICENSE](../../../LICENSE).
