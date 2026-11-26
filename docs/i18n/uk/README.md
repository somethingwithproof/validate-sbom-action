<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Українська** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · **Українська** · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Перевірка файлів SBOM за офіційними JSON-схемами CycloneDX і SPDX. Автономно. Без мережевих запитів під час валідації.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Використання

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Дія автоматично визначає формат (CycloneDX або SPDX) і версію специфікації з файлу. Якщо перевірка не пройдена, дія завершується з ненульовим кодом виходу.

## Вхідні параметри

| Параметр | Обов'язковий | За замовчуванням | Опис |
|-------|----------|---------|-------------|
| `input-file` | так | -- | Шлях до JSON-файлу SBOM |
| `format` | ні | `auto` | `cyclonedx`, `spdx` або `auto` (визначити з файлу) |
| `version` | ні | `auto` | Версія специфікації (наприклад, `1.6`, `2.3`) або `auto` (визначити з файлу) |

## Вихідні параметри

| Параметр | Опис |
|--------|-------------|
| `valid` | `true`, якщо SBOM пройшов перевірку схеми, інакше `false` |
| `format` | Визначений формат: `cyclonedx` або `spdx` |
| `spec-version` | Визначена версія специфікації (наприклад, `1.6`, `2.3`) |
| `error-count` | Орієнтовна кількість помилок валідації (0, якщо файл коректний) |

## Підтримувані формати

| Формат | Версії |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Лише JSON. Файли SBOM у форматі XML не підтримуються.

## Режими збою

Дія завершується з кодом 1 і встановлює `valid=false` у таких випадках:

| Умова | Повідомлення про помилку |
|-----------|---------------|
| Файл не існує | `Input file not found: <path>` |
| Файл не є коректним JSON | `Input file is not valid JSON: <path>` |
| Неможливо визначити формат | `Unable to detect SBOM format` |
| Неможливо визначити версію | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Відсутня схема для визначеної версії | `Schema file not found for <format> <version>` |
| Перевірка схеми не пройдена | Виведення помилок ajv-cli з подробицями |

Усі гілки завершення з помилкою записують вихідні параметри (`valid=false`, `error-count=1`) перед виходом, тому наступні кроки можуть зчитувати їх навіть у разі збою за наявності `continue-on-error: true`.

## Приклади

### Явне задання формату та версії

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Зчитування вихідних параметрів

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

### Перевірка кількох файлів

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

### Контроль перевірки в PR

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

## Модель безпеки

- **Без мережевих запитів під час валідації.** Схеми постачаються безпосередньо в репозиторії. Єдиний мережевий запит — `npm install ajv-cli ajv-formats` на етапі налаштування.
- **Без телеметрії.** Дія не надсилає жодних даних і не збирає статистику.
- **Виконання в контейнері завдання.** Без завантаження образів Docker і без зовнішніх сервісів.
- **Мінімальні привілеї.** Потребує лише `contents: read`.

Для вищого рівня надійності зафіксуйте повний SHA коміту:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Сумісність

- Працює на `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Потребує Node.js (попередньо встановлено на всіх раннерах, розміщених у GitHub).
- Потребує `jq` (попередньо встановлено на всіх раннерах, розміщених у GitHub).
- Власні (self-hosted) раннери потребують Node.js >= 18 і jq у PATH.

## Оновлення схем

Щоб оновити вбудовані схеми з апстріму:

```bash
./scripts/update-schemas.sh
```

## Ліцензія

Apache-2.0 — див. [LICENSE](../../../LICENSE).
