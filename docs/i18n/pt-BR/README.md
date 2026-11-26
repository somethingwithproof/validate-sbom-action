<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · **Português (BR)** · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · **Português (BR)** · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Valide arquivos SBOM em relação aos esquemas JSON oficiais do CycloneDX e do SPDX. Offline. Sem chamadas de rede durante a validação.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Uso

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

A action detecta automaticamente o formato (CycloneDX ou SPDX) e a versão da especificação a partir do arquivo. Ela encerra com código diferente de zero se a validação falhar.

## Entradas

| Entrada | Obrigatória | Padrão | Descrição |
|-------|----------|---------|-------------|
| `input-file` | sim | -- | Caminho para o arquivo JSON do SBOM |
| `format` | não | `auto` | `cyclonedx`, `spdx` ou `auto` (detectar a partir do arquivo) |
| `version` | não | `auto` | Versão da especificação (ex.: `1.6`, `2.3`) ou `auto` (detectar a partir do arquivo) |

## Saídas

| Saída | Descrição |
|--------|-------------|
| `valid` | `true` se o SBOM passar na validação de esquema, `false` caso contrário |
| `format` | Formato detectado: `cyclonedx` ou `spdx` |
| `spec-version` | Versão da especificação detectada (ex.: `1.6`, `2.3`) |
| `error-count` | Número aproximado de erros de validação (0 quando válido) |

## Formatos suportados

| Formato | Versões |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Apenas JSON. SBOMs em XML não são suportados.

## Modos de falha

A action encerra com código 1 e define `valid=false` nestes casos:

| Condição | Mensagem de erro |
|-----------|---------------|
| O arquivo não existe | `Input file not found: <path>` |
| O arquivo não é um JSON válido | `Input file is not valid JSON: <path>` |
| Não é possível detectar o formato | `Unable to detect SBOM format` |
| Não é possível detectar a versão | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Não há esquema para a versão detectada | `Schema file not found for <format> <version>` |
| A validação de esquema falha | Saída de erro do ajv-cli com detalhes |

## Exemplos

### Formato e versão explícitos

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Leitura das saídas

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

### Validação de múltiplos arquivos

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

### Validação obrigatória em PR

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

## Modelo de segurança

- **Sem chamadas de rede durante a validação.** Os esquemas estão embutidos (vendored) no repositório. A única chamada de rede é `npm install ajv-cli ajv-formats` durante a preparação.
- **Sem telemetria.** A action não envia dados externos nem coleta informações.
- **Execução no contêiner do job.** Sem pull de imagem Docker e sem serviços externos.
- **Privilégio mínimo.** Requer apenas `contents: read`.

Para maior segurança, fixe a referência em um SHA completo de commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Compatibilidade

- Executa em `ubuntu-latest`, `ubuntu-22.04` e `ubuntu-24.04`.
- Requer Node.js (pré-instalado em todos os runners hospedados no GitHub).
- Requer `jq` (pré-instalado em todos os runners hospedados no GitHub).
- Runners auto-hospedados precisam de Node.js >= 18 e jq no PATH.

## Atualização de esquemas

Para atualizar os esquemas embutidos a partir do upstream:

```bash
./scripts/update-schemas.sh
```

## Licença

Apache-2.0 -- consulte [LICENSE](../../../LICENSE).
