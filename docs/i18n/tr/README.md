<!-- translations:start -->
**Languages:** [English](../../../README.md) · **Türkçe** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 48 languages (Tier 1, Africa, Asia, Balkans)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · **Türkçe** · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · [isiZulu](../zu-ZA/README.md)
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)
- **Balkans:** [Bosanski](../bs/README.md) · [Hrvatski](../hr/README.md) · [Српски](../sr/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

SBOM dosyalarını resmi CycloneDX ve SPDX JSON şemalarına göre doğrulayın. Çevrimdışı. Doğrulama sırasında ağ çağrısı yapılmaz.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Kullanım

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Eylem, dosyadan biçimi (CycloneDX veya SPDX) ve belirtim sürümünü otomatik olarak algılar. Doğrulama başarısız olursa sıfırdan farklı bir çıkış koduyla sonlanır.

## Girdiler

| Girdi | Zorunlu | Varsayılan | Açıklama |
|-------|----------|---------|-------------|
| `input-file` | evet | -- | SBOM JSON dosyasının yolu |
| `format` | hayır | `auto` | `cyclonedx`, `spdx` veya `auto` (dosyadan algıla) |
| `version` | hayır | `auto` | Belirtim sürümü (ör. `1.6`, `2.3`) veya `auto` (dosyadan algıla) |

## Çıktılar

| Çıktı | Açıklama |
|--------|-------------|
| `valid` | SBOM şema doğrulamasından geçerse `true`, aksi takdirde `false` |
| `format` | Algılanan biçim: `cyclonedx` veya `spdx` |
| `spec-version` | Algılanan belirtim sürümü (ör. `1.6`, `2.3`) |
| `error-count` | Yaklaşık doğrulama hatası sayısı (geçerli olduğunda 0) |

## Desteklenen Biçimler

| Biçim | Sürümler |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

Yalnızca JSON. XML SBOM dosyaları desteklenmez.

## Hata Durumları

Eylem şu durumlarda 1 çıkış koduyla sonlanır ve `valid=false` değerini ayarlar:

| Koşul | Hata mesajı |
|-----------|---------------|
| Dosya mevcut değil | `Input file not found: <path>` |
| Dosya geçerli JSON değil | `Input file is not valid JSON: <path>` |
| Biçim algılanamıyor | `Unable to detect SBOM format` |
| Sürüm algılanamıyor | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Algılanan sürüm için şema yok | `Schema file not found for <format> <version>` |
| Şema doğrulaması başarısız | Ayrıntılarla birlikte ajv-cli hata çıktısı |

Tüm hata yolları çıkış yapmadan önce çıktıları (`valid=false`, `error-count=1`) yazar; böylece sonraki adımlar `continue-on-error: true` ile hata durumunda bile bunları okuyabilir.

## Örnekler

### Açık biçim ve sürüm

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Çıktıları okuma

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

### Birden fazla dosyayı doğrulama

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

### PR denetimi

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

## Güvenlik Modeli

- **Doğrulama sırasında ağ çağrısı yoktur.** Şemalar depoya gömülüdür. Tek ağ çağrısı kurulum sırasındaki `npm install ajv-cli ajv-formats` komutudur.
- **Telemetri yoktur.** Eylem dışarıya veri göndermez veya veri toplamaz.
- **İş kapsayıcısında çalışır.** Docker görüntüsü indirilmez, harici servis kullanılmaz.
- **En az yetki ilkesi.** Yalnızca `contents: read` iznini gerektirir.

Daha yüksek güvence için tam commit SHA'sına sabitleyin:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Uyumluluk

- `ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04` üzerinde çalışır.
- Node.js gerektirir (GitHub tarafından barındırılan tüm çalıştırıcılarda önceden kuruludur).
- `jq` gerektirir (GitHub tarafından barındırılan tüm çalıştırıcılarda önceden kuruludur).
- Kendi barındırdığınız çalıştırıcılarda PATH içinde Node.js >= 18 ve jq bulunmalıdır.

## Şema Güncellemeleri

Gömülü şemaları yukarı akıştan yenilemek için:

```bash
./scripts/update-schemas.sh
```

## Lisans

Apache-2.0 -- [LICENSE](../../../LICENSE) dosyasına bakın.
