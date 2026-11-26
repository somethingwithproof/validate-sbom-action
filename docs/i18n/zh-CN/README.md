<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · **简体中文** · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · **简体中文** · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

依据官方 CycloneDX 和 SPDX JSON Schema 验证 SBOM 文件。离线运行，验证时无网络调用。

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## 使用说明

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

该 Action 会自动从文件中检测格式（CycloneDX 或 SPDX）和规范版本。如果验证失败，将以非零退出码退出。

## 输入

| 输入 | 必填 | 默认值 | 说明 |
|-------|----------|---------|-------------|
| `input-file` | 是 | -- | SBOM JSON 文件路径 |
| `format` | 否 | `auto` | `cyclonedx`、`spdx` 或 `auto`（从文件自动检测） |
| `version` | 否 | `auto` | 规范版本（例如 `1.6`、`2.3`）或 `auto`（从文件自动检测） |

## 输出

| 输出 | 说明 |
|--------|-------------|
| `valid` | 如果 SBOM 通过 Schema 验证则为 `true`，否则为 `false` |
| `format` | 检测到的格式：`cyclonedx` 或 `spdx` |
| `spec-version` | 检测到的规范版本（例如 `1.6`、`2.3`） |
| `error-count` | 大致的验证错误数量（验证通过时为 0） |

## 支持的格式

| 格式 | 版本 |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

仅支持 JSON。不支持 XML 格式的 SBOM。

## 失败模式

在以下情况下，该 Action 会以退出码 1 退出并设置 `valid=false`：

| 条件 | 错误信息 |
|-----------|---------------|
| 文件不存在 | `Input file not found: <path>` |
| 文件不是有效的 JSON | `Input file is not valid JSON: <path>` |
| 无法检测格式 | `Unable to detect SBOM format` |
| 无法检测版本 | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| 未找到检测到版本对应的 Schema | `Schema file not found for <format> <version>` |
| Schema 验证失败 | 包含详细信息的 ajv-cli 错误输出 |

所有失败路径都会在退出前写入输出（`valid=false`、`error-count=1`），以便下游步骤在设置 `continue-on-error: true` 时即便失败也能读取这些输出。

## 示例

### 显式指定格式和版本

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### 读取输出

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

### 验证多个文件

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

### PR 门禁

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

- **验证时无网络调用。** Schema 文件已内置在代码仓库中。唯一的网络调用是在初始化阶段执行 `npm install ajv-cli ajv-formats`。
- **无遥测。** 该 Action 不会回传数据或收集信息。
- **在任务容器中运行。** 无需拉取 Docker 镜像，不依赖外部服务。
- **最小权限。** 仅需 `contents: read` 权限。

为获得更高的安全保障，可固定到完整的提交 SHA：

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## 兼容性

- 支持在 `ubuntu-latest`、`ubuntu-22.04`、`ubuntu-24.04` 上运行。
- 需要 Node.js（所有 GitHub 托管的运行器均已预装）。
- 需要 `jq`（所有 GitHub 托管的运行器均已预装）。
- 自托管运行器需要在 PATH 中安装 Node.js >= 18 和 jq。

## Schema 更新

要从上游刷新内置的 Schema 文件：

```bash
./scripts/update-schemas.sh
```

## 许可证

Apache-2.0 —— 详见 [LICENSE](../../../LICENSE)。
