# pocket-stocks-data

Small data files the [Pocket Stocks](https://github.com/brswattt/pocket-stocks) app downloads.

- `tickers.csv`: SEC ticker → CIK list (from SEC EDGAR).
- `rank.txt`: 12-month performance of S&P 500 stocks, for the RS rating.
- `fund/<SYMBOL>.json`: fundamentals (EPS, margins, ROE, debt/equity, dividend streak, up to 10 years of
  revenue / net income / free cash flow / diluted EPS). Annual EPS is on today's share count (stock splits
  applied); for foreign filers it is per ordinary share in the reporting currency (only its signs and growth
  are meant to be used). A year's figure appears in several annual reports; when the copies disagree
  on its sign the majority wins. A year whose EPS sign still contradicts that year's net income is settled by
  the dataset, or left out and listed in `annual.eps_na` (the app shows those rules as N/A). Computed from companies' own SEC XBRL filings (SEC EDGAR, public
  domain). Gaps, cross-checks and dividend history come from the
  [defeatbeta/yahoo-finance-data](https://huggingface.co/datasets/defeatbeta/yahoo-finance-data)
  dataset, licensed ODC-By (underlying data: Yahoo Finance, Nasdaq, U.S. Treasury; research and educational
  purposes). Each file says where its numbers came from (`src`, `fb` = filled from the dataset, `chk` = checks:
  a bare field name means the two sources disagreed and the filing value was kept; `field:reason` means the
  field was left out on purpose: `price` (impossible next to the share price), `quarters` / `net_income` /
  `basis` / `split` / `shares` (the filing's own figures don't add up), `unresolved` (filing and dataset
  disagree, neither trusted), `range` (impossible value, e.g. gross margin above 100%), `unconfirmed` (ADS
  ratio not confirmed). A missing field means N/A.) Annual series hold one value per fiscal year, labelled by
  the year it mostly covers. Foreign ADRs: per-ADS values converted to USD at spot FX using the ADS ratio read
  from the latest 20-F/40-F (`ads_ratio`, `ads_src`).
- `adr_ratios.json`: cache of ADS ratios per SEC CIK.

Not investment advice; may be delayed or wrong.
