# AI Exposure of the Canadian Job Market

An interactive map of how much AI is likely to reshape the work Canadians do.

**Live site:** [fb-121.github.io/canada-ai-jobs](https://fb-121.github.io/canada-ai-jobs)

---

## What this is

The site scores 113 Canadian occupations across 10 sectors from 0 to 10 on AI exposure: how much AI is likely to reshape the work over the next 5 to 10 years. Together these occupations employ 5.2 million of Canada's 9.6 million full-year, full-time workers (55%). In the treemap, the size of each tile shows how many people work in that occupation. The colour can be switched between three measures: AI exposure, median pay, and the education typically required (TEER category). A sortable list view shows the same data, and it's the default on phones.

---

## Scope

The 113 occupations are NOC 2021 unit groups chosen to represent every major sector of the Canadian economy. Canada has 516 unit groups in total, so this is a representative selection, not a complete census of occupations. Every employment and wage figure comes directly from Statistics Canada or ESDC, and every score comes from the published prompt below.

---

## Data sources

| Data | Source | Notes |
|---|---|---|
| Occupations | [NOC 2021 Version 1.0](https://www.statcan.gc.ca/en/subjects/standard/noc/2021/indexV1), Statistics Canada and ESDC | 5-digit unit group codes and official definitions |
| Workers | [Statistics Canada 2021 Census](https://www12.statcan.gc.ca/census-recensement/2021/dp-pd/dv-vd/occ-pro/index-en.cfm) | People who worked full year, full time and reported employment income in 2020. Part-time, part-year and seasonal workers are not counted. |
| Median pay | [ESDC Labour Market Information wage dataset](https://open.canada.ca/data/en/dataset/adad580f-76b0-4502-bd05-20c125de9116) | National figures, released November 2025. Hourly wages converted to annual pay at 2,080 hours a year. |
| Education | TEER category | The second digit of every NOC 2021 code. |

One exception: the Census groups senior managers (NOC 00011 to 00015) into a single category, and that category has no ESDC wage. Its pay figure is the Census median employment income for 2020, and the site labels it that way.

Every employment figure was checked against the Census release and every wage against the ESDC file.

---

## How AI exposure is scored

Each occupation gets one score from 0 to 10. The score counts direct effects (AI doing tasks people do today) and indirect effects (AI making each worker productive enough that fewer are needed). The main signal is whether the work product is digital: physical, hands-on and face-to-face work has a natural barrier.

The score measures **digital AI only**. Robots, self-checkouts and self-driving vehicles are a separate, slower kind of automation, so they do not raise a score.

| Score | Meaning |
|---|---|
| 0 to 1 | Minimal: physical work in unpredictable environments |
| 2 to 3 | Low: AI touches only peripheral tasks |
| 4 to 5 | Moderate: AI assists, but human presence stays central |
| 6 to 7 | High: mostly knowledge work, strongly AI-assisted |
| 8 to 9 | Very high: almost entirely digital work, major restructuring |
| 10 | Maximum: routine digital processing AI can already do |

Scores were produced in September 2026 by Claude Opus 5.5 (Anthropic). It applied the prompt in [`data/scoring-prompt.txt`](data/scoring-prompt.txt), unchanged, to each occupation's official NOC 2021 title and definition. Every score and its rationale is in [`data/occupations.csv`](data/occupations.csv) and [`data/occupations.json`](data/occupations.json).

The March 2026 version of this site used scores assigned without a fixed prompt. Those have been fully replaced, so the published method now matches how the scores were actually produced.

**A high score does not mean a job will disappear.** It means AI is likely to change how the work is done. Scores do not account for demand, regulation, or people's preference for a human. They are informed estimates, and reasonable analysts could score some occupations differently.

For a complementary view, Anthropic's [observed exposure research](https://www.anthropic.com/research/labor-market-impacts) (March 2026) measures which occupations people actually use AI for today, using US data.

---

## Limitations

- **National figures only.** Alberta's resource economy and Ontario's finance and tech sectors have different profiles that a national view flattens.
- **2020 employment.** The 2021 Census counted employment in 2020, a year affected by COVID-19, so counts in healthcare, hospitality and food service may be atypical. It is still the most recent detailed occupational count in Canada.
- **Different years.** Pay reflects 2025 while employment reflects 2020. Each measure uses the most current reliable source.
- **Independent analysis.** Not affiliated with or endorsed by Statistics Canada or ESDC.

---

## Files

| File | What it is |
|---|---|
| `index.html` | The whole site in one file. No build step. |
| `data/occupations.csv` | Every occupation with its NOC code, official title, workers, pay, TEER, score and rationale |
| `data/occupations.json` | The same data as JSON |
| `data/scoring-prompt.txt` | The exact prompt used to score every occupation |

To run it locally, clone the repo and open `index.html` in any browser.

```bash
git clone https://github.com/fb-121/canada-ai-jobs
cd canada-ai-jobs
open index.html
```

---

## Roadmap

- **Alberta edition** using Alberta-specific Census employment and ESDC wages
- **Job outlook layer** using the federal government's 2024 to 2033 occupational projections (COPS)
- **Full coverage** of all 516 NOC unit groups
- **2026 Census update** when Statistics Canada releases 2026 occupational data

---

## About

Built by [Faaiz Bilal](https://www.linkedin.com/in/faaiz-bilal), who is interested in AI and its impact on Canadian society and the economy.

Inspired by [Andrej Karpathy's analysis of the US job market](https://karpathy.ai/jobs/).

---

## Licence

Government of Canada data (2021 Census, ESDC Labour Market Information, NOC 2021) is used under the [Open Government Licence (Canada)](https://open.canada.ca/en/open-government-licence-canada). The visualization, methodology, scores and all other original content are the work of Faaiz Bilal.

*Last updated September 2026.*
