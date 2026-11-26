<!-- translations:start -->
**Languages:** [English](../../../README.md) · **isiZulu** · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Português (BR)](../pt-BR/README.md) · [Русский](../ru/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md)

<details>
<summary>All 45 languages (Tier 1, Africa, Asia)</summary>

- **Tier 1:** [English](../../../README.md) · [Deutsch](../de/README.md) · [Español](../es/README.md) · [Français](../fr/README.md) · [Italiano](../it/README.md) · [Português (BR)](../pt-BR/README.md) · [Nederlands](../nl/README.md) · [Русский](../ru/README.md) · [Українська](../uk/README.md) · [日本語](../ja/README.md) · [한국어](../ko/README.md) · [简体中文](../zh-CN/README.md) · [繁體中文](../zh-TW/README.md) · [العربية](../ar/README.md) · [हिन्दी](../hi/README.md) · [Polski](../pl/README.md) · [Türkçe](../tr/README.md) · [Svenska](../sv/README.md) · [Tiếng Việt](../vi/README.md) · [Bahasa Indonesia](../id/README.md)
- **Africa:** [Afrikaans](../af-ZA/README.md) · [አማርኛ](../am-ET/README.md) · [العربية (مصر)](../ar-EG/README.md) · [العربية (المغرب)](../ar-MA/README.md) · [Français (Maroc)](../fr-MA/README.md) · [Français (Sénégal)](../fr-SN/README.md) · [Hausa](../ha-NG/README.md) · [Igbo](../ig-NG/README.md) · [Malagasy](../mg-MG/README.md) · [Kinyarwanda](../rw-RW/README.md) · [Soomaali](../so-SO/README.md) · [Kiswahili](../sw-KE/README.md) · [isiXhosa](../xh-ZA/README.md) · [Yorùbá](../yo-NG/README.md) · **isiZulu**
- **Asia:** [বাংলা](../bn/README.md) · [فارسی](../fa/README.md) · [עברית](../he/README.md) · [मराठी](../mr/README.md) · [தமிழ்](../ta/README.md) · [తెలుగు](../te/README.md) · [ไทย](../th/README.md) · [اردو](../ur/README.md) · [Bahasa Melayu](../ms/README.md) · [Filipino](../fil/README.md)

</details>
<!-- translations:end -->

# validate-sbom-action

Qinisekisa amafayela e-SBOM ngokubheka ama-schema asemthethweni e-JSON e-CycloneDX ne-SPDX. Ngaphandle kwe-inthanethi (offline). Azikho izicelo zenethiwekhi ngesikhathi sokuqinisekisa.

