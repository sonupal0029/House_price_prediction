# House Price Prediction

A machine learning web app that predicts USA house prices from area-level features. It trains 13 regression models, compares their performance, and lets you pick any model in a Flask web interface to get a price prediction.

## Features

- Trains and compares 13 regression models on the same dataset
- Saves each trained model as a `.pkl` file
- Saves evaluation metrics (MAE, MSE, R2) for every model to a CSV
- Flask web app to enter inputs, choose a model, and see the predicted price
- Results page showing the model comparison table

## Models Used

| #  | Model                                | Library      |
| -- | ------------------------------------ | ------------ |
| 1  | Linear Regression                    | scikit-learn |
| 2  | Robust Regression (Huber)            | scikit-learn |
| 3  | Ridge Regression                     | scikit-learn |
| 4  | Lasso Regression                     | scikit-learn |
| 5  | ElasticNet                           | scikit-learn |
| 6  | Polynomial Regression (degree 4)     | scikit-learn |
| 7  | SGD Regressor                        | scikit-learn |
| 8  | ANN (MLPRegressor, 100 hidden units) | scikit-learn |
| 9  | Random Forest                        | scikit-learn |
| 10 | SVM (SVR)                            | scikit-learn |
| 11 | LightGBM                             | lightgbm     |
| 12 | XGBoost                              | xgboost      |
| 13 | KNN                                  | scikit-learn |

## Dataset

`USA_Housing.csv` has 5,000 rows and 7 columns.

| Column                       | Description                              |
| ---------------------------- | ---------------------------------------- |
| Avg. Area Income             | Average income of residents in the area  |
| Avg. Area House Age          | Average age of houses in the area        |
| Avg. Area Number of Rooms    | Average number of rooms per house        |
| Avg. Area Number of Bedrooms | Average number of bedrooms per house     |
| Area Population              | Population of the area                   |
| Price                        | **Target**: house price            |
| Address                      | Dropped before training (text, not used) |

Train/test split: 80% / 20% (`random_state=0`).

## Project Structure

```
house_price_prediction/
├── app.py                         # Flask web app
├── model.py                       # Trains models, saves .pkl files and results CSV
├── USA_Housing.csv                # Dataset
├── model_evaluation_results.csv   # Generated metrics for all models
├── *.pkl                          # Generated trained models
├── templates/
│   ├── index.html                 # Input form + model selection
│   ├── results.html               # Prediction output
│   └── model.html                 # Model comparison table
├── requirements.txt
└── README.md
```

## Installation

```bash
git clone https://github.com/<your-username>/house_price_prediction.git
cd house_price_prediction
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS / Linux
pip install -r requirements.txt
```

## Usage

**1. Train the models** (creates the `.pkl` files and `model_evaluation_results.csv`):

```bash
python model.py
```

**2. Start the web app:**

```bash
python app.py
```

**3. Open** http://127.0.0.1:5000 in your browser, enter the five input values, choose a model, and click predict.

### Routes

| Route        | Method | Description                                      |
| ------------ | ------ | ------------------------------------------------ |
| `/`        | GET    | Home page with the input form                    |
| `/predict` | POST   | Returns the predicted price for the chosen model |
| `/results` | GET    | Table of model evaluation metrics                |

## Evaluation Metrics

- **MAE**: Mean Absolute Error
- **MSE**: Mean Squared Error
- **R2**: Coefficient of determination

See `model_evaluation_results.csv` for the numbers for each model.

## Tech Stack

Python, Flask, pandas, scikit-learn, LightGBM, XGBoost, HTML

## Future Improvements

- Add feature scaling for SVM, KNN, SGD and ANN
- Hyperparameter tuning with GridSearchCV
- Cross-validation instead of a single train/test split
- Deploy to a cloud platform (Render, Heroku, etc.)

## Author

sonupal0029  — [GitHub](<[[https://github.com/your-username<](<%5Bhttps://github.com/your-username%3C>)>>)]([github.com/sonupal0029/House_price_prediction](https://github.com/sonupal0029/House_price_prediction))

## License

MIT License
