This repository contains the MATLAB code, experimental datasets, and simulation resources accompanying the article:

“Tactile Perception through Fluid–Solid Interaction”
_(Nature Communications, 2026)_


# **Raw Data Processing**

The Raw Data Processing folder includes MATLAB scripts used to process raw analog sensor signals and experimental force data to generate features and labels for machine learning.

The provided MATLAB scripts:
- Process raw analog signals from the sensor
- Extract input features from pressure signals
- Process experimental force measurements to generate labels

**Processing pipeline**
1. Remove baseline offset from raw signals
2. Extract from sensor signals
   - Maximum pressure (peak value)
   - Rise time (time to peak)
3. Extract from experimental data
   - Maximum force (used as label)

**Example datasets are provided for:**

- 1D preliminary results for all 3 media

- 2D preliminary results for oil-filled sensor

- Underwater 1D sensor

**How to use**

1. Add the folder to MATLAB path:
   ```matlab
   addpath(genpath('Raw_Data_Processing'));
2. Load an example dataset loaded in preliminary or underewater folder:
   ```matlab
   data = readmatrix('example_dataset.mat');
3. Run the processing script
   ```matlab
   process_raw_data

# **Machine Learning**

The Machine Learning folder contains MATLAB code used to map sensor signals to position and force using a combination of Fuzzy C-Means (FCM) clustering and Adaptive Neuro-Fuzzy Inference System (ANFIS).
A detailed description of the model is provided in Supplementary Information S11 of the paper.

The MATLAB script: 
- Learns the relationship between pressure values (input) and force and position (outputs)
- Predicts:
   - Position (X, X-Y, or Hilbert index)
   - Force (F)
- Supports both 1D and 2D sensor


**Workflow**
1. Select sensor type (1D or 2D)
2. Select dataset (provided in this folder)
3. Define the number of clusters (FCM)
4. Train FIS model using ANFIS
5. Evaluate model performance (regression + RMSE)
6. Save trained models

**Included data**

Example datasets are provided in this folder and correspond to those used in the paper:
- 1D sensor (all data)
- 2D sensor (60×60 sample)

**How to run**
      
3. Run the processing script
   ```matlab
   addpath(genpath('Learning'));
   run('main_training_script.m')   % replace with your script name

Then:
- Select 1D or 2D sensor
- Choose one of the provided .xlsx dataset
- Enter the number of clusters when prompt

**Output**
- Trained FSI models (.mat and  .fis files)
- Regression plots for each predicited variable
- Test RMSE displayed in MATLAB console

**Model details**
- Clustering: Fuzzy C-Means (via _genfis_)
- FIS type: Sugeno
- Training: ANFIS (hybrid optimization)
- Trian/test split: 80%/20% (randomized)
- Separated models are trained for each output (X, Y, F)


**Notes**
- Input structure:
  - 1D: PL, PR
  - 2D: PL, PR, TL, TR
- Output structure:
  - 1D: X, F
  - 2D: X, Y, F
- Results depend o the chosen number of clusters (please refer to the paper for better understanding the trade-off)
- Ensure dataset format matches the expected column structure

# **MATLAB–Python TCP**

