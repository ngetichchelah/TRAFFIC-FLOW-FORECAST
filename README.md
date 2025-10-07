# **Traffic Volume Prediction**

### **Project Objective**
To build a machine learning system that predicts **hourly traffic volume** on highways based on **weather conditions, temporal factors, and holiday effects**.  

This project demonstrates **end-to-end ML workflow skills**: data preprocessing, EDA, feature engineering, regression modeling, time series forecasting, model evaluation, and insights generation.  

**Purpose:** Compare different forecasting models to determine the best approach for urban planners or traffic managers to anticipate traffic conditions and make informed decisions.

***Presentation:*** 
https://preview--commuter-cognition.lovable.app/

---

### **Dataset**
**Source:** [Metro Interstate Traffic Volume Dataset (UCI)]  

**Features (independent variables):**
- `holiday` → Whether the day is a holiday or not  
- `temp` → Temperature in Kelvin  
- `rain_1h`, `snow_1h` → Rainfall & snowfall in the past hour (mm)  
- `clouds_all` → Cloud coverage (%)  
- `weather_main`, `weather_description` → Weather categories (Clear, Clouds, Rain, etc.)  
- `date_time` → Timestamp (used to extract hour, day, month, weekday, rush hour flag, seasonality)  

**Target (dependent variable):**
- `traffic_volume` → Hourly traffic count

---

### **Methodology/Process**

### ***1. Data Preprocessing***
- Handle missing values for `holiday` & weather columns  
- Convert categorical features (`holiday`, `weather_main`, `weather_description`) into numerical encodings  
- Extract datetime features: hour of day, weekday/weekend, month, season, rush hour flag  
- Convert temperature from Kelvin → Celsius  
- Remove extreme outliers in traffic and weather features  
- Time-based indexing & duplicate removal

### ***2. Exploratory Data Analysis (EDA)***
- Visualize traffic patterns (rush hours, weekdays vs weekends, holiday effects)  
- Study correlations between weather & traffic volume  
- Detect seasonality (daily, weekly, yearly) and long-term trends  

**Key Visualizations:**
1. Traffic volume over time → confirms cyclicality  
2. Average traffic by hour → identifies commuter peaks  
3. Average traffic by day of week → validates weekday patterns  
4. Correlation heatmap → hour/day-of-week highly correlated  
5. Traffic vs weather boxplots → severe weather reduces traffic volume  
6. Distribution plots for traffic, temperature, precipitation, and clouds → show multimodal patterns and data sparsity

### ***3. Feature Engineering***
- Cyclical encoding for temporal features (hour, month)  
- Lag features for traffic volume (1, 24, 168 hours prior)  
- Rolling statistics (mean, std)  
- Simplified holiday flag (binary)  
- Handling missing or skewed weather features for robust model input

### ***4. Modeling Approaches***
#### Classical Time Series
- **ARIMA & SARIMAX**: Capture linear trends & seasonality; SARIMAX includes exogenous weather variables  

#### Ensemble Machine Learning
- **Random Forest** (Tuned): Non-linear tree-based model, handles feature interactions, best performer  
- **Gradient Boosting / XGBoost / LightGBM**: Additional ensemble comparison  

#### Deep Learning
- **LSTM & GRU Networks**: Capture sequential dependencies in traffic volume  

**Key Modeling Insights:**
- Random Forest achieved **Test R² ≈ 0.983**, minimal overfitting gap (0.007)  
- GRU achieved **R² ≈ 0.9818**, converged 25% faster than LSTM  
- Classical TS models underperformed on non-linear, multi-scale patterns  

### ***5. Model Evaluation***
- Metrics: RMSE, MAE, R², overfitting gap  
- Visual comparisons: forecast vs actual traffic, model convergence plots  
- Feature importance analysis for tree-based models

### ***6. Deployment / Output***
- Optional dashboard (e.g., Streamlit) for inputting weather + date and receiving predicted traffic volume  
- Insights: optimal/worst traffic conditions, rush hour predictions, holiday impact  

---

### **Expected Deliverables**
- Cleaned dataset with engineered features  
- EDA visualizations (rush hour curves, weather impact, seasonality plots)  
- Feature engineering notebook  
- Model comparison: baseline vs advanced models  
- Trained models with performance metrics  

---

**Key Insights & Project Conclusions**
1. Feature Engineering is Critical: Lag features, rolling statistics, and cyclical encoding often mattered more than model complexity.
2. Random Forest Won: Best accuracy, interpretability, and fast training (~5 min vs 45 min for GRU).
3. Deep Learning Viable but Costly: GRU matched RF performance but required more computation.
4. Classical Time Series Models Limitations: Struggle with non-linear multi-scale traffic patterns.
5. Societal Impact: Enables proactive traffic management, reduces congestion, supports city planning, and improves commuter decision-making.

**Technology Stack**
- Python 3.8+
- Libraries: NumPy, Pandas, Scikit-learn, TensorFlow/Keras, XGBoost, Matplotlib/Seaborn, SciPy
- Visualization: Plotly, Seaborn, Matplotlib

**Installation Steps**
1. Clone repository:
git clone <repository-url>
cd traffic-volume-prediction
2. Create virtual environment:
python -m venv venv
source venv/bin/activate (Windows: venv\Scripts\activate)
3. Install dependencies:
pip install -r requirements.txt
4. Place dataset in data/ folder
5. Run notebooks to reproduce analysis and forecasts

**Acknowledgments**
- UCI for Metro Interstate Traffic Volume dataset

### ***Project Flow***

graph TD
    A[Dataset: Traffic Volume + Weather] --> B[Preprocessing & Feature Engineering]
    B --> C[Exploratory Data Analysis]
    C --> D[Baseline Model: Linear Regression]
    C --> E[Advanced Models: Random Forest, Gradient Boosting, Neural Nets, LSTM/GRU]
    E --> F[Model Evaluation & Comparison]
    F --> G[Insights & Project Conclusion]

----
