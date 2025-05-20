# Subsurface Porosity & Permeability Prediction Using Machine Learning
This project demonstrates how machine learning—particularly neural networks—can be used to predict porosity and permeability of subsurface rock formations from well log data. These parameters are essential for evaluating reservoir quality and making drilling and production decisions in the oil and gas industry.

# Objectives
  - Load and process LAS wireline log data
  - Visualize and clean the data, including outlier removal
  - Perform feature selection and scaling
  - Cluster geological formations using unsupervised learning (KMeans)
  - Align core analysis (RCAL) data with wireline data
  - Train a neural network model to predict porosity and permeability
  - Apply the model to a new well in the same field

## 1. Data Acquisition and Preparation
I have used LAS files and csv files in this project. Detailed explanation is given below :

  - **Well Log Data (LAS Files):**
      - I have utilised two wireline log files stored in LAS format `well_1.las` and `well_2.las`. They contain depth-indexed measurements collected by downhole logging tools during drilling or post-drilling operations.
      - The LAS files contain multiple columns including `DEPTH`, `GR`, `NPHI`, `RHOB`, `DTC`, `LLD`, `SGR`, `CALI` and so on.
   
  - **RCAL (Routine Core Analysis) Data:**
      - I have used `well_1_rcal.csv` data file, which is a lab-analyzed core plug measurements taken from discrete depths in well_1. These are considered ground truth for training supervised models.
   
  ## 2. Exploratory Data Analysis (EDA): 
  The EDA phase focuses on understanding the structure and quality of data before applying any modeling techniques. Here's what I did : 
  - **Handled missing values:**  Standard null values encoded as -999.25 in LAS files are replaced with actual nulls and dropped to ensure clean input for the next stages.
  - **Visualise data** in Boxplots and Histograms to identify the distribution patterns and detect potential outliers in the logs. This helps uncover skewness, multimodality, and abnormal peaks or spikes.
  - **Outlier detection** is centered around identifying problematic entries in logs like LLD (deep resistivity) and MSFL (shallow resistivity), which commonly contain extremely high or inconsistent values.
  - **Correlation analysis** is used to understand relationships among logs. For example, logs like LLD and LLS or GR and SGR often carry redundant information, and identifying such pairs helps reduce dimensionality and avoid multicollinearity in later stages.

## 3, Feature Selection and Scaling: 
Once the data is clean, the most relevant logs are selected based on their geological and petrophysical significance. This includes:
  - Triple Combo logs: A standard subset used in subsurface analysis, including gamma ray (`GR`), neutron porosity (`NPHI`), bulk density (`RHOB`), sonic travel time (`DTC`), and deep resistivity (`LLD`). Shallow resistivity (`MSFL`) is also retained.
  - To prepare for machine learning, all features are scaled using MinMax normalization, bringing them into the 0,1 range.

## 4. Unsupervised Clustering: 
To explore natural groupings within the subsurface data, KMeans clustering is applied:
  - The **Elbow Method** is used to determine the optimal number of clusters by analyzing the within-cluster sum of squares (WCSS).
  - Based on this analysis, 3 clusters are chosen, which likely correspond to distinct lithofacies or reservoir zones.
  - Clustering results are added to the dataset and visualized using feature-wise boxplots to interpret the petrophysical characteristics of each cluster.

## 5. Core Data Integration: 
The dataset is further enhanced by integrating core laboratory measurements from RCAL, which provides high-accuracy porosity (`HE POR`) and permeability (`KH`) values at discrete depths. A depth alignment algorithm matches these discrete core measurements to the closest log measurement within a ±10 cm tolerance.

## 6. Neural Network Modeling: 
I have trained the pre processed data on a fully connected neural network (FCNN) to learn the mapping between log measurements and core properties.
  - The network includes multiple hidden layers with ReLU activation, and the output layer predicts either porosity alone or both porosity and permeability.
  - The model is trained using Mean Squared Error (MSE) loss and evaluated using training and validation splits.

The trained model is applied to another well in the same field to evaluate its generalizability. Results are visualized on multi-track composite plots alongside the original logs to compare predicted properties with known formation characteristics.



  



        

   
