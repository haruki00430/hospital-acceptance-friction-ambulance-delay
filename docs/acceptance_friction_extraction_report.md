# JFT-02 Phase P1 extraction report

## Execution scope

Executed package: JFT02_Acceptance_Friction_Extraction_Package_v1_0.zip  
Source agency: Fire and Disaster Management Agency (FDMA), Japan  
Official PDFs downloaded: 11  
Target years: 2014-2024  
Target geography: 47 prefectures  
Target table: ?????????????????????????2?  
Target population: ?????????????, excluding interfacility transfers as specified in the package manifest.

## Extracted fields

- analysis_population_n: table column ?
- inquiries_ge4_n: table column 4???
- inquiries_ge4_share_reported_pct: printed ???
- inquiries_ge4_share_calculated_pct: 100 * inquiries_ge4_n / analysis_population_n
- rounding_difference_pp: calculated percentage minus reported percentage

## Method

Official PDFs were downloaded from the URLs in official_source_manifest.csv. SHA-256 checksums are recorded in SHA256SUMS.txt. The target table page was located using the package manifest page mapping and the table header. Values were extracted from embedded PDF text tables without OCR. Target pages were also rendered to PNG under target_page_renders for audit support. Annual national totals were parsed from the PDF total row and reconciled against prefecture sums.

## QA result

Validation status: PASS  
Rows: 517  
Years: 11  
Prefectures: 47  
Maximum absolute rounding difference: 0.049864 percentage points  
Annual denominator totals match: True  
Annual numerator totals match: True  
All rows double-check status: True

## Annual total reconciliation

| Year | PDF denominator | Prefecture denominator sum | PDF ge4 numerator | Prefecture ge4 sum | Match |
|---:|---:|---:|---:|---:|:---:|
| 2014 | 439547 | 439547 | 14114 | 14114 | yes |
| 2015 | 431642 | 431642 | 11754 | 11754 | yes |
| 2016 | 440106 | 440106 | 10039 | 10039 | yes |
| 2017 | 453618 | 453618 | 9834 | 9834 | yes |
| 2018 | 459167 | 459167 | 10861 | 10861 | yes |
| 2019 | 456973 | 456973 | 11067 | 11067 | yes |
| 2020 | 440136 | 440136 | 12998 | 12998 | yes |
| 2021 | 450378 | 450378 | 19174 | 19174 | yes |
| 2022 | 478840 | 478840 | 34580 | 34580 | yes |
| 2023 | 477749 | 477749 | 30069 | 30069 | yes |
| 2024 | 482778 | 482778 | 26020 | 26020 | yes |

## Stop-condition review

No stop condition was triggered. No prefecture values were left missing. No annual national-total mismatch was detected. No material definition deviation was detected in the completed definition-continuity log. Reported and calculated percentages were consistent within the required rounding tolerance.

## Completion declaration

PHASE P1 COMPLETE - 2014-2024 ACCEPTANCE-FRICTION PANEL VERIFIED
