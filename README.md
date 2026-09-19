# Medical Insurance Cost Prediction

A simple web app that estimates annual medical insurance charges using a Multiple Linear Regression model, trained on the [Medical Cost Personal Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance) (1,338 records: age, sex, BMI, children, smoker status, region).

**Live demo:** https://misbahahmad2.github.io/Medical-Insurance-Cost-Prediction/

## How it works

The model was trained in Python using `scikit-learn`'s `LinearRegression`, achieving an **R² of 0.81** on held-out test data. The app is a single static HTML/CSS/JS page — the trained model's coefficients and intercept are embedded directly in the JavaScript, so predictions are calculated instantly in the browser with no backend or server required.

| Metric | Value |
|---|---|
| MAE | ~$4,177 |
| RMSE | ~$5,956 |
| R² Score | 0.81 |

## Features

- Sliders for age, BMI, and number of children
- Toggles for gender and smoking status
- Dropdown for region
- Live prediction that updates instantly as inputs change
- A breakdown of how each feature contributes to the final estimate

## Tech stack

- Python (`pandas`, `scikit-learn`) — data cleaning, EDA, and model training
- HTML/CSS/JavaScript — the deployed prediction interface

## Running locally

No build step or dependencies needed. Clone the repo and open `index.html` in any browser:

```bash
git clone https://github.com/MisbahAhmad2/Medical-Insurance-Cost-Prediction.git
cd Medical-Insurance-Cost-Prediction
open index.html   # or just double-click the file
```

## Deploying on GitHub Pages

1. Push this repo to GitHub.
2. Go to **Settings → Pages** in your repository.
3. Under **Source**, select the `main` branch and `/ (root)` folder.
4. Save — your site will be live at `https://misbahahmad2.github.io/Medical-Insurance-Cost-Prediction/` within a minute or two.

## Model training

The model was trained on the Medical Cost Personal Dataset using:
- `sex` and `smoker` mapped to binary values
- `region` one-hot encoded (with `northeast` as the baseline category)
- An 80/20 train/test split (`random_state=42`)

## Limitations

- **Linear model, non-linear reality:** the model assumes each feature adds a fixed amount to the cost independently. In practice, smoking and high BMI interact and compound each other's effect on charges, which a straight-line model can't fully capture. This shows up as larger errors on high-cost smoker cases (see the RMSE vs. MAE gap above).
- **Missing real-world factors:** the dataset doesn't include pre-existing conditions, family medical history, occupation, or income, all of which affect real insurance pricing.
- **US-only, dated dataset:** the data reflects a US insurance market and is not regional or currency-adjusted, so it wouldn't generalize directly to other countries' pricing systems.
- **Small dataset:** 1,337 records is enough for a class project but small by real-world underwriting standards.
- **Not a real quote:** this tool is for educational/demonstration purposes only. It should not be used to estimate actual insurance premiums or make financial decisions.

## Disclaimer

This is a student/portfolio project for educational purposes. Estimates are based on a public dataset and a simple linear model — they are not actual insurance quotes.
