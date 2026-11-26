<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · **日本語** · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · **日本語** · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

SBOM ファイルを公式の CycloneDX および SPDX JSON スキーマに照らして検証します。オフラインで動作し、検証時にネットワーク通信は行いません。

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## 使用方法

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

このアクションは、ファイルからフォーマット（CycloneDX または SPDX）と仕様バージョンを自動検出します。検証に失敗した場合は、0 以外の終了コードで終了します。

## 入力

| 入力 | 必須 | デフォルト | 説明 |
|-------|----------|---------|-------------|
| `input-file` | はい | -- | SBOM JSON ファイルへのパス |
| `format` | いいえ | `auto` | `cyclonedx`、`spdx`、または `auto`（ファイルから自動検出） |
| `version` | いいえ | `auto` | 仕様バージョン（例: `1.6`、`2.3`）または `auto`（ファイルから自動検出） |

## 出力

| 出力 | 説明 |
|--------|-------------|
| `valid` | SBOM がスキーマ検証を通過した場合は `true`、それ以外は `false` |
| `format` | 検出されたフォーマット: `cyclonedx` または `spdx` |
| `spec-version` | 検出された仕様バージョン（例: `1.6`、`2.3`） |
| `error-count` | 検証エラーのおおよその件数（有効な場合は 0） |

## サポート対象フォーマット

| フォーマット | バージョン |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON のみ対応しています。XML 形式の SBOM はサポートされていません。

## エラー条件

次の場合、アクションは終了コード 1 で終了し、`valid=false` を設定します。

| 条件 | エラーメッセージ |
|-----------|---------------|
| ファイルが存在しない | `Input file not found: <path>` |
| ファイルが有効な JSON ではない | `Input file is not valid JSON: <path>` |
| フォーマットを検出できない | `Unable to detect SBOM format` |
| バージョンを検出できない | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| 検出されたバージョンに対応するスキーマがない | `Schema file not found for <format> <version>` |
| スキーマ検証に失敗した | 詳細を含む ajv-cli のエラー出力 |

## 使用例

### フォーマットとバージョンを明示的に指定する

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### 出力を読み取る

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

### 複数のファイルを検証する

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

### PR でのゲートチェック

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

## セキュリティモデル

- **検証時のネットワーク通信なし。** スキーマはリポジトリ内にベンダー同梱されています。ネットワーク通信が発生するのはセットアップ時の `npm install ajv-cli ajv-formats` のみです。
- **テレメトリなし。** このアクションは外部への通信やデータ収集を行いません。
- **ジョブコンテナ内で実行。** Docker イメージのプルや外部サービスは不要です。
- **最小権限。** 必要な権限は `contents: read` のみです。

より高い安全性を確保するには、完全なコミット SHA で固定してください。

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## 互換性

- `ubuntu-latest`、`ubuntu-22.04`、`ubuntu-24.04` で動作します。
- Node.js が必要です（すべての GitHub ホストランナーにプリインストール済み）。
- `jq` が必要です（すべての GitHub ホストランナーにプリインストール済み）。
- セルフホストランナーでは、Node.js >= 18 および PATH 上の jq が必要です。

## スキーマの更新

アップストリームから同梱スキーマを更新するには次を実行します。

```bash
./scripts/update-schemas.sh
```

## ライセンス

Apache-2.0 -- 詳細は [LICENSE](../../../LICENSE) を参照してください。
