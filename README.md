# **Traffic Volume Prediction**

## Project Objective
To build a machine learning system that predicts **hourly traffic volume** on highways based on **weather conditions, time factors, and holiday effects**.  
This project demonstrates end-to-end ML skills across **data preprocessing, EDA, feature engineering, regression modeling, time series forecasting, and model evaluation**.

---

## Dataset
**Source:** [Metro Interstate Traffic Volume Dataset (Kaggle)](https://www.kaggle.com/datasets/sobhanmoosavi/us-accidents)  

**Features (independent variables):**
- `holiday` → Whether the day is a holiday or not  
- `temp` → Temperature in Kelvin  
- `rain_1h`, `snow_1h` → Rainfall & snowfall in the past hour (mm)  
- `clouds_all` → Cloud coverage (%)  
- `weather_main`, `weather_description` → Weather categories (Clear, Clouds, Rain, etc.)  
- `date_time` → Timestamp (to extract hour, day, month, weekday, rush hour, season)

**Target (dependent variable):**
- `traffic_volume` → Hourly traffic count

---

## 🛠️ Methodology & Steps
1. **Data Preprocessing**
   - Handle missing values in `holiday` & weather columns  
   - Convert categorical features (`holiday`, `weather_main`, `weather_description`) into numerical (encoding)  
   - Extract datetime features: hour of day, weekday/weekend, month, season, rush hour flag  

2. **Exploratory Data Analysis (EDA)**
   - Visualize traffic patterns (rush hours, weekdays vs weekends, holiday effects)  
   - Study correlation between weather & traffic volume  
   - Detect seasonality and long-term trends  

3. **Feature Engineering**
   - Create cyclical features for time (hour, month)  
   - Create lag features for traffic volume (previous hour/day)  
   - Holiday flag simplification (binary: holiday vs non-holiday)  

4. **Modeling Approaches**
   - **Baseline:** Linear Regression (simple benchmark)  
   - **Tree-based models:** Random Forest, Gradient Boosting (XGBoost/LightGBM)  
   - **Neural Networks:** Feedforward or GRU/LSTM (time-aware models)  
   - **Time Series:** ARIMA/Prophet for forecasting future traffic trends  

5. **Evaluation**
   - Regression metrics: RMSE, MAE, R²  
   - Compare models and justify best performer  

6. **Deployment/Output**
   - Build a small dashboard (e.g., Streamlit) to input weather + date and get predicted traffic volume  
   - Provide insights (best/worst conditions for traffic, rush hour predictions, holiday impact)  

---

## Expected Deliverables
- Cleaned and well-documented dataset  
- EDA visualizations (rush hour curves, weather impact, seasonality plots)  
- Feature engineering notebook  
- Comparison of regression models (baseline vs advanced)  
- Final trained model with performance metrics  
- Optional: Interactive dashboard for predictions  

---

##(Project Flow)

```mermaid
graph TD
    A[Dataset: Traffic Volume + Weather] --> B[Preprocessing & Feature Engineering]
    B --> C[Exploratory Data Analysis]
    C --> D[Baseline Model: Linear Regression]
    C --> E[Advanced Models: Random Forest, Gradient Boosting, Neural Nets]
    E --> F[Model Evaluation & Comparison]
    F --> G[Insights & Dashboard Deployment]
