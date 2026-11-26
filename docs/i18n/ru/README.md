<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · **Русский** · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · **Русский** · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Проверка файлов SBOM на соответствие официальным JSON-схемам CycloneDX и SPDX. Полностью офлайн. Без сетевых запросов во время проверки.

[![CI](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/thomasvincent/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Использование

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Action автоматически определяет формат (CycloneDX или SPDX) и версию спецификации по содержимому файла. При ошибке проверки завершается с ненулевым кодом возврата.

## Входные параметры

| Параметр | Обязательный | По умолчанию | Описание |
|-------|----------|---------|-------------|
| `input-file` | да | -- | Путь к JSON-файлу SBOM |
| `format` | нет | `auto` | `cyclonedx`, `spdx` или `auto` (определение по файлу) |
| `version` | нет | `auto` | Версия спецификации (например, `1.6`, `2.3`) или `auto` (определение по файлу) |

## Выходные параметры

| Параметр | Описание |
|--------|-------------|
| `valid` | `true`, если SBOM прошёл проверку по схеме, иначе `false` |
| `format` | Определённый формат: `cyclonedx` или `spdx` |
| `spec-version` | Определённая версия спецификации (например, `1.6`, `2.3`) |
| `error-count` | Приблизительное количество ошибок валидации (0 при успешной проверке) |

## Поддерживаемые форматы

| Формат | Версии |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Только JSON. Файлы SBOM в формате XML не поддерживаются.

## Сценарии ошибок

Action завершается с кодом 1 и устанавливает `valid=false` в следующих случаях:

| Условие | Сообщение об ошибке |
|-----------|---------------|
| Файл не существует | `Input file not found: <path>` |
| Файл не является корректным JSON | `Input file is not valid JSON: <path>` |
| Не удалось определить формат | `Unable to detect SBOM format` |
| Не удалось определить версию | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Отсутствует схема для определённой версии | `Schema file not found for <format> <version>` |
| Ошибка проверки по схеме | Вывод ошибок ajv-cli с подробностями |

Во всех сценариях сбоя перед завершением записываются выходные параметры (`valid=false`, `error-count=1`), поэтому последующие шаги могут прочитать их даже при ошибке, если задано `continue-on-error: true`.

## Примеры

### Явное указание формата и версии

```yaml
- uses: thomasvincent/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Чтение выходных параметров

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

### Проверка нескольких файлов

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

### Проверка в Pull Request

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

## Модель безопасности

- **Без сетевых запросов во время проверки.** Схемы встроены в репозиторий. Единственный сетевой запрос — `npm install ajv-cli ajv-formats` на этапе настройки.
- **Без телеметрии.** Action не отправляет данные вовне и не собирает статистику.
- **Выполнение в контейнере задания.** Без загрузки образов Docker и без внешних сервисов.
- **Минимальные привилегии.** Требуется только разрешение `contents: read`.

Для большей надёжности закрепите конкретный полный SHA коммита:

```yaml
- uses: thomasvincent/validate-sbom-action@46e800d6e8da6a10d3dc8ab21baabb8f6e8320a0 # v1
```

## Совместимость

- Работает на `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Требует Node.js (предустановлен на всех раннерах, размещённых в GitHub).
- Требует `jq` (предустановлен на всех раннерах, размещённых в GitHub).
- Для self-hosted раннеров требуются Node.js >= 18 и jq в PATH.

## Обновление схем

Чтобы обновить встроенные схемы из upstream:

```bash
./scripts/update-schemas.sh
```

## Лицензия

Apache-2.0 — см. [LICENSE](../../../LICENSE).
