<!-- translations:start -->
**Languages:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · **한국어** · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · **한국어** · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

공식 CycloneDX 및 SPDX JSON 스키마를 기준으로 SBOM 파일을 검증합니다. 오프라인으로 동작하며 검증 시점에 네트워크 호출을 수행하지 않습니다.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## 사용법

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

이 액션은 파일에서 형식(CycloneDX 또는 SPDX)과 사양 버전을 자동으로 감지합니다. 검증에 실패하면 0이 아닌 종료 코드로 종료됩니다.

## 입력값

| 입력값 | 필수 여부 | 기본값 | 설명 |
|-------|----------|---------|-------------|
| `input-file` | 예 | -- | SBOM JSON 파일 경로 |
| `format` | 아니요 | `auto` | `cyclonedx`, `spdx`, 또는 `auto` (파일에서 자동 감지) |
| `version` | 아니요 | `auto` | 사양 버전(예: `1.6`, `2.3`) 또는 `auto` (파일에서 자동 감지) |

## 출력값

| 출력값 | 설명 |
|--------|-------------|
| `valid` | SBOM이 스키마 검증을 통과하면 `true`, 그렇지 않으면 `false` |
| `format` | 감지된 형식: `cyclonedx` 또는 `spdx` |
| `spec-version` | 감지된 사양 버전(예: `1.6`, `2.3`) |
| `error-count` | 대략적인 검증 오류 개수(유효한 경우 0) |

## 지원 형식

| 형식 | 버전 |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

JSON 형식만 지원합니다. XML SBOM은 지원하지 않습니다.

## 실패 조건

다음과 같은 경우 액션은 종료 코드 1로 종료하고 `valid=false`를 설정합니다:

| 조건 | 오류 메시지 |
|-----------|---------------|
| 파일이 존재하지 않음 | `Input file not found: <path>` |
| 파일이 유효한 JSON이 아님 | `Input file is not valid JSON: <path>` |
| 형식을 감지할 수 없음 | `Unable to detect SBOM format` |
| 버전을 감지할 수 없음 | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| 감지된 버전에 해당하는 스키마 없음 | `Schema file not found for <format> <version>` |
| 스키마 검증 실패 | 세부 정보가 포함된 ajv-cli 오류 출력 |

모든 실패 경로는 종료 전에 출력값(`valid=false`, `error-count=1`)을 기록하므로 `continue-on-error: true`를 설정하면 실패 시에도 후속 단계에서 이를 읽을 수 있습니다.

## 예제

### 형식과 버전 명시적 지정

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### 출력값 읽기

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

### 여러 파일 검증

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

### PR 게이팅

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

## 보안 모델

- **검증 시점 네트워크 호출 없음.** 스키마는 저장소에 벤더링되어 있습니다. 유일한 네트워크 호출은 설정 단계의 `npm install ajv-cli ajv-formats`입니다.
- **텔레메트리 없음.** 이 액션은 외부로 정보를 전송하거나 데이터를 수집하지 않습니다.
- **작업 컨테이너 내에서 실행.** Docker 이미지를 풀하거나 외부 서비스를 사용하지 않습니다.
- **최소 권한.** `contents: read` 권한만 필요합니다.

보안 보증을 높이려면 전체 커밋 SHA로 버전을 고정하세요:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## 호환성

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`에서 실행됩니다.
- Node.js가 필요합니다(모든 GitHub 호스팅 러너에 사전 설치됨).
- `jq`가 필요합니다(모든 GitHub 호스팅 러너에 사전 설치됨).
- 자체 호스팅 러너에는 Node.js >= 18 및 PATH에 포함된 jq가 필요합니다.

## 스키마 업데이트

업스트림에서 벤더링된 스키마를 갱신하려면 다음 명령을 실행하세요:

```bash
./scripts/update-schemas.sh
```

## 라이선스

Apache-2.0 -- [LICENSE](../../../LICENSE)를 참고하세요.
