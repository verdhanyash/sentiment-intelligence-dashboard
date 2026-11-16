# AWS costs — quick guide

The simplified tab has five charts. USD/INR switches currency; hover or focus values for formulas and evidence. Each chart offers CSV and PNG export.

| Chart | Function |
| --- | --- |
| Service spending mix | Select latest November, October + November, earlier audit, an audited day, or retained-resource estimate. Shares use the rounded category sum. |
| Six-month spending | Supplied June–November 2026 totals. November is a partial month. |
| Month-end outlook | Compare $116.78 MTD with the $233.56 linear scenario and AWS screenshot forecast of $258.31. The methods differ. |
| Cost per video run | Split the 8- and 18-second runs into GPU runtime allocation and estimated S3. |
| Runtime vs endpoint uptime | Compare 26 seconds of runtime allocation with 1/5/15/60 minutes of shared endpoint uptime, selected using the dropdown. These are alternative views. |

The top cards show November spend, October + November total, average daily burn and remaining credit balance. The two-run cards show combined allocation, mean per run and S3 total. Expand the assumptions note for exclusions and endpoint-status limits.

## Corrected arithmetic

GPU allocation = (8 + 18) × $1.8312 / 3600 = **$0.01322533 total**, or **$0.00661267 per run**. The supplied $0.0061 GPU average was incorrect.

Assuming decimal file sizes 0.89/0.92 MB, one PUT, one GET and one month of storage each, S3 is approximately **$0.00005402 total**. Combined allocation is **$0.01327936**, averaging **$0.00663968 per run**.

The times were supplied by the user; billable GPU uptime was not independently measured. A shared one-hour endpoint costs **$1.8312 GPU**, or **$0.9156/run** for two runs, before S3. Idle and provisioning time can increase costs. Application plans, tax and other services are excluded, not assumed free. No live AWS bill or current endpoint status was checked.

Sources: [calculation evidence](https://verdhanyash.github.io/sentiment-intelligence-dashboard/two-run-cost-basis.txt), [audited rates](https://github.com/Aamodx6/Argus/blob/cef48cb/docs/reports/aws-cost-2026-11-15/sydney-unit-rates.csv), [AWS pricing](https://aws.amazon.com/sagemaker/ai/pricing/), [supplied console](https://verdhanyash.github.io/sentiment-intelligence-dashboard/aws-console-snapshot-2026-11-15.png).
