# Build guide: NYC flight delays (R)

**Business question:** which flights leaving New York leave late, and how much of that is the weather rather than things the airline controls, like the time of day?

**Result:** a Quarto report (`flight_delays.html`) with four charts and a logistic regression, published on GitHub Pages. Time: about two sessions.

---

## 1. Put the folder in place

Unzip `nyc-flight-delays` into your `Project Portfolio` folder.

## 2. Install the data package (5 minutes)

Open RStudio and paste this into the Console:

```r
options(timeout = 600)
install.packages("nycflights23")
```

The data comes inside the package, so there is nothing to download by hand.

## 3. Open the project

Double-click `nyc-flight-delays.Rproj`, then click `flight_delays.qmd` in the **Files** panel.

## 4. Run the chunks in order and check your numbers

Click the green ▶ on each chunk from the top. Send a screenshot whenever a number differs.

| Chunk | Check | Expected |
| --- | --- | --- |
| `load` | Flights, cancelled | 435,352, 10,738 (2.5%) |
| `load` | Departed, late | 424,614, 21.6% late |
| `by-hour` | Late rate at 6:00 / 19:00 | 8.9% / 32.5% |
| `by-airline` | Lowest / highest of the 10 airlines | Republic 12.5% / JetBlue 32.3% |
| `by-airline` | Late rate by airport | EWR 23.4%, JFK 23.1%, LGA 18.7% |
| `weather` | Flights matched to weather | 406,779 |
| `weather` | Late without / with rain | 20.2% / 29.5% |
| `weather` | Late without / with low visibility | 21.0% / 32.6% |
| `weather` | Late without / with strong wind | 20.9% / 30.8% |
| `model` | Odds ratio, 6pm+ against 5-8am | about 4.45 |
| `model` | Odds ratio, rain / low visibility / strong wind | about 1.69 / 1.58 / 1.42 |
| `what-if` | Morning vs evening (all flights) | 10.4% vs 32.1% |
| `what-if` | Dry vs rain | 20.2% vs 28.9% |

The `model` and `what-if` chunks take a minute: the model is fitted on over 400,000 flights.

## 5. Write your readings

Two places say **Your reading**. Replace each line with two or three sentences in your own words, as in the retail project (no `>` at the start, no `_` at the end).

Points to think about:

- Why would delays build up through the day? (Think about what an aircraft does between its first and last flight.)
- Rain raises the late rate, but how many hours of the year does it rain? Which factor affects more flights overall?
- What can an airline change: the weather, or its timetable?

## 6. Render and publish

1. Click **Render**. It creates `flight_delays.html`.
2. On GitHub, create a public repository `nyc-flight-delays` (README off). Description: *Which NYC flights leave late, and how much is weather to blame? Delay analysis and logistic regression in R.*
3. Upload `flight_delays.qmd`, `flight_delays.html`, `README.md`, `GUIDE.md`, `nyc-flight-delays.Rproj` and the `charts` folder. Add `.gitignore` by hand.
4. Topics: `r`, `tidyverse`, `ggplot2`, `logistic-regression`, `aviation`, `quarto`, `data-analysis`.
5. **Settings > Pages**: branch `main`, folder `/ (root)`, Save. The report will be at `https://ayanfedara.github.io/nyc-flight-delays/flight_delays.html`.
