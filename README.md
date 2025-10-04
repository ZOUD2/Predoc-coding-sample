# FMC Exam – Donghang Zou

## File Structure
~~~
.
├── fmc_report_Zou_Donghang.pdf     # Written report (main deliverable)
├── fmc_script_Zou_Donghang.do      # Main Stata script (entry point)
├── README.md                       # Instructions (this file)
├── data/                           # Raw CSVs + intermediate and cleaned .dta files
│   ├── crsp.csv
│   ├── comp.csv
│   ├── linktable.csv
│   ├── crsp_raw.dta
│   ├── comp_raw.dta
│   ├── ccm_raw.dta
│   ├── crsp_clean.dta
│   ├── comp_clean.dta
│   ├── ccm_clean.dta
│   ├── comp_june.dta
│   ├── market_returns.dta
│   └── crsp_compustat_merged.dta
├── output/
│   ├── figures/                    # Graphical output
│   │   └── market_cum_return.png
│   └── tables/                     # Tables (LaTeX export)
│       └── summary_stats.tex
└── code/                           # (Optional: space for extra scripts or notes)
~~~

## How to Run
1. Open **Stata 17+**.  
2. Navigate to the **exam root folder** (the folder containing `fmc_script_Zou_Donghang.do`):  
   ~~~stata
   cd "path/to/unzipped/folder"
   ~~~
   The script uses **relative paths** (`data/...`, `output/...`), so you only need to set this once.  
3. Run:  
   ~~~stata
   do fmc_script_Zou_Donghang.do
   ~~~

## What the Script Does
- **Data Import & Cleaning:** Imports CRSP, Compustat, and the CCM link table; builds cum-dividend returns and market equity.  
- **Market Return Index:** Computes value-weighted market return and cumulative index → `output/figures/market_cum_return.png`.  
- **Book Equity & Fundamentals:** Constructs book equity and investment ratios (CAPX/AT, XRD/AT) under the June–t convention.  
- **Merge:** Links CRSP–Compustat via CCM with priority rules.  
- **Summary Statistics:** Exports to `output/tables/summary_stats.tex`.  
- **Analysis:** Runs regressions for **Q1** (physical investment) and **Q3** (heterogeneity by industry/size).

## Notes
- The first `cd` line in the `.do` file (pointing to the author’s machine) can be **ignored or commented out**. Just `cd` to the exam root as above.  
- Intermediate `.dta` files in `data/` are included for transparency and are recreated automatically when running the script.  
- Requires two user-written Stata packages (install if needed):  
  - [`reghdfe`](https://github.com/sergiocorreia/reghdfe)  
  - [`estout`](https://repec.sowi.unibe.ch/stata/estout/)  
- Tested with **Stata 17**.
