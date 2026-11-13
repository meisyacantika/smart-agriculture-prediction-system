\# Smart Agriculture Prediction System



\*\*Efficient Irrigation Management for Smart Farming Using Random Forest and K-Means Clustering\*\*



A Machine Learning-based agricultural data analysis project that applies supervised and unsupervised learning techniques to support data-driven irrigation management within a Smart Farming environment.



The project uses Random Forest Classification to predict irrigation outcomes and K-Means Clustering to identify patterns in agricultural and environmental conditions.



\*\*Project Type:\*\* Academic Group Project  

\*\*My Role:\*\* Machine Learning Developer – Random Forest Modeling \& Evaluation  

\*\*Team Size:\*\* 4 Members  

\*\*Development Period:\*\* June 2026 – July 2026



\---



\## Project Overview



Efficient irrigation management is essential for maintaining agricultural productivity and optimizing water resource utilization.



This project explores the application of Data Mining and Machine Learning techniques to analyze agricultural and environmental conditions using the Smart Agriculture Dataset.



Two machine learning approaches are implemented:



\- \*\*Random Forest Classification:\*\* Predicts irrigation outcome categories based on agricultural and environmental features.

\- \*\*K-Means Clustering:\*\* Identifies groups of agricultural conditions with similar environmental characteristics.



The project also includes data preprocessing, exploratory data analysis (EDA), model evaluation, feature importance analysis, and an interactive web-based prediction demo.



\## Relationship with Smart Farm



This project is related to the broader \*\*Smart Farm\*\* concept, which aims to improve agricultural management through technology, environmental monitoring, and data-driven decision-making.



The Machine Learning component explores how agricultural data can be transformed into predictive insights to support smarter irrigation management.



Its potential role within a Smart Farm ecosystem includes:



\- Analyzing agricultural and environmental data.

\- Identifying irrigation-related patterns.

\- Predicting irrigation outcomes.

\- Grouping similar land conditions through clustering.

\- Supporting agricultural decision-making through predictive analytics.



The current project demonstrates the Machine Learning and prediction component. Integration with real-time IoT sensors and a complete Smart Farm platform remains a potential direction for further development.



\## Project Objectives



\- Perform data cleaning and preprocessing.

\- Conduct Exploratory Data Analysis (EDA).

\- Develop a Random Forest classification model for irrigation prediction.

\- Optimize model parameters using GridSearchCV.

\- Evaluate model performance using classification metrics.

\- Analyze feature importance.

\- Apply K-Means clustering to identify agricultural condition patterns.

\- Deploy an interactive irrigation prediction application using Hugging Face Spaces.



\## Dataset



\*\*Smart Agriculture Dataset – Kaggle\*\*



