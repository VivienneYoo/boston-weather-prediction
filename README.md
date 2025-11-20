# Boston Weather Prediction Model

Predicting Boston's daily temperatures using 10 years of weather data and linear regression. Got 99.5% accuracy which honestly surprised me.

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Accuracy](https://img.shields.io/badge/Accuracy-99.5%25-success)

---

## What This Project Does

I built a machine learning model that predicts Boston's daily temperature. Started with 10 years of weather data from 2013-2023 and used linear regression with some feature engineering to get really accurate predictions.

**Results:**
- Testing accuracy: 99.5% (R² = 0.9950)
- Average error: ±0.86°F
- Used 3,988 days of weather data
- Created 18 features from the raw data

### How It Looks

![Predicted vs Actual Temperatures](predicted_vs_actual.png)

The scatter plot shows predictions vs actual temps - most points cluster right on the red line which means the model is working well.

---

## Interesting Findings

The model performs differently across seasons. Fall turned out to be the most predictable, probably because there are fewer storm systems than winter.

![Seasonal Performance](seasonal_performance.png)

| Season | Accuracy | Avg Error |
|--------|----------|-----------|
| Fall | 99.29% | ±0.73°F |
| Spring | 98.81% | ±0.87°F |
| Summer | 98.11% | ±0.70°F |
| Winter | 97.62% | ±1.11°F |

Winter has the most variance - makes sense given how unpredictable Boston winters can be with nor'easters and temperature swings.

### Year-Long Predictions

![Time Series Comparison](time_series_comparison.png)

This shows a full year of predictions. The red line (predictions) tracks the actual temps pretty closely throughout the year.

---

## Tech Stack

- Python 3.x
- Pandas & NumPy for data handling
- Scikit-learn for the ML model
- Matplotlib & Seaborn for visualizations
- Jupyter Notebook

---

## Features I Created

Started with basic weather data and engineered 18 features:

**Lag Variables**
- Yesterday's temp, 3 days ago, last week's temp
- These turned out to be super important since yesterday's weather affects today

**Rolling Averages**
- 7-day and 30-day moving averages
- Helps smooth out day-to-day noise

**Cyclical Encoding**
- Used sin/cos transformations for months and day of year
- This keeps December and January close together mathematically (they're both winter but far apart numerically)

**Weather Variables**
- Temperature (max, min, mean)
- Precipitation
- Wind speed

![Feature Importance](feature_importance.png)

Daily max and min temps ended up being the strongest predictors, followed by seasonal patterns.

---

## Running the Code

Install dependencies:
```bash
pip install pandas numpy scikit-learn matplotlib seaborn requests jupyter
```

Run it:
```bash
git clone https://github.com/VivienneYoo/boston-weather-prediction.git
cd boston-weather-prediction
jupyter notebook boston_weather_model.ipynb
```

Just run all the cells in order. The notebook downloads data, processes everything, trains the model, and generates the plots.

---

## Files in This Repo
```
boston_weather_model.ipynb          # Main notebook
boston_weather_2013_2023.csv        # Weather data
boston_weather_model.pkl            # Saved model
feature_columns.pkl                 # Feature list
PROJECT_SUMMARY.txt                 # Full technical writeup
predicted_vs_actual.png             # Visualizations
time_series_comparison.png
seasonal_performance.png
feature_importance.png
README.md
```

---

## About the Data

Weather data comes from the Open-Meteo API (free historical weather data):
- Location: Boston, MA
- Dates: Jan 1, 2013 - Dec 31, 2023
- Daily measurements of temp, precipitation, wind speed
- API: https://open-meteo.com/en/docs/historical-weather-api

---

## Why Linear Regression?

Could have used more complex models, but linear regression worked really well here and has some advantages:
- Easy to interpret (can see which features matter most)
- Fast to train
- Results are explainable
- No overfitting issues

The training accuracy (99.66%) is really close to testing (99.50%) which means the model generalizes well.

**Performance:**
```
Training R²: 99.66%
Testing R²: 99.50%
RMSE: 1.17°F
MAE: 0.86°F
```

---

## What I Learned

This was my first real machine learning project and I learned a lot:

**Technical stuff:**
- How to handle time series data (can't just shuffle everything)
- Feature engineering is really important
- Creating lag variables and rolling averages
- Cyclical encoding for seasonal patterns

**Insights about the data:**
- Recent weather is the best predictor of current weather
- Fall in Boston is surprisingly stable
- Winter variance probably comes from storm systems moving through
- Daily high and low temps are more important than I expected

**Challenges:**
- Figuring out how to encode months without treating December and January as super far apart
- Dealing with NaN values from lag operations
- Making sure not to leak future data into the training set

---

## Ideas for Improvement

Some things I might try in the future:

- Try LSTM neural networks (good for sequences)
- Add more weather variables like humidity and pressure
- Multi-day forecasting (predict 3 or 7 days ahead)
- Compare Boston to other cities
- Build a simple web app with Streamlit

---

## Project Context

I'm a CS student at Northeastern looking for a co-op position. Built this to practice ML concepts and have something concrete to talk about in interviews. The original idea came from a Codedex house price prediction tutorial, but I adapted it to weather data and added more complex feature engineering.

---

## Contact

**Vivienne YeonSeo Yoo**  
CS Student @ Northeastern University  
Hellman Scholar | Dean's List 

- LinkedIn: www.linkedin.com/in/vivienne-yoo-092547333
- GitHub: https://github.com/VivienneYoo
- Email: yoo.ye@northeastern.edu

---

## License

MIT License - use this however you want for learning!

---

*Project completed October 2025*
