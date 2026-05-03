# Dataset

## Daily Delhi Climate Dataset

This project uses the **Daily Delhi Climate Dataset** available on Kaggle.

### Download Instructions

1. Go to: https://www.kaggle.com/datasets/sumanthvrao/daily-climate-time-series-data
2. Download and extract the ZIP file
3. Place the following files in this `data/` directory:
   - `DailyDelhiClimateTrain.csv`
   - `DailyDelhiClimateTest.csv`

### Features

| Column        | Description                     | Unit  |
|---------------|---------------------------------|-------|
| `date`        | Date of observation             | —     |
| `meantemp`    | Mean daily temperature          | °C    |
| `humidity`    | Relative humidity               | %     |
| `wind_speed`  | Wind speed                      | km/h  |
| `meanpressure`| Mean atmospheric pressure       | hPa   |

### Why not included?

CSV files are excluded from version control via `.gitignore` to keep the repository lightweight. Please download from Kaggle directly.
