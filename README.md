# **Predictive Analysis and Enhanced Prediction for AQI**

This repository presents an **advanced air quality prediction system** that utilizes **deep learning techniques** to analyze and forecast **PM2.5 concentrations**. The project is structured around **two key aspects**:  

1️⃣ **Data Visualization**: Understanding the complex relationships between air pollutants and meteorological factors.  
2️⃣ **Prediction Model**: Implementing a **hybrid LSTM-FCNN model** to enhance air quality forecasting accuracy.  

## **📌 Dataset Selection & Preprocessing**
### **1️⃣ Dataset Source & Selection Criteria**  
- Data was collected from the **Central Pollution Control Board (CPCB) (2010-2023)** covering **453 cities** in India.  
- Focused analysis on **Tamil Nadu**, selecting **26 locations**, classified into:
  - **Urban zones** – higher vehicle emissions, commercial density.
  - **Industrial zones** – higher NH3, SO2 emissions from factories.
  - **Residential zones** – relatively lower pollution levels.

- **Three locations in Chennai** were chosen for in-depth analysis, each representing one of the above zones.

### **2️⃣ Feature Selection**
The dataset contains **both pollutant concentrations and meteorological parameters**:

#### **Air Pollutants:**
- **PM2.5, PM10** – Primary indicators of air quality.
- **NO2, SO2, NH3, CO** – Gaseous pollutants affecting respiratory health.

#### **Meteorological Features:**
- **Temperature, Humidity, Wind Speed, Solar Radiation, Atmospheric Pressure.**

### **3️⃣ Handling Missing Values**
- **KNN Imputation** was used for estimating missing values, ensuring dataset consistency.

### **4️⃣ Data Transformation**
- **Hourly pollutant data aggregated into daily averages**.
- **Min-Max Scaling** was applied to normalize pollutant concentration values.

## **📊 Data Visualization: Understanding Air Quality Trends**
Before making predictions, we conducted a thorough **data visualization analysis** to understand **pollution patterns and meteorological influences**.

### **1️⃣ Pollutant Contributions in Different Zones**  
**Visualization: Pie Charts**  
These charts represent the **average contribution of pollutants (PM2.5, PM10, NO, NO2, NH3, SO2, CO)** across **urban, industrial, and residential zones**.

#### **Key Insights:**
- **PM10 and PM2.5 are dominant across all zones**, indicating widespread particulate matter pollution.
- **Industrial zones have higher NH3 and SO2 concentrations**, suggesting emissions from **factories and chemical processing units**.
- **Urban zones exhibit higher NO2 and CO levels**, largely attributed to **vehicular emissions**.
- **Residential zones have comparatively lower pollutant concentrations**, but PM2.5 levels remain a concern.

