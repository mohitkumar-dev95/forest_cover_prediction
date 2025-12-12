# 🌲 Forest Cover Type Prediction (Multiclass Classification)

This project predicts the **forest cover type** (7 different classes) using environmental and geographical attributes from the Forest Cover Type dataset. The task is a **multinomial classification problem** solved using **Logistic Regression**, **Linear SVM**, and a **Neural Network (MLPClassifier)**.

Advanced **feature engineering**, **data preprocessing**, and **model comparison** were performed to build an efficient prediction pipeline.

---

## 👨‍💻 Contributors


- **Mohit Kumar (MT2025075)**

GitHub Links:  

- Mohit: https://github.com/mohitkumar-dev95/forest_cover_prediction  

---

## 📁 Repository Structure



---

## 📊 Dataset Overview

- **Total samples:** 210,896  
- **Features:** 54 numerical columns (after cleaning)  
- **Target:** `Cover_Type` (7 unique classes)  
- **Missing values:** Only **1 row** had missing values → removed  

Final dataset size: **210,895 rows × 54 features**

---

## 🧪 Exploratory Data Analysis (EDA)

Key insights:

- Dataset consists mostly of **float64 features** (49 columns) with some int64 features.
- Only 1 row contained missing values across multiple columns → removed.
- The target variable `Cover_Type` is **multiclass** and slightly imbalanced.
- Environmental factors (Elevation, Slope, Aspect, Hillshade, Soil Type) contribute strongly to class separation.

---

## 🛠 Feature Engineering

New informative features were added to capture spatial, topographical, and cyclical relationships:

### Engineered Features:

| Feature | Description |
|--------|-------------|
| **Euclidean_Distance_To_Hydrology** | sqrt(horizontal² + vertical²) |
| **Aspect_sin / Aspect_cos** | Circular encoding of Aspect |
| **Hillshade_Diff** | Hillshade_9am − Hillshade_3pm |
| **Elevation_Slope_Interaction** | Elevation × Slope |

### Why These Features?

- Hydrology distance improves ecological relevance.  
- Aspect is cyclic → sin/cos avoids wrong linear interpretation.  
- Hillshade differences capture slope orientation.  
- Interaction terms capture complex vegetation–terrain relationships.

---

## 🧹 Data Preprocessing

### 1. Handling Missing Values
- Only 1 row had missing values → dropped.

### 2. Feature & Target Split


Stratification preserved label distribution in both splits.

---

## 🤖 Model Building

Three models were trained and compared:

---

### 1️⃣ Logistic Regression (Multinomial)

Key Parameters:



Performance:
- **Accuracy:** 0.7614  
- Strong recall for majority classes  
- Very poor recall for minority classes (e.g., Class 5: recall 0.17)  
- Linear decision boundary insufficient for complex relationships

---

### 3️⃣ Neural Network (MLPClassifier) — ⭐ Best Model

Architecture:



Training:
- Early stopping triggered at **Iteration 190**
- Prevented overfitting  
- Stable convergence  

Performance:
- **Accuracy:** 0.8878 (Best)  
- Strong precision, recall, and F1 across most classes  
- Handled non-linear relationships effectively  

---

## 📈 Model Comparison

| Model | Accuracy |
|--------|----------|
| Logistic Regression | 0.7699 |
| Linear SVM | 0.7614 |
| **Neural Network (MLPClassifier)** | **0.8878** |

✔ Neural Network significantly outperformed linear models  
✔ Linear models struggled with class imbalance  
✔ Neural Network captured non-linear terrain–environment interactions

---

## 🧮 Evaluation Metrics

The following metrics were used:

### Accuracy
How many predictions were correct overall.

### Precision
Out of predicted cover types → how many were correct.

### Recall
Out of actual cover types → how many were detected correctly.

### F1-Score
Balances precision and recall; useful for imbalanced classes.

---

## 🏁 Final Summary & Conclusion

- Data was cleaned, feature engineered, scaled, and split properly.
- Three models were trained: Logistic Regression, Linear SVM, and Neural Network.
- The **Neural Network (MLPClassifier)** achieved the **best overall performance** with **88.78% accuracy**.
- Linear models were limited due to dataset complexity and class imbalance.
- Neural Network captured non-linear ecological relationships more effectively.

### 🚀 Future Work
- Hyperparameter tuning for Neural Network  
- Try non-linear SVM kernels (RBF, polynomial)  
- Apply SMOTE or class-weight adjustments  
- Experiment with deeper neural architectures  
- Add tree-based models (Random Forest, XGBoost) for comparison  

---

## 🔧 How to Run

```bash
# Clone repository
git clone <your-repo-url>

# Install dependencies
pip install -r requirements.txt

# Run model training
python src/train.py


