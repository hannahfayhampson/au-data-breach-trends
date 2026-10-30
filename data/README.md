# 📥 Data guide

## Source

Office of the Australian Information Commissioner (OAIC) Notifiable Data Breaches (NDB) reports.

- **2018 to mid-2019:** reports were published **quarterly**
- **Later reports:** published **half-yearly** (January–June and July–December)

Quarterly figures are combined into half-years during cleaning so every period compares fairly.

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
| `top_sectors` | `health_service_providers`, `finance`, `education`, `retail`, `australian_government` | 3. Sectors |
| `time_to_identify` | `under_10_days`, `11_to_30_days`, `31_to_60_days`, `61_to_120_days`, `over_120_days`, `unknown` | 4. Response |
| `time_to_notify` | same groupings as above | 4. Response |

## Tips 💅

- Use **lowercase with underscores** for `metric`, `category` and `subcategory`, and keep spelling identical every time.
- Record numbers **exactly as the report shows them**. Don't calculate anything here; that happens in the notebooks.
- If a report doesn't include a figure, **skip the row** rather than entering 0.
- Fill in the **most recent report first**, check it loads properly, then work backwards.