\[View Original Dataset](https://www.kaggle.com/datasets/chaitanyagopidesi/smart-agriculture-dataset)



The original dataset contains 16,411 records and 7 columns, representing agricultural and environmental information.



\### Dataset Features



| Feature | Description |

|---|---|

| crop ID | Crop category |

| soil\_type | Soil category |

| Seedling Stage | Crop growth stage |

| MOI | Moisture Index |

| temp | Temperature |

| humidity | Humidity level |

| result | Irrigation outcome category |



After data cleaning, 128 duplicate records were removed, resulting in 16,283 records for subsequent analysis.



\## Machine Learning Workflow



\### 1. Data Preprocessing \& Exploratory Data Analysis



The preprocessing stage focuses on preparing the dataset for machine learning implementation.



Activities include:



\- Data understanding and inspection.

\- Checking missing values.

\- Identifying and removing duplicate records.

\- Encoding categorical features.

\- Statistical analysis and data visualization.

\- Feature correlation analysis.



\*\*Dataset after preprocessing:\*\* 16,283 records.



\*\*Notebook:\*\* \[Data Preprocessing \& EDA – Google Colab](https://colab.research.google.com/drive/1r6vxkXALae0PYVHS9gk4AKtU2FMAdpFe?usp=sharing)



\### 2. Random Forest Classification



Random Forest is implemented as a supervised learning algorithm to classify irrigation outcomes based on agricultural and environmental conditions.



The target variable consists of three classes:



| Class | Description |

|---|---|

| 0 | Irrigation Not Required |

| 1 | Irrigation Required |

| 2 | Additional irrigation outcome category (refer to original dataset/report) |



The modeling process includes:



\- Feature and target separation.

\- Stratified Train-Validation-Test splitting (70:15:15).

\- Baseline Random Forest training.

\- Hyperparameter tuning using GridSearchCV.

\- Final model training.

\- Prediction on unseen test data.



\*\*Best Model Parameters:\*\*



| Parameter | Value |

|---|---|

| n\_estimators | 200 |

| max\_depth | 20 |

| class\_weight | balanced |

| random\_state | 42 |

| Cross-validation | 3-fold |

| Best CV Macro F1 | 0.9066 |



\*\*Notebook:\*\* \[Random Forest Model – Google Colab](https://colab.research.google.com/drive/1b7aJfSYhorGllUkXdAG1xV4Gub3kxDbr?usp=sharing)



\### 3. Model Evaluation



The final Random Forest model was evaluated using the test dataset, consisting of 2,443 records.



\*\*Final Test Results:\*\*



| Evaluation Metric | Result |

|---|---:|

| Accuracy | 98.44% |

| Macro Precision | 97.98% |

| Macro Recall | 93.51% |

| Macro F1-Score | 95.50% |



The model also uses a confusion matrix and classification report to analyze prediction performance across individual classes.



\### 4. Feature Importance Analysis



Feature importance analysis was conducted to identify the variables contributing most significantly to the Random Forest model's predictions.



| Feature | Importance |

|---|---:|

| MOI | 42.79% |

| Temperature | 22.36% |

| Humidity | 18.64% |

| Seedling Stage | 9.79% |



MOI was identified as the most influential feature, followed by temperature and humidity.



\### 5. K-Means Clustering



K-Means is implemented as an unsupervised learning technique to identify groups of agricultural conditions with similar characteristics.



The clustering process includes:



\- Selecting MOI, Seedling Stage, and temperature.

\- Standardizing features using StandardScaler.

\- Determining the number of clusters using the Elbow Method.

\- Applying K-Means with three clusters.

\- Evaluating clustering quality using the Silhouette Score.

\- Analyzing cluster centroids.



\*\*Clustering Configuration:\*\*



| Parameter | Value |

|---|---|

| Algorithm | K-Means |

| Number of Clusters | 3 |

| Random State | 42 |

| n\_init | 10 |

| Silhouette Score | 0.3043 |



The resulting clusters provide additional insights into agricultural environmental conditions and potential irrigation management patterns.



\*\*Notebook:\*\* \[K-Means Clustering – Google Colab](https://colab.research.google.com/drive/1cw5Phr\_TIJQXBpMK4T-rvrY8gGFcsCg4?usp=sharing)



\## Live Demo



\*\*\[Crop Irrigation Predictor – Hugging Face Spaces](https://huggingface.co/spaces/Miemey/crop-irrigation-predictor)\*\*



An interactive web application that demonstrates the irrigation prediction functionality of the developed Machine Learning model.



\## Technologies \& Tools



| Technology | Purpose |

|---|---|

| Python | Machine Learning development |

| Pandas | Data manipulation and preprocessing |

| NumPy | Numerical computation |

| Scikit-learn | Random Forest, K-Means, preprocessing, and evaluation |

| Matplotlib | Data visualization |

| Seaborn | Statistical data visualization |

| Joblib | Model serialization |

| Google Colab | Model development and experimentation |

| Hugging Face Spaces | Application deployment |

| Kaggle | Dataset source |



\## My Contributions



As a Machine Learning Developer, my primary responsibilities in this group project included:



\- Developing the Random Forest classification model.

\- Performing stratified training, validation, and testing data splitting.

\- Conducting hyperparameter optimization using GridSearchCV.

\- Evaluating model performance using Accuracy, Precision, Recall, F1-Score, and Confusion Matrix.

\- Performing feature importance analysis.

\- Interpreting and integrating Random Forest experimental results into the project report.



\## Project Documentation



The complete academic report provides detailed information about the research background, methodology, implementation, experimental results, discussion, and conclusions.



\*\*\[View Smart Agriculture Machine Learning Project Report (PDF)](https://drive.google.com/file/d/1RPP7pH0BIAsYrM7TXD4I7FtIBz7QN-FU/view?usp=sharing)\*\*



\## Repository Structure



```text

smart-agriculture-prediction-system/

│

├── notebooks/

│   ├── 01\_data\_preprocessing.ipynb

│   ├── 02\_random\_forest\_model.ipynb

│   └── 03\_kmeans\_clustering.ipynb

│

├── reports/

│   └── Smart\_Agriculture\_Machine\_Learning\_Report.pdf

│

├── screenshots/

│

├── README.md

├── requirements.txt

└── .gitignore

```



\## Acknowledgements



This project was developed collaboratively by four students from the Information Systems Study Program, Faculty of Engineering and Vocational, Universitas Pendidikan Ganesha.



The project was conducted as part of an academic Data Mining course.



\*\*Dataset Source:\*\* \[Smart Agriculture Dataset – Kaggle](https://www.kaggle.com/datasets/chaitanyagopidesi/smart-agriculture-dataset)



\---



\*Academic Group Project | June – July 2026\*

