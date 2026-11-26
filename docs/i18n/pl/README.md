<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Polski** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · **Polski** · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Waliduj pliki SBOM względem oficjalnych schematów JSON CycloneDX i SPDX. W trybie offline. Bez wywołań sieciowych podczas walidacji.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Użycie

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Akcja automatycznie wykrywa format (CycloneDX lub SPDX) oraz wersję specyfikacji na podstawie pliku. Jeśli walidacja zakończy się niepowodzeniem, kończy działanie niezerowym kodem wyjścia.

## Parametry wejściowe

| Parametr | Wymagany | Domyślnie | Opis |
|-------|----------|---------|-------------|
| `input-file` | tak | -- | Ścieżka do pliku SBOM w formacie JSON |
| `format` | nie | `auto` | `cyclonedx`, `spdx` lub `auto` (wykrywanie na podstawie pliku) |
| `version` | nie | `auto` | Wersja specyfikacji (np. `1.6`, `2.3`) lub `auto` (wykrywanie na podstawie pliku) |

## Wartości wyjściowe

| Wyjście | Opis |
|--------|-------------|
| `valid` | `true`, jeśli SBOM przechodzi walidację schematu, w przeciwnym razie `false` |
| `format` | Wykryty format: `cyclonedx` lub `spdx` |
| `spec-version` | Wykryta wersja specyfikacji (np. `1.6`, `2.3`) |
| `error-count` | Przybliżona liczba błędów walidacji (0, gdy plik jest poprawny) |

## Obsługiwane formaty

| Format | Wersje |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Wyłącznie JSON. Pliki SBOM w formacie XML nie są obsługiwane.

## Tryby błędów

Akcja kończy działanie z kodem 1 i ustawia `valid=false` w następujących przypadkach:

| Warunek | Komunikat błędu |
|-----------|---------------|
| Plik nie istnieje | `Input file not found: <path>` |
| Plik nie jest poprawnym JSON-em | `Input file is not valid JSON: <path>` |
| Nie można wykryć formatu | `Unable to detect SBOM format` |
| Nie można wykryć wersji | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Brak schematu dla wykrytej wersji | `Schema file not found for <format> <version>` |
| Walidacja schematu kończy się błędem | Wynik błędu ajv-cli ze szczegółami |

Wszystkie ścieżki błędów zapisują wartości wyjściowe (`valid=false`, `error-count=1`) przed zakończeniem działania, dzięki czemu kolejne kroki mogą je odczytać nawet po błędzie przy użyciu `continue-on-error: true`.

## Przykłady

### Jawne określenie formatu i wersji

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Odczyt wartości wyjściowych

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

### Walidacja wielu plików

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

### Bramkowanie PR

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

## Model bezpieczeństwa

- **Brak wywołań sieciowych podczas walidacji.** Schematy są dołączone bezpośrednio do repozytorium. Jedynym wywołaniem sieciowym jest `npm install ajv-cli ajv-formats` podczas konfiguracji środowiska.
- **Brak telemetrii.** Akcja nie wysyła żadnych danych na zewnątrz ani ich nie gromadzi.
- **Uruchamiana w kontenerze zadania.** Bez pobierania obrazów Docker i bez usług zewnętrznych.
- **Zasada najmniejszych uprawnień.** Wymaga wyłącznie `contents: read`.

Dla większego poziomu bezpieczeństwa przypnij akcję do pełnego skrótu SHA commita:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Kompatybilność

- Działa na `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Wymaga Node.js (preinstalowanego na wszystkich runnerach hostowanych przez GitHub).
- Wymaga `jq` (preinstalowanego na wszystkich runnerach hostowanych przez GitHub).
- Runnery self-hosted wymagają Node.js >= 18 oraz jq w zmiennej PATH.

## Aktualizacja schematów

Aby zaktualizować dołączone schematy ze źródeł nadrzędnych:

```bash
./scripts/update-schemas.sh
```

## Licencja

Apache-2.0 -- zobacz [LICENSE](../../../LICENSE).
