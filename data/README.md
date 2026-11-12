# Data files

- **`NBASupermaxTrap.csv`** — the original author-supplied, 38-column team-season dataset. It has 270 populated team-season observations covering nine seasons (2017–18 through 2025–26), plus a blank trailing row in the original export. It retains team and season IDs, team win totals, roster financial metrics, and the derived salary-share and contract indicators used for the models. The input is preserved **unchanged**. The notebook filters out the blank row in memory.
- **`nba_modeling_data.csv`** — 270-row, 19-column numeric modeling extract recovered from the saved output of the original notebook before the full team-season CSV was supplied. It is retained as a check/audit snapshot; the main notebook **now loads the original full CSV**, not this extract.

The notebook verifies matching values for all 15 inputs used in the two primary OLS specifications. These are *compiled research datasets*, not a complete, independently reproducible scrape or ETL pipeline from Spotrac, RealGM, or NBAstuffer. See the research paper for stated sources, definitions, and the missing analytics-staff interpolation.

The distinct player-level relational database is provided in `../sql/NBASalary.sql` and should not be mistaken for this team-season CSV.
