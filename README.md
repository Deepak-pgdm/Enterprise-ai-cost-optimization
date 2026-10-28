# Enterprise AI Cost and Compute Resource Optimization Framework

This project looks at how a business can estimate AI model costs and compare options before choosing a model for different tasks. It uses a small example dataset so the calculations are easy to review and change.

## What it does

- Estimates monthly input and output token costs for a sample set of workloads.
- Compares the estimated cost of three example model tiers.
- Checks whether each model meets the quality level listed for a workload.
- Suggests practical ways to reduce unnecessary token use.
- Saves the results as CSV files and charts.

## Project folders

```text
enterprise-ai-cost-framework/
|-- data/
|   |-- model-rates.csv
|   |-- sample-workload.csv
|-- reports/
|-- src/
|   |-- optimize-costs.py
|-- requirements.txt
|-- README.md
|-- LICENSE
```

## Before you start

You will need Python 3.10 or newer. The project uses pandas and matplotlib for its data work and charts.

Install the required packages from the project folder:

```bash
pip install -r requirements.txt
```

Run the analysis from the same folder:

```bash
python src/optimize-costs.py
```

The script reads the sample files in `data` and creates the result files in `reports`.

## Input data

### `data/model-rates.csv`

This file contains example prices per one million input and output tokens, along with a quality tier for each model. The prices are examples for learning and are not current quotes from any AI provider. Check the official pricing page for your provider before using the figures for a real budget.

### `data/sample-workload.csv`

This file contains fictional monthly usage estimates for tasks such as FAQ answers, email drafting, document analysis, ticket classification and report summaries. The sample numbers do not describe a real company.

## Reports created

- `reports/cost-estimates.csv` lists the estimated cost for each workload and model.
- `reports/model-comparison.csv` compares estimated monthly totals by model.
- `reports/optimization-recommendations.csv` gives a model suggestion and a few cost-saving ideas for each workload.
- `reports/monthly-cost-comparison.png` compares the estimated monthly cost by model.
- `reports/workload-costs.png` compares estimated cost across workloads.

## How costs are calculated

For each workload, the script estimates the number of input and output tokens used in a month.

Input cost = monthly input tokens / 1,000,000 x input price per million tokens

Output cost = monthly output tokens / 1,000,000 x output price per million tokens

Estimated monthly cost = input cost + output cost

These estimates do not include taxes, hosting, networking, tool use or other provider-specific charges.

## How to read the recommendations

The script first filters out models that do not meet the workload's configured quality tier. From the remaining options, it selects the lowest estimated cost. It also suggests reviewing long outputs, repeated context, caching and model routing where appropriate.

These are starting points, not automatic production decisions. Test the recommendations against response quality, latency, security and reliability before adopting them.

## Limitations

This is a small planning and learning project. It uses sample data and does not connect to an AI provider, monitor live traffic or change production infrastructure. Results will only be as accurate as the prices and workload figures entered into the CSV files.

## License

This project is shared under the MIT License. See `LICENSE` for details.