[![CI](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml/badge.svg)](https://github.com/somethingwithproof/validate-sbom-action/actions/workflows/ci.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=somethingwithproof_validate-sbom-action&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=somethingwithproof_validate-sbom-action)
[![Release](https://img.shields.io/github/v/release/somethingwithproof/validate-sbom-action)](https://github.com/somethingwithproof/validate-sbom-action/releases)
[![GitHub Marketplace](https://img.shields.io/badge/marketplace-validate--sbom--action-blue?logo=github)](https://github.com/marketplace/actions/validate-sbom)
[![License: Apache-2.0](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](../../../LICENSE)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/somethingwithproof/validate-sbom-action/badge)](https://scorecard.dev/viewer/?uri=github.com/somethingwithproof/validate-sbom-action)

## Ukusetshenziswa

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: sbom.json
```

Lesi senzo (action) sibona ngokuzenzakalelayo ifomethi (i-CycloneDX noma i-SPDX) nenguqulo yokucaciswa (spec version) kusuka efayeleni. Siphuma ngekhodi engeyona iqanda (non-zero) uma ukuqinisekiswa kwehluleka.

## Okufakwayo

| Okufakwayo | Kuyadingeka | Okuzenzakalelayo | Incazelo |
|-------|----------|---------|-------------|
| `input-file` | yebo | -- | Indlela eya efayeleni le-SBOM JSON |
| `format` | cha | `auto` | `cyclonedx`, `spdx`, noma `auto` (bona kusuka efayeleni) |
| `version` | cha | `auto` | Inguqulo yokucaciswa (isib., `1.6`, `2.3`) noma `auto` (bona kusuka efayeleni) |

## Okuphumayo

| Okuphumayo | Incazelo |
|--------|-------------|
| `valid` | `true` uma i-SBOM iphasa ukuqinisekiswa kwe-schema, `false` kungenjalo |
| `format` | Ifomethi etholiwe: `cyclonedx` noma `spdx` |
| `spec-version` | Inguqulo yokucaciswa etholiwe (isib., `1.6`, `2.3`) |
| `error-count` | Inani elilinganiselwe lamaphutha okuqinisekisa (0 uma kuqinisekisiwe) |

## Amafomethi Asekelwayo

| Ifomethi | Izinguqulo |
|--------|----------|
| CycloneDX | 1.4, 1.5, 1.6, 1.7 |
| SPDX | 2.2, 2.3 |

I-JSON kuphela. Ama-SBOM e-XML awasekelwa.

## Izindlela Zokwehluleka

Lesi senzo siphuma ngekhodi engu-1 futhi sisetha `valid=false` kulezi zimo:

| Isimo | Umlayezo wephutha |
|-----------|---------------|
| Ifayela alikho | `Input file not found: <path>` |
| Ifayela aliyona i-JSON esebenzayo | `Input file is not valid JSON: <path>` |
| Ifomethi ayikwazi ukubonakala | `Unable to detect SBOM format` |
| Inguqulo ayikwazi ukubonakala | `Unable to detect CycloneDX specVersion` / `Unable to detect SPDX version` |
| Ayikho i-schema yenguqulo etholiwe | `Schema file not found for <format> <version>` |
| Ukuqinisekiswa kwe-schema kuyehluleka | Okuphumayo kwephutha kwe-ajv-cli okunemininingwane |

Zonke izindlela zokwehluleka zibhala okuphumayo (`valid=false`, `error-count=1`) ngaphambi kokuphuma, ukuze izinyathelo ezilandelayo zikwazi ukukufunda ngisho noma kwehlulekile nge-`continue-on-error: true`.

## Izibonelo

### Ifomethi nenguqulo ecacisiwe

```yaml
- uses: somethingwithproof/validate-sbom-action@v1
  with:
    input-file: cyclonedx-sbom.json
    format: cyclonedx
    version: '1.6'
```

### Funda okuphumayo

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

### Qinisekisa amafayela amaningi

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

### Ukuvimba ama-PR (PR gating)

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

## Imodeli Yokuvikeleka

- **Azikho izicelo zenethiwekhi ngesikhathi sokuqinisekisa.** Ama-schema afakwe ngaphakathi enqolobaneni. Okuwukuphela kwesicelo senethiwekhi yi-`npm install ajv-cli ajv-formats` ngesikhathi sokusetha.
- **Ayikho i-telemetry.** Lesi senzo asithumeli ulwazi ngaphandle noma siqoqe idatha.
- **Sisebenza ku-container yomsebenzi.** Akukho ukudonswa kwe-Docker, azikho izinsizakalo zangaphandle.
- **Izimvume ezincane kakhulu.** Sidinga kuphela i-`contents: read`.

Ukuze uthole isiqinisekiso esiphezulu, phina ku-SHA egcwele ye-commit:

```yaml
- uses: somethingwithproof/validate-sbom-action@691aeb90ba3a03910cbc14b618f3c8046e165f0b # v1
```

## Ukuhambisana

- Sisebenza ku-`ubuntu-latest`, `ubuntu-22.04`, `ubuntu-24.04`.
- Sidinga i-Node.js (efakwe kusenesikhathi kuwo wonke ama-runner asingathwe yi-GitHub).
- Sidinga i-`jq` (efakwe kusenesikhathi kuwo wonke ama-runner asingathwe yi-GitHub).
- Ama-runner azisingathele adinga i-Node.js >= 18 kanye ne-jq ku-PATH.

## Ukubuyekezwa Kwe-Schema

Ukuvuselela ama-schema afakiwe kusuka ku-upstream:

```bash
./scripts/update-schemas.sh
```

## Ilayisense

I-Apache-2.0 -- bheka i-[LICENSE](../../../LICENSE).
