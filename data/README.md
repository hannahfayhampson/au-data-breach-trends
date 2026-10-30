# 📥 Data guide

## Source

Office of the Australian Information Commissioner (OAIC) Notifiable Data Breaches (NDB) reports.

- **2018 to mid-2019:** reports were published **quarterly**
- **Later reports:** published **half-yearly** (January–June and July–December)

Quarterly figures are combined into half-years during cleaning so every period compares fairly.

## Coverage & known gaps

| Period | Source | Notes |
|---|---|---|
| Feb–Mar 2018 | Quarterly statistics report | Scheme began **22 Feb 2018**, so this is ~6 weeks. Figures come from chart descriptions. |
| Apr–Jun 2018 | Quarterly statistics report | Source of breaches published as **percentages only**. |
| Jul 2018 – Jun 2024 | Quarterly, then half-yearly reports | Full detail. Source counts sum exactly to the total in every period. |
| Jan–Jun 2023 | Half-yearly report | Malicious and system fault published as **percentages only** (human error count available). |
| Jul–Dec 2024 | Half-yearly report | Source counts sum to 586 of 595: 9 breaches not attributed to a source. Includes time-to-identify/notify and sector-by-source detail. |
| Jan–Jun 2025 | OAIC blog (no full report) | **Headline figures only.** Malicious + human error = 501 of 532; system fault not published. |
| Jul–Dec 2025 | data.gov.au dataset (XLSX) | **Not yet added.** |

Not every report breaks down every cyber incident method as a count (some give percentages only), so `cyber_incident_breakdown` has gaps in some periods. Gaps are left as missing rows rather than zeros.

**Collection method:** Jul–Dec 2024 figures were read directly from the report. Other periods were extracted from the OAIC report web pages and checked by reconciling totals: source counts against total notifications, and malicious subcategories against the malicious total.

## `raw/oaic_ndb_raw.csv`

Figures are entered by hand from each report, **one number per row** (a "long" or "tidy" format).
This keeps the file flexible, because the categories the OAIC reports change slightly over time.

| Column | What goes in it | Example |
|---|---|---|
| `period_start` | First day of the reporting period (YYYY-MM-DD) | `2024-07-01` |
| `period_end` | Last day of the reporting period (YYYY-MM-DD) | `2024-12-31` |
| `frequency` | `quarterly` or `half-yearly` | `half-yearly` |
| `metric` | What is being measured (see list below) | `breaches_by_source` |
| `category` | The main group within that metric | `malicious_or_criminal_attack` |
| `subcategory` | A finer breakdown, if the report gives one (otherwise leave blank) | `phishing` |
| `value` | The number exactly as reported | `404` |
| `unit` | `count` or `percent` | `count` |
| `source_report` | Name of the report it came from | `NDB report Jul–Dec 2024` |
| `page` | Page number in the report, so it can be checked | `9` |
| `notes` | Anything unusual (e.g. "OAIC rounded this figure") | |

## Metrics to collect

Start with these. They map directly to the project questions.

| `metric` | `category` examples | Answers question |
|---|---|---|
| `total_notifications` | `all` | 1. Trend over time |
| `breaches_by_source` | `malicious_or_criminal_attack`, `human_error`, `system_fault` | 2. Causes |
| `malicious_breakdown` | `cyber_incident`, `theft_of_paperwork_or_storage_device`, `social_engineering_or_impersonation`, `rogue_employee_or_insider` | 2. Causes |
| `cyber_incident_breakdown` | `phishing`, `ransomware`, `compromised_or_stolen_credentials_unknown_method`, `hacking`, `brute_force_attack`, `malware`, `other` | 2. Causes |
| `top_sectors` | `health_service_providers`, `finance`, `education`, `retail`, `australian_government` | 3. Sectors |
| `sector_by_source` | sector name, with the source (`malicious_or_criminal_attack`, `human_error`, `system_fault`) in `subcategory` | 3. Sectors |
| `time_to_identify` | use the bands exactly as the report's chart shows them, e.g. `10_days_or_less`, `11_to_20_days`, `21_to_30_days`, `over_30_days`, `unknown` | 4. Response |
| `time_to_notify` | same as above (Jul–Dec 2024 bands: `10_days_or_less`, `11_to_20_days`, `21_to_30_days`, `over_30_days`, `unknown`) | 4. Response |

Time bands are reported as **percentages**, so set `unit` to `percent` for those rows.

## Tips 💅

- Use **lowercase with underscores** for `metric`, `category` and `subcategory`, and keep spelling identical every time.
- Record numbers **exactly as the report shows them**. Don't calculate anything here; that happens in the notebooks.
- If a report doesn't include a figure, **skip the row** rather than entering 0.
- Fill in the **most recent report first**, check it loads properly, then work backwards.
