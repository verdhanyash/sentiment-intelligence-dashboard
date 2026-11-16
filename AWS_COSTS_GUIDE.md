# AWS costs tab — quick guide

The tab combines supplied billing evidence with clearly labelled cost scenarios. USD/INR changes the display currency. Hover or focus a value for its formula, source, period and FX rate. CSV exports download the underlying values; PNG exports save a chart.

## Controls and calculations

- **Service view** selects the latest console total, October plus latest November, the earlier audit, one audited day, or retained-storage estimates. The latest total is $116.78 while rounded service entries sum to $116.77.
- **Earlier audit ledger** expands historical gross usage, signed credits and net. Remaining credits are a separate balance.
- **Burn basis** selects console $116.78 or summary $116.77. Daily average = MTD / 15; linear month-end = average × 30; annual run rate = average × 365. Budget days = max(0, budget − MTD) / average. These use the supplied 15-day period.
- **Video scenarios** select processing speed, per-chunk setup, video length, users and iterations per user. GPU seconds = video seconds / speed + setup × ceil(video seconds / 120). Cost = GPU seconds × $1.8312 / 3600. Aggregate cost = iteration cost × users × iterations/user.
- **Small-upload controls** select the assumed 0.89/0.92 MB file, GPU runtime and completed videos/day. S3 = one PUT + one GET + first-month storage. Actual video files and successful inference runtimes were not supplied.
- **Application charges** expand the cost-basis note and official Vercel/Neon pricing links. Actual plans and overages remain unknown.

## Graphs

| Graph | What it shows |
| --- | --- |
| Service spending mix | Service shares for the selected billing view. |
| Six-month cost trend | Supplied June–November totals; November is incomplete. |
| Latest published daily peak | The supplied $44.02 November 14 peak; other recent daily numbers are unavailable. |
| Daily AWS expenditure — earlier audit | Older exported daily charges, with their original cutoff. |
| Cumulative expenditure — earlier audit | Running sum of those older daily charges. |
| Monthly services — earlier audit | Monthly gross spending split by service. |
| Usage and credits — earlier audit | Gross charges versus positive credit-offset magnitudes. |
| Other services — earlier audit | Non-SageMaker charges on a readable smaller scale. |
| Month-end scenarios | MTD, simple linear projection and AWS's separate $258.31 forecast. |
| Budget remaining | Share of the assumed cap used and illustrative days remaining. |
| One iteration — 5 sec to 5 min | GPU-only allocation by video duration and assumed speed. |
| Aggregate cost by duration | The same model multiplied by selected users and iterations. |
| One small video — assumed GPU runtime | GPU allocation plus S3 requests and first-month storage. |
| Always-on cost allocated across videos | Daily and 730-hour monthly capacity costs divided across assumed completed uploads. |

## Checked cost interpretation

At the audited Sydney rates, a decimal 0.89–0.92 MB file costs about $0.0000267–$0.0000274 for one PUT, one GET and one month of S3 Standard storage. “About $0.00003” is reasonable for that limited scope.

Adding assumed GPU runtime gives approximately $0.00104 at 2 seconds, $0.00511 at 10 seconds and $0.01529 at 30 seconds. These allocate runtime on a warm provisioned instance; provisioning, idle time, failures and other services can add cost.

The daily GPU charge is $43.9488. Dividing by 19 gives $2.3131/video; dividing by 100 gives $0.4395/video. The audit's 19 invocations were one sampled day, not verified completed videos/day. A 730-hour budget is $1,336.776; dividing that by 30 × 19 instead gives $2.3452/video. Runtime and always-on GPU allocations are alternative accounting views and must not be added together.

The cleanup report found zero endpoints on November 15 and about $1.05/month of retained storage. Current endpoint state has not been queried. Videos over 120 seconds need chunking and a tested orchestration path.

Sources: [audited Sydney rates](https://github.com/Aamodx6/Argus/blob/cef48cb/docs/reports/aws-cost-2026-11-15/sydney-unit-rates.csv), [cleanup report](https://github.com/Aamodx6/Argus/blob/cef48cb/docs/reports/aws-cost-reductions-2026-11-15.md), [supplied console screenshot](public/aws-console-snapshot-2026-11-15.png), [Vercel](https://vercel.com/docs/plans/pro-plan), [Neon](https://neon.com/pricing). Evidence dates and FX are retained in tooltips and exports.
