<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Bahasa Indonesia** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · **Bahasa Indonesia**
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Memvalidasi berkas SBOM terhadap skema JSON resmi CycloneDX dan SPDX. Luring. Tanpa panggilan jaringan saat validasi.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Penggunaan

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Action ini mendeteksi otomatis format (CycloneDX atau SPDX) dan versi spesifikasi dari berkas. Action keluar dengan kode bukan nol jika validasi gagal.

## Masukan

| Masukan | Wajib | Default | Deskripsi |
|-------|----------|---------|-------------|
| `input-file` | ya | -- | Jalur ke berkas JSON SBOM |
| `format` | tidak | `auto` | `cyclonedx`, `spdx`, atau `auto` (deteksi dari berkas) |
| `version` | tidak | `auto` | Versi spesifikasi (mis., `1.6`, `2.3`) atau `auto` (deteksi dari berkas) |

## Keluaran

| Keluaran | Deskripsi |
|--------|-------------|
| `valid` | `true` jika SBOM lolos validasi skema, `false` jika tidak |
| `format` | Format yang terdeteksi: `cyclonedx` atau `spdx` |
| `spec-version` | Versi spesifikasi yang terdeteksi (mis., `1.6`, `2.3`) |
| `error-count` | Perkiraan jumlah kesalahan validasi (0 jika valid) |

## Format yang Didukung

| Format | Versi |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Hanya JSON. SBOM XML tidak didukung.

## Mode Kegagalan

Action keluar dengan kode 1 dan menetapkan `valid=false` pada kasus-kasus berikut:

| Kondisi | Pesan kesalahan |
|-----------|---------------|
| Berkas tidak ditemukan | `Input file not found: <path>` |
| Berkas bukan JSON yang valid | `Input file is not valid JSON: <path>` |
| Format tidak dapat dideteksi | `Unable to detect SBOM format` |
| Versi tidak dapat dideteksi | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Tidak ada skema untuk versi yang terdeteksi | `Schema file not found for <format> <version>` |
| Validasi skema gagal | Keluaran kesalahan ajv-cli beserta rinciannya |

## Contoh

### Format dan versi eksplisit

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Membaca keluaran

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

### Memvalidasi beberapa berkas

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

### Gerbang PR

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

## Model Keamanan

- **Tanpa panggilan jaringan saat validasi.** Skema disertakan langsung (vendored) di dalam repositori. Satu-satunya panggilan jaringan adalah `npm install ajv-cli ajv-formats` saat penyiapan.
- **Tanpa telemetri.** Action ini tidak menghubungi server eksternal maupun mengumpulkan data.
- **Berjalan di dalam kontainer job.** Tanpa penarikan Docker, tanpa layanan eksternal.
- **Hak akses minimum.** Hanya memerlukan `contents: read`.

Untuk jaminan keamanan lebih tinggi, sematkan ke SHA commit lengkap:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Kompatibilitas

- Berjalan pada `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Memerlukan Node.js (sudah terpasang di semua runner yang dihosting GitHub).
- Memerlukan `jq` (sudah terpasang di semua runner yang dihosting GitHub).
- Runner yang dihosting sendiri memerlukan Node.js >= 18 dan jq di dalam PATH.

## Pembaruan Skema

Untuk memperbarui skema vendored dari hulu:

```bash
./scripts/update-schemas.sh
```

## Lisensi

Apache-2.0 -- lihat [LICENSE](../../../LICENSE).
