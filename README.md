# Korean Listed Company Valuation Automation
## Comparable Company Analysis (Comps) Pipeline

A Python-based pipeline that automates the IB valuation workflow for Korean-listed companies — extracting financial statements via DART API, parsing D&A from annual report filings, computing key valuation metrics, and generating an IB-formatted Excel output.

---

## What It Does

- Pulls financial statements (IS, BS) from DART Open API
- Extracts D&A via HTML parsing of annual report footnotes (not available through standard API)
- Computes EV, EBITDA, and core valuation multiples (EV/EBITDA, EV/EBIT, P/E)
- Outputs a formatted Comps table in Excel — IB-style, with negative figures in parentheses

---

## How to Use

```python
# Input tickers and company names
results = [get_valuation('005930'), get_valuation('000660')]
names = ['Samsung Electronics', 'SK Hynix']

# Generate Excel output
build_comps_excel(results, names)
```

---

## Requirements
pip install opendartreader finance-datareader pandas openpyxl requests beautifulsoup4 lxml

DART API key required — apply at https://opendart.fss.or.kr

---

## Sample Output

| Company | Ticker | EV/EBITDA | EV/EBIT | P/E |
|---|---|---|---|---|
| Samsung Electronics | 005930 | 9.94x | 69.15x | 34.43x |
| SK Hynix | 000660 | 14.79x | (12.28x) | (11.27x) |
| DB HiTek | 000990 | 5.20x | 7.82x | 9.87x |
| **Average** | - | **9.98x** | **38.48x** | **22.15x** |

---

## Next Steps
- DCF model automation (WACC, FCFE projection, Terminal Value)
- Expand comparable universe
- Package as reusable Python library
