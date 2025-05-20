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
  
  



        

   
