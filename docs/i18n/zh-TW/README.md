<!-- translations:start -->
**Languages:** [English](../../../README.md) · **繁體中文** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · **繁體中文** · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

依據官方 CycloneDX 與 SPDX JSON Schema 驗證 SBOM 檔案。完全離線運作，驗證期間不進行任何網路呼叫。

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## 使用方式

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

此 Action 會自動從檔案偵測格式（CycloneDX 或 SPDX）與規格版本。若驗證失敗，將以非零結束碼結束。

## 輸入參數

| 輸入參數 | 必填 | 預設值 | 說明 |
|-------|----------|---------|-------------|
| `input-file` | 是 | -- | SBOM JSON 檔案的路徑 |
| `format` | 否 | `auto` | `cyclonedx`、`spdx` 或 `auto`（從檔案自動偵測） |
| `version` | 否 | `auto` | 規格版本（例如 `1.6`、`2.3`）或 `auto`（從檔案自動偵測） |

## 輸出參數

| 輸出參數 | 說明 |
|--------|-------------|
| `valid` | 若 SBOM 通過 Schema 驗證則為 `true`，否則為 `false` |
| `format` | 偵測到的格式：`cyclonedx` 或 `spdx` |
| `spec-version` | 偵測到的規格版本（例如 `1.6`、`2.3`） |
| `error-count` | 大約的驗證錯誤數量（驗證通過時為 0） |

## 支援的格式

| 格式 | 版本 |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

僅支援 JSON。不支援 XML 格式的 SBOM。

## 失敗模式

在以下情況中，此 Action 會以結束碼 1 結束並設定 `valid=false`：

| 條件 | 錯誤訊息 |
|-----------|---------------|
| 檔案不存在 | `Input file not found: <path>` |
| 檔案不是有效的 JSON | `Input file is not valid JSON: <path>` |
| 無法偵測格式 | `Unable to detect SBOM format` |
| 無法偵測版本 | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| 找不到對應偵測版本的 Schema | `Schema file not found for <format> <version>` |
| Schema 驗證失敗 | 附帶詳細資訊的 ajv-cli 錯誤輸出 |

所有失敗路徑都會在結束前寫入輸出（`valid=false`、`error-count=1`），因此即使在失敗時，搭配 `continue-on-error: true` 的下游步驟仍可讀取這些輸出值。

## 範例

### 明確指定格式與版本

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### 讀取輸出

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

### 驗證多個檔案

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

### PR 閘道檢查

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

## 安全模型

- **驗證期間不進行任何網路呼叫。** Schema 已內嵌（vendored）於儲存庫中。唯一的網路呼叫是在環境設定階段執行的 `npm install ajv-cli ajv-formats`。
- **無遙測資料。** 此 Action 不會回傳連線或收集資料。
- **於作業容器內執行。** 無需拉取 Docker 映像檔，也無需外部服務。
- **最小權限原則。** 僅需要 `contents: read` 權限。

若需要更高的安全保證，請固定（pin）至完整的 commit SHA：

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## 相容性

- 可執行於 `ubuntu-latest`、`ubuntu-22.04`、`ubuntu-24.04`。
- 需要 Node.js（已預先安裝於所有 GitHub 託管的 runner）。
- 需要 `jq`（已預先安裝於所有 GitHub 託管的 runner）。
- 自行託管的 runner 需要 Node.js >= 18 且在 PATH 中具備 jq。

## Schema 更新

若要從上游重新同步內嵌的 Schema：

```bash
./scripts/update-schemas.sh
```

## 授權

Apache-2.0 -- 請參閱 [LICENSE](../../../LICENSE)。
