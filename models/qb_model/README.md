# QB Fantasy Football Model

## Model Information
- **Model Type**: LinearRegression
- **Target Variable**: fantasy_points_ppr
- **Training Data**: 89 samples
- **Test Data**: 23 samples
- **Data Years**: 2022, 2023, 2024

## Performance Metrics
- **R² Score**: 0.976
- **RMSE**: 17.82
- **MAE**: 14.52
- **Cross-Validation R²**: 0.951 ± 0.012

## Features Used
- pass_touchdown
- season_average_fantasy_points_ppr
- rushing_yards

## Model Coefficients
- pass_touchdown: 87.791
- season_average_fantasy_points_ppr: 10.387
- rushing_yards: 34.304
- Intercept: 242.506

## Files in this Directory
- `qb_model_package.joblib`: Complete model package (recommended for loading)
- `qb_model.joblib`: Individual model object
- `qb_scaler.joblib`: Individual scaler object
- `qb_model_metadata.json`: Model metadata and performance metrics
- `README.md`: This documentation file

## Usage Example
```python
import joblib

# Load complete model package
qb_model_pkg = joblib.load('qb_model_package.joblib')

# Make prediction
def predict_qb_points(pass_td, season_avg_ppr, rush_yards):
    input_data = np.array([[pass_td, season_avg_ppr, rush_yards]])
    if qb_model_pkg['model_type'] == 'LinearRegression':
        input_scaled = qb_model_pkg['scaler'].transform(input_data)
        return qb_model_pkg['model'].predict(input_scaled)[0]
    else:
        return qb_model_pkg['model'].predict(input_data)[0]

# Example prediction
predicted_points = predict_qb_points(25, 20, 300)
```

## Model Created
2025-08-26 17:59:01
