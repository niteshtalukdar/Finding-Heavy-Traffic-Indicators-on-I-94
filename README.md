# Finding Heavy Traffic Indicators on I-94

An exploratory data analysis project investigating what conditions — time of day, season, day of the week, and weather — are associated with heavy westbound traffic on Interstate 94 near the Minneapolis–Saint Paul metro area.

---

## Project Overview

Using hourly traffic volume records from a monitoring station located approximately midway between Minneapolis and Saint Paul, this analysis identifies patterns and conditions that correlate with high traffic volumes. Because the station only records **westbound traffic**, findings apply specifically to that direction and location rather than the I-94 corridor as a whole.

**Goal:** Determine reliable indicators of heavy traffic (volumes above ~5,000 cars/hour) to support traffic planning, commute decisions, or further predictive modeling.

---

## Dataset

**Source:** Metro Interstate Traffic Volume dataset (`Metro_Interstate_Traffic_Volume.csv`)

**Key columns:**
- `date_time` — hourly timestamp of the observation
- `traffic_volume` — number of vehicles recorded per hour
- `temp` — temperature in Kelvin
- `rain_1h`, `snow_1h` — precipitation totals for the hour
- `clouds_all` — cloud cover percentage
- `weather_main` — broad weather category (e.g., Clear, Rain, Snow)
- `weather_description` — granular weather description (e.g., "light rain and snow")

---

## Methodology

1. **Exploratory analysis** — distribution of traffic volume, identifying the day/night split
2. **Day/night segmentation** — nighttime data (7 PM – 7 AM) was excluded since traffic is consistently light; analysis focuses on daytime hours (7 AM – 7 PM)
3. **Time-based analysis** — average traffic volume broken down by month, day of week, and hour of day (with business days and weekends analyzed separately)
4. **Weather-based analysis** — Pearson correlations for numerical weather features; bar chart comparison of average traffic by weather category and description

---

## Key Findings

### Time Indicators

| Indicator | Finding |
|---|---|
| **Season** | Traffic is heavier during warm months (March–October); July shows an anomalous dip, possibly linked to road construction in 2016 |
| **Day of week** | Business days (Mon–Fri) consistently see higher volumes than weekends, reflecting commuter patterns |
| **Hour of day (weekdays)** | Two clear rush hour peaks: ~7 AM and ~4 PM, with volumes regularly exceeding **6,000 cars/hour** |
| **Hour of day (weekends)** | Smoother, lower-volume pattern (1,500–4,500 cars/hour) with no distinct rush hours |

### Weather Indicators

Numerical weather features (temperature, rain, snow, cloud cover) show weak correlations with traffic volume overall. However, three specific weather descriptions are associated with volumes exceeding 5,000 cars/hour:

- **Shower snow**
- **Light rain and snow**
- **Proximity thunderstorm with drizzle**

A likely explanation: moderate adverse weather discourages walking and cycling, pushing more people into cars without being severe enough to deter driving altogether.

---

## Tools & Libraries

- **Python 3**
- `pandas` — data loading, transformation, and groupby aggregations
- `matplotlib` — histograms, line plots, scatter plots, and bar charts

---

## Limitations

- Results reflect **westbound traffic only** at a single monitoring station; they should not be generalized to the full I-94 corridor
- The July traffic anomaly likely reflects a data artifact (construction in one year) rather than a consistent seasonal pattern
- Weather correlations are weak at the aggregate level; more granular modeling (e.g., interaction effects between weather and time) may yield stronger signals

---

## Potential Next Steps

- Build a predictive model for traffic volume using time and weather features
- Investigate the July anomaly year-by-year to isolate the cause
- Extend the analysis to eastbound traffic for directional comparison
