# GeoAI Amazon Basin Secret Runway Detection Challenge
## Team: TerraPulse

The [Amazon Basin Secret Runway Detection Challenge](https://zindi.africa/competitions/geoai-amazon-basin-secret-runway-detection-challenge) on Zindi aims to leverage satellite imagery and machine learning to detect illegal airstrips within the Amazon rainforest.

This project is Team TerraPulse contribution to the challege. We use a combination of data preprocessing, deep learning, and geospatial analysis techniques to accurately locate potential airstrips.

## Table of contents
1. [Coding Environment](#CodingEnvironment)
2. [Data Description](#DataDescription)
3. [Model Architecture](#ModelArchitecture)
4. [Environment Setup](#EnvironmentSetup)
5. [Usage Instructions](#UsageInstructions)
6. [Acknowledgments](#Acknowledgments)

## Data Description
This project uses the following data sources:
- Sentinel-1 Satellite Imagery:
- Sentinel-2 Satellite Imagery:
- Sample Illegal Runways:
- Road Network: 

## Data Processing:
- Band Selection:
- Cropping:
- Normalization:
- Augmentation:

## Model Architecture
UNET with special encoder

## Environment Setup
This project is configured to run on Google Colab. Satellite imagery used for training and inference is stored on Google Drive.

## Usage Instructions
- Data Preparation:
    - Run ??.ipynb to download satellite data for training and inference
    - Run .pynpb to remove border columns with NaN values
    - Generate masks

- Model Training:
    - Run the notebook [zindi_airstrip_training.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/zindi_airstrip_training.ipynb) to train the model.

- Inference:
    - Run [zindi_airstrip_prediction.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/zindi_airstrip_prediction.ipynb) to generate predictions on new satellite images. Results will be saved in Google Colab runtime.

- Post-processing:
    - Use [image_cleaning.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/image_cleaning.ipynb) to remove roads and add buffers to predicted runways
    - Use [image_pred_stats.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/image_pred_stats.ipynb) to create prediction csv


## Acknowledgements
Special thanks to Zindi for organizing this challenge and providing the opportunity to work on a meaningful geospatial project. We also extend our gratitude to the Google Earth Engine for providing access to high-quality satellite imagery. 

### TerraPulse Team Members
- [Pascal Fortrin](https://github.com/Pascal-Fortin)
- [Shruti Mukhtyar](https://github.com/mukhtyar)
- [Dylan Manchester](https://github.com/dylan-manchester)
- [Liang Chow](https://github.com/liangchow)
