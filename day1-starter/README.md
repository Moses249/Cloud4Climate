# Compare Climate Change: Then vs Now

**What it does (one line):** You enter a **city** and your **birth year**. The app shows how much **warmer it is now** compared to around your birth.

## Inputs
- `city` (or `latitude` + `longitude`)
- `birth_year` (example: 1994)

## Time windows
- **THEN** = birth_year-2 .. birth_year+2  (5 years)
- **NOW**  = last 5 full years (example: 2020–2024)

## Metrics
- `t_mean` = average temperature
- `t_max`  = very hot temperature (about the top 5% hottest days)
- `hot_days` = number of days > 30°C (you can change 30 later)

## Output (example)
{
  "location": {"city":"Calgary","lat":51.05,"lon":-114.07},
  "periods": {
    "then": {"years":"1992-1996","t_mean":6.4,"t_max":30.1,"hot_days":2, "quality":"ok"},
    "now":  {"years":"2020-2024","t_mean":8.1,"t_max":33.2,"hot_days":11, "quality":"ok"}
  },
  "deltas": {"t_mean":1.7,"t_max":3.1,"hot_days":9}
}

## Data checks (click these to see JSON)
- Geocoding (Calgary → lat/lon):  
  https://geocoding-api.open-meteo.com/v1/search?name=Calgary&count=1&format=json

- Monthly climate (THEN, 1992–1996):  
  https://climate-api.open-meteo.com/v1/climate?latitude=51.05&longitude=-114.07&start_year=1992&end_year=1996&temperature_unit=celsius&monthly=temperature_2m_mean,temperature_2m_max

- Daily max temps (NOW, 2020–2024):  
  https://archive-api.open-meteo.com/v1/archive?latitude=51.05&longitude=-114.07&start_date=2020-01-01&end_date=2024-12-31&daily=temperature_2m_max&temperature_unit=celsius&timezone=auto

## Folder map (today)
/
├─ app/                # frontend + tiny backend (later)
├─ infra/              # terraform on azure (later)
├─ ops/                # scripts (pdf, alerts) (later)
└─ .github/workflows/  # ci/cd (added on Day 5)

## Next (Day 2)
- Build one composite API (`/compare`) using Celigo that returns the JSON above.
