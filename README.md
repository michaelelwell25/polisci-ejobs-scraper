# Political Science eJobs Scraper

Parses APSA eJobs PDFs and MPSA eJobs CSVs, filters listings based on your research profile and job preferences, and outputs a color-coded Excel tracker.

## Setup

```bash
pip install -r requirements.txt
```

## Usage

```bash
# Both sources
python ejobs_scraper.py --apsa PSJobs202604.pdf --mpsa "Full-Time Faculty Positions.csv" -o tracker.xlsx

# APSA only
python ejobs_scraper.py --apsa PSJobs202604.pdf -o tracker.xlsx

# MPSA only
python ejobs_scraper.py --mpsa "Full-Time Faculty Positions.csv" -o tracker.xlsx

# Custom config
python ejobs_scraper.py --config my_profile.yaml --apsa PSJobs202604.pdf -o tracker.xlsx
```

## Customizing Your Profile

Edit `profile_config.yaml` to match your research agenda:

- **research_keywords**: Terms that get matched against job descriptions. Listings with more matches score higher.
- **subfield_match**: Which APSA subfield categories you'd apply to.
- **rank_tiers**: Which position types are Priority (TT), Lower Priority (VAP), or Excluded.
- **locations**: US-only, include Canada, or fully international. Option to exclude community colleges.

## Output

The Excel file includes:
- Color-coded rows (green = Priority/TT, yellow = Lower Priority/VAP)
- Match score based on keyword hits against your profile
- Frozen header row with auto-filters
- "Applied?" and "Status" columns for tracking

## Where to Get the Data

- **APSA eJobs**: Download the monthly PDF from [eJobs](https://www.apsanet.org/jobs) (requires APSA membership)
- **MPSA eJobs**: Export the CSV from the [MPSA job board](https://www.mpsanet.org/job-board/)

## Notes

- The APSA PDF parser handles the messy formatting as best it can -- some institution names or deadlines may need manual cleanup
- Duplicate listings across sources are auto-removed
- Deadlines that have already passed are still included (filter in Excel if needed)
