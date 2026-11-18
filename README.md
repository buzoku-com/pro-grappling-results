---
license: cc-by-4.0
pretty_name: Professional grappling results (ADCC, Polaris, UFC BJJ)
language:
  - en
tags:
  - sports
  - grappling
  - brazilian-jiu-jitsu
  - adcc
size_categories:
  - 1K<n<10K
configs:
  - config_name: bouts
    data_files: data/bouts.csv
  - config_name: events
    data_files: data/events.csv
---

# Professional grappling results: ADCC, Polaris, UFC BJJ

Match-level results from professional submission grappling and Brazilian jiu-jitsu events,
compiled and maintained by [bjj.space](https://bjj.space), the open BJJ community database.

| File | Rows | What |
|---|---|---|
| `data/events.csv` | 76 | ADCC World Championships (1998–2026), ADCC Trials and continental championships, numbered Polaris cards (including Squads and Grand Prix), UFC BJJ cards |
| `data/bouts.csv` | 4,675 | one row per match: fighters, winner, method, weight class or division, round |

Every row links to its page on bjj.space: `event_url` on every row, plus `fighter_1_url` and
`fighter_2_url` where the athlete has a public profile. The pages hold brackets, records,
lineage and photos.

## Columns (`bouts.csv`)

| Column | Meaning |
|---|---|
| `bout_id`, `event_id` | stable bjj.space ids |
| `event_name`, `date` | event and its start date (ISO 8601) |
| `weight_class` | weight class or division label |
| `category` | card position on superfight cards (e.g. "Main Event") |
| `round` | bracket round where applicable |
| `title_fight` | 1 for a title match |
| `fighter_1`, `fighter_2` | athlete names |
| `fighter_1_url`, `fighter_2_url` | bjj.space profile |
| `winner` | `1`, `2`, `draw`, or empty when unknown |
| `method` | `submission`, `points`, `decision`, `split_decision`, `dq`, `no_show`, `draw`, `split_draw`, or empty |
| `method_detail` | e.g. the submission |
| `event_url` | bjj.space event page |

## Scope and privacy
- Only adult professional events. A match involving anyone under 18 is left out.
- Athletes who opted out of bjj.space's public listing appear as `withheld`.
- Byes and cancelled matches are left out.
- Coverage has gaps: some Polaris numbers are missing, and some matches have no recorded
  method. Corrections are welcome at [bjj.space](https://bjj.space) or as an issue on this
  repository.

## Licence and attribution
[CC BY 4.0](LICENSE). Credit **"bjj.space"** with a link to <https://bjj.space>, for example:

> Results data from [bjj.space](https://bjj.space), CC BY 4.0.

## Updates
Regenerated from the bjj.space database with `bin/rails datasets:pro_results`.
