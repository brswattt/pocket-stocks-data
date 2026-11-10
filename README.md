# pocket-stocks-data

Small data files the [Pocket Stocks](https://github.com/brswattt/pocket-stocks) app downloads.

- `tickers.csv`: SEC ticker → CIK list (from SEC EDGAR).
- `rank.txt`: 12-month performance of S&P 500 stocks, for the RS rating.
- `fund/<SYMBOL>.json`: fundamentals (EPS, margins, ROE, debt/equity, dividend streak, up to 10 years of
  revenue / net income / free cash flow). Computed from companies' own SEC XBRL filings (SEC EDGAR, public
  domain). Gaps, cross-checks and dividend history come from the
  [defeatbeta/yahoo-finance-data](https://huggingface.co/datasets/defeatbeta/yahoo-finance-data)
  dataset, licensed ODC-By (underlying data: Yahoo Finance, Nasdaq, U.S. Treasury; research and educational
  purposes). Each file says where its numbers came from (`src`, `fb` = filled from the dataset, `chk` = the
  two sources disagreed). Foreign ADRs: per-ADS values converted to USD at spot FX using the ADS ratio read
  from the latest 20-F/40-F (`ads_ratio`, `ads_src`).
- `adr_ratios.json`: cache of ADS ratios per SEC CIK.

Not investment advice; may be delayed or wrong.
