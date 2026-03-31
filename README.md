# Machine Learning-Based Habitability Analysis of Exoplanets

> A data-driven approach using machine learning to identify Earth-like exoplanets Identification using NASA data

## Project Overview
This project explores the habitability of exoplanets using real-world data from the NASA Exoplanet Archive.

It combines:
Astrophysical reasoning
Machine Learning (Random Forest)
Data analysis & visualization

Goal: Identify **Earth-like planets** and predict their habitability.

---
##Key Concepts
* **Habitable Zone (HZ)** → Region where liquid water can exist
* **Insolation (`pl_insol`)** → Energy received from star (sun)
* **Equilibrium Temperature (`pl_eqt`)** → Estimated planetary temperature
* **Planet Size & Mass** → Determines atmosphere & surface
---

##Dataset
* Source: NASA Exoplanet Archive (PS Table)
* ~6000+ confirmed exoplanets
* Real astrophysical measurements

### Key Features Used
* `pl_orbsmax` → Orbital distance
* `pl_rade` → Planet radius
* `pl_bmasse` → Planet mass
* `pl_eqt` → Temperature
* `pl_insol` → Stellar energy
* `st_teff` → Stellar temperature
---

⚙️ Methodology
1. Data Preprocessing
* Selected relevant columns
* Removed missing values
* Cleaned dataset

---

2. Habitability Filtering

python
df = df[(df['pl_eqt'] > 200) & (df['pl_eqt'] < 350)]
df = df[(df['pl_insol'] > 0.3) & (df['pl_insol'] < 2)]
df = df[(df['pl_rade'] > 0.5) & (df['pl_rade'] < 2)]
3. Habitability Score

```python
df['score'] = (
 abs(df['pl_rade'] - 1) +
 abs(df['pl_bmasse'] - 1) +
 abs(df['pl_eqt'] - 288)/288
)
```

More the Lower score = more Earth-like

4. Machine Learning Model

```python
from sklearn.ensemble import RandomForestRegressor
model = RandomForestRegressor()
model.fit(X_train, y_train)
```

* Model: Random Forest Regressor
* Task: Predict habitability score

---

Visualizations
Exoplanet Distribution

![Distribution](images/distribution.png)

### 🔥 Habitable Zone Candidates

![Habitable Zone](images/habitable_zone.png)

### 🤖 ML Model Performance

![ML Results](images/ml_results.png)

---

## 📈 Results

### 🔍 Key Findings:

* Most planets are too hot or too large
* Only a small fraction fall in habitable conditions
* Temperature & energy are dominant factors

👉 ML model successfully captures nonlinear relationships.

---

## 🧠 Discussion

### ✅ Insights:

* Habitability is multi-factorial
* Distance alone is insufficient
* Stellar properties matter significantly

### ⚠️ Limitations:

* No atmospheric modeling
* Temperature is approximate
* Observational bias exists

---

## 🔮 Future Improvements

* 🌫️ Atmospheric modeling
* 🤖 Deep learning models
* 🔗 Real-time NASA API integration
* 🌍 Climate simulations

---

## 📁 Project Structure

```
exoplanet_project/
│── data/
│── src/
│── models/
│── images/
│── notebooks/
│── README.md
```

---

## 🚀 How to Run

```bash
pip install pandas numpy matplotlib scikit-learn
python src/model.py
python src/predict.py
```

---

## 🎯 Key Takeaways

✔ Real NASA dataset used
✔ Physics + ML combined
✔ Scalable research pipeline
✔ GitHub-ready scientific project

---

## 👨‍🚀 Author

Jeevan Jyoti Rout
---

## ⭐ Acknowledgements

* NASA Exoplanet Archive
* Kepler Mission
* TESS Mission
---

Final Note
> This project demonstrates how **data science + astrophysics + AI** can be combined to explore one of humanity’s biggest questions:
> 🌍 *Are we alone in the universe?*
---
