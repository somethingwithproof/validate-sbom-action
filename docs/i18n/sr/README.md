<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Српски** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · **Српски**

</details>
<!-- translations:end -->

# validate-sbom-action

Проверавајте SBOM датотеке у односу на званичне CycloneDX и SPDX JSON шеме. Ван мреже. Без мрежних позива током провере.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Коришћење

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Акција аутоматски препознаје формат (CycloneDX или SPDX) и верзију спецификације из датотеке. Завршава са ненултим излазним кодом ако провера не успе.

## Улазни параметри

| Улаз | Обавезно | Подразумевано | Опис |
|-------|----------|---------|-------------|
| `input-file` | да | -- | Путања до SBOM JSON датотеке |
| `format` | не | `auto` | `cyclonedx`, `spdx` или `auto` (препознај из датотеке) |
| `version` | не | `auto` | Верзија спецификације (нпр. `1.6`, `2.3`) или `auto` (препознај из датотеке) |

## Излазни параметри

| Излаз | Опис |
|--------|-------------|
| `valid` | `true` ако SBOM прође проверу шеме, иначе `false` |
| `format` | Препознати формат: `cyclonedx` или `spdx` |
| `spec-version` | Препозната верзија спецификације (нпр. `1.6`, `2.3`) |
| `error-count` | Приближан број грешака провере (0 када је датотека исправна) |

## Подржани формати

| Формат | Верзије |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Само JSON. XML SBOM датотеке нису подржане.

## Начини грешака

Акција завршава са кодом 1 и поставља `valid=false` у следећим случајевима:

| Услов | Порука грешке |
|-----------|---------------|
| Датотека не постоји | `Input file not found: <path>` |
| Датотека није исправан JSON | `Input file is not valid JSON: <path>` |
| Формат се не може препознати | `Unable to detect SBOM format` |
| Верзија се не може препознати | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Нема шеме за препознату верзију | `Schema file not found for <format> <version>` |
| Провера шеме није успела | излаз грешке алата ajv-cli са детаљима |

## Примери

### Изричито задавање формата и верзије

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Читање излаза

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

### Провера више датотека

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

### Провера за Pull Request

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

## Безбедносни модел

- **Без мрежних позива током провере.** Шеме су укључене директно у репозиторијум. Једини мрежни позив је `npm install ajv-cli ajv-formats` приликом подешавања.
- **Без телеметрије.** Акција не шаље податке на удаљене сервере нити их прикупља.
- **Покреће се у контејнеру посла.** Без преузимања Docker слика и без спољних сервиса.
- **Најмања овлашћења.** Захтева само `contents: read`.

За виши ниво сигурности вежите акцију за пуни SHA сажетак комита:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Компатибилност

- Ради на `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Захтева Node.js (унапред инсталиран на свим GitHub серверима за извршавање).
- Захтева `jq` (унапред инсталиран на свим GitHub серверима за извршавање).
- Сопствени сервери захтевају Node.js >= 18 и `jq` у променљивој `PATH`.

## Ажурирање шема

Да освежите укључене шеме из узводних извора:

```bash
./scripts/update-schemas.sh
```

## Лиценца

Apache-2.0 -- погледајте [LICENSE](../../../LICENSE).
