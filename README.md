# Smart Agriculture Prediction System

**Efficient Irrigation Management for Smart Farming Using Random Forest and K-Means Clustering**

A machine learning project that analyzes agricultural and environmental data to support data-driven irrigation management. The project combines **Random Forest Classification** to predict irrigation outcome categories and **K-Means Clustering** to explore groups of similar agricultural conditions.

**Project type:** Academic group project  
**My role:** Machine Learning Developer — Random Forest Modeling and Evaluation  
**Team size:** 4 members  
**Development period:** June–July 2026

---

## Project Overview

Irrigation decisions are often made using manual observations or fixed schedules, which may not reflect changes in soil moisture and environmental conditions. This project explores how machine learning can analyze agricultural data and provide insights to support irrigation-related decision-making.

The project has two main analytical components:

- **Random Forest Classification (supervised learning):** predicts irrigation outcome categories from crop, soil, plant-growth, and environmental features.
- **K-Means Clustering (unsupervised learning):** groups observations with similar land and environmental conditions.

The workflow also covers data preprocessing, exploratory data analysis (EDA), model evaluation, feature-importance analysis, and an interactive prediction interface deployed on Hugging Face Spaces.

## Dataset

The project uses the [Smart Agriculture Dataset on Kaggle](https://www.kaggle.com/datasets/chaitanyagopidesi/smart-agriculture-dataset).

The original dataset contains **16,411 records** and **7 attributes**.

| Attribute | Description | Type |
|---|---|---|
| `crop ID` | Crop category | Categorical |
| `soil_type` | Soil category | Categorical |
| `Seedling Stage` | Crop growth stage | Categorical / ordinal |
| `MOI` | Moisture Index | Numerical |
| `temp` | Environmental temperature (°C) | Numerical |
| `humidity` | Relative humidity (%) | Numerical |
| `result` | Irrigation outcome category | Target |

After duplicate removal, the cleaned dataset contains **16,283 records**.

## Machine Learning Workflow

### 1. Data Cleaning and Preprocessing

The preprocessing stage prepares the dataset for machine learning:

- Checked the dataset for missing values. The report records no missing values across the seven attributes.
- Identified and removed **128 duplicate records**, reducing the dataset from 16,411 to 16,283 rows.
- Checked numerical attributes (`MOI`, `temp`, and `humidity`) for outliers using the Interquartile Range (IQR) method. The report records no outliers under the selected 1.5 × IQR thresholds.
- Applied **One-Hot Encoding** to the nominal `crop ID` and `soil_type` attributes.
- Applied **Label Encoding** to the ordinal `Seedling Stage` attribute.
- Kept `MOI`, `temp`, and `humidity` as numerical features without categorical encoding.

The resulting modeling dataset contains **16,283 rows and 17 columns**: 16 processed input features and 1 target column (`result`).

**Notebook:** [Data Preprocessing and EDA — Google Colab](https://colab.research.google.com/drive/1r6vxkXALae0PYVHS9gk4AKtU2FMAdpFe?usp=sharing)

### 2. Random Forest Classification

Random Forest was used as a supervised classification algorithm to predict the `result` target from the processed agricultural and environmental features.

The target contains three classes:

| Class | Meaning in the report |
|---|---|
| 0 | No Irrigation Needed |
| 1 | Irrigation Needed |
| 2 | Class 2 — the report and dataset do not provide a more descriptive label |

The modeling workflow used a stratified **70:15:15 train-validation-test split** to preserve the class distribution across the data subsets.

| Dataset split | Records | Proportion |
|---|---:|---:|
| Training | 11,398 | 70% |
| Validation | 2,442 | 15% |
| Test | 2,443 | 15% |
| **Total** | **16,283** | **100%** |

Hyperparameter tuning was performed using **GridSearchCV** with 3-fold cross-validation and macro F1-score as the optimization metric.

**Best model configuration reported:**

| Parameter | Value |
|---|---:|
| `n_estimators` | 200 |
| `max_depth` | 20 |
| `class_weight` | `balanced` |
| `random_state` | 42 |
| Cross-validation | 3-fold |
| Best CV Macro F1-score | 0.9066 |

**Notebook:** [Random Forest Model — Google Colab](https://colab.research.google.com/drive/1b7aJfSYhorGllUkXdAG1xV4Gub3kxDbr?usp=sharing)

### 3. Model Evaluation

The selected model was retrained using the combined training and validation data (13,840 records), then evaluated on the **2,443-record test set**, which was not used during training or hyperparameter tuning.

**Final test-set results:**

| Evaluation metric | Score |
|---|---:|
| Accuracy | **98.44%** |
| Macro Precision | **97.98%** |
| Macro Recall | **93.51%** |
| Macro F1-score | **95.50%** |

The evaluation also used a classification report and confusion matrix to examine performance across the three classes.

**Test-set confusion matrix** (rows = actual class, columns = predicted class):

| Actual \ Predicted | Class 0 | Class 1 | Class 2 |
|---|---:|---:|---:|
| Class 0 | 1,337 | 2 | 1 |
| Class 1 | 0 | 931 | 3 |
| Class 2 | 11 | 21 | 137 |

Class 2 is the minority class in the dataset. On the test set, it achieved a recall of **81.07%** and an F1-score of **88.39%**; its results are reported separately to make the class imbalance visible rather than relying on accuracy alone.

### 4. Feature Importance Analysis

Feature importance was analyzed to identify which inputs contributed most to the Random Forest model's predictions.

| Feature | Importance |
|---|---:|
| MOI | **42.79%** |
| Temperature | **22.36%** |
| Humidity | **18.64%** |
| Seedling Stage | **9.79%** |

MOI was the most influential feature, followed by temperature and humidity. The report also notes that the individual encoded crop and soil categories each contributed less than 1.2%.

These values represent the model's feature-importance scores; they describe how the fitted model used the features and should not be interpreted as proof of causal relationships.

### 5. K-Means Clustering

K-Means was included as the project's unsupervised learning component to group agricultural observations with similar environmental characteristics.

The clustering workflow used `MOI`, `Seedling Stage`, and `temp`, standardized the selected features with `StandardScaler`, and evaluated three clusters.

| Configuration | Value |
|---|---:|
| Number of clusters | 3 |
| `random_state` | 42 |
| `n_init` | 10 |
| Silhouette score | 0.3043 |

**Notebook:** [K-Means Clustering — Google Colab](https://colab.research.google.com/drive/1cw5Phr_TIJQXBpMK4T-rvrY8gGFcsCg4?usp=sharing)

## Live Demo

**[Crop Irrigation Predictor — Hugging Face Spaces](https://huggingface.co/spaces/Miemey/crop-irrigation-predictor)**

The project includes an interactive web interface that demonstrates irrigation prediction using the developed machine learning model.

## Technologies and Tools

| Technology / Tool | Purpose |
|---|---|
| Python | Machine learning development |
| Pandas | Data manipulation and preprocessing |
| NumPy | Numerical computation |
| Scikit-learn | Encoding, Random Forest, K-Means, model tuning, and evaluation |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Google Colab | Notebook-based development and experimentation |
| Hugging Face Spaces | Deployment of the interactive prediction interface |
| Kaggle | Dataset source |

## My Contributions

My contributions to the project, reflected in my CV, include:

- Performed data cleaning and preprocessing, including duplicate removal and categorical encoding.
- Developed a Random Forest model to predict irrigation requirements using agricultural and environmental data.
- Evaluated model performance using accuracy, precision, recall, F1-score, and confusion matrix.
- Analyzed feature importance to identify the most influential predictors of irrigation outcomes.
- Developed and deployed an interactive web interface for the prediction demo on Hugging Face Spaces.

## Project Scope and Limitations

- The analysis is based on the historical Smart Agriculture Dataset; it does not use live readings from deployed agricultural sensors.
- The project focuses on prediction and analysis. It does not implement automated control of physical irrigation pumps or valves.
- The source report identifies Class 0 and Class 1 as irrigation outcome labels but refers to the third target category only as Class 2. This README keeps that label unchanged rather than assigning an unsupported interpretation.

## Project Documentation

The full report describes the dataset, preprocessing process, methodology, model experiments, evaluation, feature-importance analysis, clustering results, and project limitations.

**[Smart Agriculture Machine Learning Project Report (PDF)](https://drive.google.com/file/d/1RPP7pH0BIAsYrM7TXD4I7FtIBz7QN-FU/view?usp=sharing)**

## Acknowledgements

This academic group project was developed by four students from the Information Systems Study Program, Faculty of Engineering and Vocational, Universitas Pendidikan Ganesha, as part of a Data Mining course.

**Dataset:** [Smart Agriculture Dataset — Kaggle](https://www.kaggle.com/datasets/chaitanyagopidesi/smart-agriculture-dataset)

---

*Academic Group Project | June–July 2026*