![image](https://github.com/user-attachments/assets/b2b4b2fc-a27e-436b-ad37-12924e049411)
![image](https://github.com/user-attachments/assets/e74405f4-3f24-4923-bfb3-57d1282f8f7e)
![image](https://github.com/user-attachments/assets/c3bd90ab-7145-4096-8aee-38e997ec1965)

### **2️⃣ Annual Trends in PM2.5 and PM10 Levels**  
**Visualization: Line Charts**  
These graphs illustrate **yearly trends in PM2.5 and PM10** levels across different zones.

#### **Key Insights:**
- **PM levels are steadily rising over the years**, indicating increasing pollution levels.
- **Urban areas show seasonal spikes**, especially in winter, due to **low dispersion rates**.
- **Industrial areas maintain consistently high PM concentrations**, highlighting **ongoing emissions from manufacturing activities**.

![image](https://github.com/user-attachments/assets/05480a48-559e-4b75-90ab-045336908ad2)

### **3️⃣ Relationship Between Meteorological Factors & Pollutants**  
**Visualization: Heatmaps & Stacked Area Charts**  

#### **Heatmaps: Pollutant-Meteorology Correlation**  
- Show **correlations between air pollutants and meteorological conditions**.
- Helps identify how weather conditions influence pollutant dispersion.

#### **Key Insights:**
- **Higher temperatures correlate with increased NH3 levels**, possibly due to **volatility of ammonia-based emissions**.
- **Humidity negatively correlates with SO2 and CO**, suggesting moisture contributes to **pollutant absorption**.
- **Wind speed inversely impacts PM2.5 levels**, indicating **higher wind disperses pollutants more effectively**.

#### **Stacked Area Charts: Seasonal Pollutant Variations**
- Visual representation of **how pollutants interact over time with meteorological conditions**.
- **Key Insight**: **Solar radiation influences NO2 and O3 formation**, indicating photochemical smog formation.

![image](https://github.com/user-attachments/assets/45b85728-c69b-4251-beb1-93cdf7a5debb)
![image](https://github.com/user-attachments/assets/b772ae86-38db-490f-bee6-8af982c2daaf)
![image](https://github.com/user-attachments/assets/63afe0ff-b7ac-4263-ace0-662ad6cffe7c)

## **📈 Prediction**
The **LSTM-FCNN hybrid model** is an advanced deep learning architecture designed for **air quality prediction**. This model combines two powerful neural network components:  

1️⃣ **Long Short-Term Memory (LSTM)** – Captures **temporal dependencies** in pollution data.  
2️⃣ **Fully Connected Neural Network (FCNN)** – Models **feature interactions** and refines predictions.  

This combination allows for **accurate forecasting of PM2.5 concentrations** by leveraging both **time-series patterns** and **environmental influences**.

# **Why LSTM-FCNN Instead of a Normal Regression Model?**
Air quality prediction is **not a simple regression problem** because pollution levels depend on **both past trends (temporal dependencies) and environmental interactions (non-linear dependencies).** The **LSTM-FCNN hybrid model** is specifically designed to handle these complexities, making it superior to traditional regression models.

### **1️⃣ Time-Dependency (Temporal Aspect)**
- **Air pollution fluctuates over time** due to meteorological conditions (temperature, wind, humidity) and external factors (seasonal changes, industrial activity).
- Traditional regression assumes **each data point is independent**, ignoring past trends that influence future pollution levels.
- **LSTM (Long Short-Term Memory)** networks excel at capturing **sequential patterns** and **long-term dependencies** in time-series data.

**Example:**  
If PM2.5 is high today, it’s likely to remain high tomorrow unless significant meteorological changes occur. **LSTM remembers past trends and uses them for forecasting.**  

### **2️⃣ Complex Interactions (Non-Linear Dependencies)**
- PM2.5 concentration is influenced by **multiple factors** (temperature, wind speed, humidity, etc.).
- Linear regression assumes a **fixed relationship** (e.g., PM2.5 increases by X when temperature drops by Y), which is too simplistic.
- **FCNN (Fully Connected Neural Network)** learns **non-linear interactions** between meteorological features and pollutant concentrations.

**Example:**  
- **Low wind speed & high humidity** → PM2.5 increases (pollutants stay in the air longer).  
- **High wind speed & low humidity** → PM2.5 decreases (pollutants disperse quickly).  
These **interactions are not linear** and require FCNN to model the relationships effectively.

## **📌 Why LSTM + FCNN Instead of Just LSTM?**
While **LSTM captures temporal patterns**, it **doesn’t model complex feature interactions** effectively. That’s where **FCNN enhances the prediction process**.

### **How the LSTM-FCNN Hybrid Works:**
1. **LSTM processes the time-series sequence** and learns how pollution levels change over time.  
2. **FCNN refines the LSTM outputs** by considering **feature interactions** (e.g., how temperature & humidity together impact PM2.5).  
3. **The combined model generates highly accurate predictions**, capturing both **past pollution trends (LSTM)** and **current environmental influences (FCNN).**  

**Example:**  
- LSTM predicts that **PM2.5 will be high tomorrow** based on past pollution levels.  
- FCNN adjusts the prediction by considering **weather conditions**—if strong winds are forecasted, it lowers the PM2.5 estimate because **pollutants will disperse faster.**  

## **📌 LSTM-FCNN Model Architecture**
The **LSTM-FCNN model** consists of several layers:

1️⃣ **LSTM Network**  
   - **Input:** Sequence of past PM2.5 values.  
   - **Hidden state:** Stores learned pollution trends.  
   - **Output:** Time-dependent pollution forecast.  

2️⃣ **FCNN Layers**  
   - **Input:** LSTM output + meteorological features.  
   - **Hidden Layers:** Fully connected layers with **ReLU activation** for feature learning.  
   - **Output Layer:** Final PM2.5 prediction.  

## **⚡ Optimizer Performance Analysis**
### **Why Optimizer Selection is Crucial**
The choice of **optimizer** significantly impacts **convergence speed and accuracy**. Multiple optimizers were tested:

| **Optimizer** | **Learning Rate Adaptability** | **Best Use Case** |
|--------------|------------------------------|-------------------|
| **Adam**      | Adaptive learning rate      | Balances speed & accuracy |
| **RMSprop**   | Scales gradient updates     | Works well for time-series |
| **SGD**       | Fixed learning rate         | Good for simple models |
| **Adadelta**  | No manual tuning required  | Works well with noisy data |
| **Adagrad**   | Adapts learning per feature | Best for sparse data |
| **Adamax**    | Generalization-focused     | Stable training |

![rmse optimizers](https://github.com/user-attachments/assets/7e4dccdc-b832-4b30-bb74-f3aaa8adad3d)

### **Final Results: Best Optimizer for LSTM-FCNN**
| **Model**               | **RMSE**  | **MSE**   | **MAE**  | **MAPE**  |
|--------------------------|-----------|-----------|-----------|-----------|
| **LSTM**                 | 28.799    | 829.43    | 18.431    | 48.127    |
| **FCNN**                 | 27.894    | 786.304   | 17.660    | 46.648    |
| **LSTM-FCNN (RMSprop)**  | **27.496** | **783.819** | **17.167** | **40.817** |

![acPr](https://github.com/user-attachments/assets/ae16faa1-bb0b-4e42-bf96-2d32fdf469d3)

![model loss](https://github.com/user-attachments/assets/5dbcdec3-d73f-4d30-9237-1a19e46f5f9f)

✅ **RMSprop optimizer yielded the best performance**, minimizing RMSE to **27.496**.  
✅ **Adam performed well but was slightly slower in convergence**.  
✅ **SGD struggled due to inconsistent gradient updates in time-series data**.  

## **📌 Future Enhancements**
📍 **Real-time IoT sensor integration** for live air quality monitoring.  
📍 **Incorporate Ozone (O3), VOCs, and CO2** for broader air quality forecasting.  
📍 **Deploy as an API or Web App** for real-time user access.  

## **📈 Comparison: LSTM-FCNN vs. Normal Regression**

| **Aspect**               | **Traditional Regression** | **LSTM-FCNN** |
|--------------------------|---------------------------|--------------|
| **Captures time-series trends** | ❌ No | ✅ Yes (LSTM remembers past values) |
| **Handles non-linear interactions** | ❌ No (Assumes fixed relationships) | ✅ Yes (FCNN learns complex patterns) |
| **Considers external meteorological factors** | ✅ Limited | ✅ Yes (FCNN models impact of weather) |
| **Adapts to seasonal variations** | ❌ No | ✅ Yes (LSTM captures seasonal changes) |
| **Handles missing & noisy data** | ❌ No | ✅ Yes (Deep learning models generalize better) |

## **📌 Conclusion: Why LSTM-FCNN is the Best Choice**
1. **Captures both time-series trends (LSTM) and complex feature interactions (FCNN).**  
2. **Adapts to real-world pollution dynamics, unlike traditional regression models.**  
3. **Achieves lower RMSE and higher prediction accuracy compared to standalone LSTM or regression models.**  

🚀 **LSTM-FCNN is designed to model real-world air quality variations, making it the optimal choice over traditional regression techniques!**  
