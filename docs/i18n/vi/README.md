<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Tiếng Việt** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · **Tiếng Việt** · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Xác thực các tệp SBOM dựa trên lược đồ JSON chính thức của CycloneDX và SPDX. Hoạt động ngoại tuyến. Không thực hiện kết nối mạng tại thời điểm xác thực.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Hướng dẫn sử dụng

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Action tự động phát hiện định dạng (CycloneDX hoặc SPDX) và phiên bản đặc tả từ tệp đầu vào. Nó trả về mã thoát khác 0 nếu quá trình xác thực thất bại.

## Tham số đầu vào

| Tham số | Bắt buộc | Mặc định | Mô tả |
|-------|----------|---------|-------------|
| `input-file` | có | -- | Đường dẫn đến tệp SBOM JSON |
| `format` | không | `auto` | `cyclonedx`, `spdx` hoặc `auto` (tự phát hiện từ tệp) |
| `version` | không | `auto` | Phiên bản đặc tả (ví dụ: `1.6`, `2.3`) hoặc `auto` (tự phát hiện từ tệp) |

## Giá trị đầu ra

| Đầu ra | Mô tả |
|--------|-------------|
| `valid` | `true` nếu SBOM vượt qua bước xác thực lược đồ, ngược lại là `false` |
| `format` | Định dạng phát hiện được: `cyclonedx` hoặc `spdx` |
| `spec-version` | Phiên bản đặc tả phát hiện được (ví dụ: `1.6`, `2.3`) |
| `error-count` | Số lượng lỗi xác thực ước tính (bằng 0 khi hợp lệ) |

## Định dạng được hỗ trợ

| Định dạng | Phiên bản |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Chỉ hỗ trợ JSON. Không hỗ trợ SBOM định dạng XML.

## Các trường hợp lỗi

Action sẽ thoát với mã 1 và thiết lập `valid=false` trong các trường hợp sau:

| Điều kiện | Thông báo lỗi |
|-----------|---------------|
| Tệp không tồn tại | `Input file not found: <path>` |
| Tệp không phải JSON hợp lệ | `Input file is not valid JSON: <path>` |
| Không thể phát hiện định dạng | `Unable to detect SBOM format` |
| Không thể phát hiện phiên bản | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Không có lược đồ cho phiên bản phát hiện được | `Schema file not found for <format> <version>` |
| Xác thực lược đồ thất bại | Đầu ra lỗi chi tiết của ajv-cli |

Tất cả các nhánh lỗi đều ghi giá trị đầu ra (`valid=false`, `error-count=1`) trước khi thoát, giúp các bước phía sau vẫn đọc được ngay cả khi xảy ra lỗi cùng với `continue-on-error: true`.

## Ví dụ

### Chỉ định rõ định dạng và phiên bản

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Đọc giá trị đầu ra

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

### Xác thực nhiều tệp

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

### Kiểm soát PR

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

## Mô hình bảo mật

- **Không kết nối mạng tại thời điểm xác thực.** Các lược đồ được đóng gói sẵn trong kho lưu trữ. Kết nối mạng duy nhất là lệnh `npm install ajv-cli ajv-formats` trong quá trình thiết lập.
- **Không thu thập dữ liệu đo từ xa (telemetry).** Action không gửi dữ liệu ra ngoài hay thu thập thông tin.
- **Chạy trực tiếp trong container của job.** Không kéo ảnh Docker, không dùng dịch vụ bên ngoài.
- **Quyền hạn tối thiểu.** Chỉ yêu cầu quyền `contents: read`.

Để tăng mức độ đảm bảo an toàn, hãy ghim vào mã SHA đầy đủ của commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Khả năng tương thích

- Chạy trên `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Yêu cầu Node.js (được cài đặt sẵn trên mọi runner do GitHub lưu trữ).
- Yêu cầu `jq` (được cài đặt sẵn trên mọi runner do GitHub lưu trữ).
- Các runner tự lưu trữ (self-hosted) cần có Node.js >= 18 và jq trong PATH.

## Cập nhật lược đồ

Để cập nhật lại các lược đồ đóng gói sẵn từ nguồn thượng nguồn:

```bash
./scripts/update-schemas.sh
```

## Giấy phép

Apache-2.0 -- xem [LICENSE](../../../LICENSE).
