# Data

The dataset used is the **Bike Sharing Dataset** from the UCI Machine Learning Repository.

- **Source**: https://archive.ics.uci.edu/ml/datasets/Bike+Sharing+Dataset
- **File needed**: `day.csv` (daily aggregated records)
- **Rows**: 731 (2 years of daily data)
- **License**: Creative Commons Attribution 4.0

## Columns used

| Column | Description |
|---|---|
| `season` | 1=spring, 2=summer, 3=fall, 4=winter |
| `yr` | Year (0=2011, 1=2012) |
| `mnth` | Month (1–12) |
| `holiday` | Whether the day is a holiday |
| `weekday` | Day of the week |
| `workingday` | 1 if neither weekend nor holiday |
| `weathersit` | Weather situation (1=clear, 2=mist, 3=light snow/rain) |
| `temp` | Normalised temperature (Celsius) |
| `atemp` | Normalised feeling temperature |
| `hum` | Normalised humidity |
| `windspeed` | Normalised wind speed |
| `casual` | Count of casual users (dropped — leaks target) |
| `registered` | Count of registered users (dropped — leaks target) |
| `cnt` | **Target** — total bike rentals |

## Download

The notebook downloads `day.csv` automatically in cell 2 via `urllib`:

```python
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/00275/Bike-Sharing-Dataset.zip"
```

Do not commit `day.csv` to this repo — it is listed in `.gitignore`.
