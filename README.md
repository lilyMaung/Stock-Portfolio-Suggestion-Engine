# Stock Portfolio Suggestion Engine

CMPE 165 Final Project

An educational web app that suggests a four-stock portfolio from historical data, based on an investment amount and a risk profile (Conservative, Balanced, or Growth). It helps beginners see how return, risk, and diversification relate.

> **Educational use only.** This app does not execute trades and does not guarantee any investment return. Past performance does not predict future results.

## Team Members

| Name | Role |
|---|---|
| _Name 1_ | Data and calculations |
| _Name 2_ | Strategy and app logic |
| _Name 3_ | UI and documentation |

## Links

- **Final report:** [docs/report.pdf](docs/report.pdf)
- **Presentation slides:** [docs/slides.pdf](docs/slides.pdf)
- **Loom demo video (1 min):** _add Loom URL here_

## Features

- Enter an investment amount and choose a risk profile
- Input validation for blank, negative, and non-numeric amounts
- Stock analysis table: ticker, company name, sector, historical return
- Suggests exactly 4 stocks from at least 3 sectors, allocating 100% of the investment
- Shows percentage and dollar allocation for each stock
- Explains why each stock was selected and how the risk profile affected the result
- Compares the suggested portfolio against an equal-weight portfolio (historical return and estimated final value)
- Hypothetical scenario: all selected stocks decline by 10% (estimated loss and remaining value)
- No login required; no AI API is called at runtime

## How It Works

1. Historical adjusted closing prices are loaded from a saved dataset.
2. The analyzer calculates each stock's historical return (and volatility).
3. The strategy for the chosen risk profile selects four stocks from at least three sectors and assigns weights.
4. The allocator converts weights into percentages and dollar amounts.
5. The app compares the result with an equal-weight portfolio and runs the 10% decline scenario.

### Risk Profiles

_Fill in the final definitions your group chooses._

| Profile | Meaning in this project |
|---|---|
| Conservative | Lower-volatility stocks, more even weights |
| Balanced | Mix of return and risk (return/risk score) |
| Growth | Higher-return stocks, larger weights on top performers |

### Formulas

- **Historical return** = (final adj. close − initial adj. close) / initial adj. close
- **Portfolio return** = sum of (weight × stock return)

## Project Structure

```
src/        Application code (data loader, analyzer, strategies, allocator, UI)
data/       Saved price data and data notes
tests/      Test cases and results
docs/       Report, slides, screenshots, AI-use disclosure
README.md
requirements.txt
```

## Setup Instructions

**Requirements:** Python 3.10+

```bash
git clone <repo-url>
cd <repo-folder>

python -m venv venv
source venv/bin/activate          # Windows: venv\Scripts\activate

pip install -r requirements.txt
```

## Run the App

```bash
streamlit run src/app.py
```

## Run the Tests

```bash
pytest tests/
```

## Dependencies

- Python
- Streamlit
- yfinance
- pandas
- pytest

## Data Source

- **Source:** yfinance (Yahoo Finance)
- **Stocks used:** _list the 20 tickers_
- **Historical period:** _start date to end date (about 1 year)_
- **Prices:** adjusted closing prices
- **Sector and company names:** provided by yfinance
- **Cleaning steps:** _document missing-value handling, date alignment, etc._
- **Saved copy:** `data/prices.csv` (so results are repeatable)

## Testing

Test cases, results, and hand-verified calculations are in `tests/` and `docs/`. See the report for the acceptance criteria and how each was tested.

## AI Use Disclosure

AI tools were used to assist with coding, debugging, documentation, and learning. The application does not call any AI API at runtime to select stocks, build portfolios, or make recommendations. Details are in [docs/ai-disclosure.md](docs/ai-disclosure.md).

## Limitations

- Based on about one year of historical data only; the past does not predict the future
- Small stock universe (20 stocks)
- Does not account for fees, taxes, or trading costs
- Educational tool, not financial advice
