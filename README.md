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
2. Load an example dataset:
   ```matlab
   data = readmatrix('example_dataset.xlsx');
3. Run the processing script
   ```matlab
   process_raw_data

  
# **Machine Learning**

The Learning folder contains MATLAB code for fuzzy clustering, used to train and analyze the dataset.
Example data includes:

- 1D sensor all data

- 2D 60×60 sensor

These datasets correspond to those used in the paper.

**MATLAB-Python TCP**

This folder includes MATLAB and Python code for establishing a TCP/IP connection between MATLAB and Python.
It is used to connect the trained ANFIS model in MATLAB with Python to interface and control the UR robot during the HRI demonstrations.

**FSI COMSOL Simulation** 

This section contains files and instructions related to the Fluid–Solid Interaction (FSI) simulation performed in COMSOL Multiphysics.
A detailed description and simulation data can be found at the following [link](https://github.com/mwberghuis/softsensor?tab=readme-ov-file)
