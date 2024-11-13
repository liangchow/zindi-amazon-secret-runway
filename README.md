# GeoAI Amazon Basin Secret Runway Detection Challenge
## Team: TerraPulse

The [Amazon Basin Secret Runway Detection Challenge](https://zindi.africa/competitions/geoai-amazon-basin-secret-runway-detection-challenge) on Zindi aims to leverage satellite imagery and machine learning to detect illegal airstrips within the Amazon rainforest.

This project is Team TerraPulse contribution to the challege. We use a combination of data preprocessing, deep learning, and geospatial analysis techniques to accurately locate potential airstrips.

## Table of contents
1. [Coding Environment](#CodingEnvironment)
2. [Data Description](#DataDescription)
3. [Model Architecture](#ModelArchitecture)
4. [Usage Instructions](#UsageInstructions)
5. [Acknowledgments](#Acknowledgments)

## Coding Environment
This project was developed using the Google environment and GitHub. Google Colab for coding. Google Drive for storing training data, masks, and test AOI images. Google Earth Engine (GEE) was used to download all the Sentinel 1 and 2 data for training and inference. GitHub was used as repository and version control.

## Data Description
This project uses the following data sources:
- Sentinel-1 Satellite Imagery: Synthetic Aperture Radar (SAR) images. Data from the VV and VH bands are used for this project.
- Sentinel-2 Satellite Imagery: The S2 Multispectral Instrument (MSI) samples 13 spectral bands: visible, NIR, red edge and Short Wave Infra-Red (SWIR), and atmospheric bands. The visible, NIR and SWIR bands were used for this project, a total of 6 bands.
- Sample Illegal Runways: Geospatial shape files were provided by the Zindi team.
- Road Network: Open Street Map (OSM) geospatial data were used for this project to identify roads during the image cleaning process.

## Data Processing:
- Bands Selection: Sentinel 1 and 2 data were merged using GEE and a total of 9 bands are available for all images (training and inference).
- Cropping: Training images are 512px x 512px at 10m/px resolution. The inference images match the bounding boxes provided by the Zindi team.
- Normalization: The RGB channels are normalized to the ImageNet values. The other bands are normalized to the mean / std values of the entire training set. See utils/Calculate Channel Stats.ipynb for details.
- Augmentation: Standard data augmentation methods are used, including random cropping to 224px x 224px, rotation / flips, normalization, etc.

## Model Architecture
UNET with ResNet50 encoder and ImageNet pre-trained weights for RGB bands. The code supports additional bands beyond the RGB channels and the optimizer supports different learning rates for the additional bands.

## Usage Instructions
- Data Preparation:
    - Run [Data_Visualization/explore_sentinel_data.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/Data_Visualization/explore_sentinel_data.ipynb) to download satellite data for training and inference
    - Run [utils/GeoTIFF_modifications.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/utils/GeoTIFF_modifications.ipynb) to remove border columns with NaN values
    - Run [utils/Generate_airstrip_masks.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/utils/Generate_airstrip_masks.ipynb) to generate masks for training.

- Model Training:
    - Run [zindi_airstrip_training.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/zindi_airstrip_training.ipynb) to train the model.

- Inference:
    - Run [zindi_airstrip_prediction.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/zindi_airstrip_prediction.ipynb) to generate predictions on new satellite images. Results will be saved in Google Colab runtime. (time to run 4 minutes 31 seconds)

- Post-processing:
    - Use [image_cleaning.ipynb](https://github.com/liangchow/zindi-amazon-secret-runway/blob/main/image_cleaning.ipynb) to remove roads and add buffers to predicted runways (time to run 43 seconds)


## Acknowledgements
Special thanks to Zindi for organizing this challenge and providing the opportunity to work on a meaningful geospatial project. We also extend our gratitude to the Google Earth Engine for providing access to high-quality satellite imagery. 

### TerraPulse Team Members
- [Pascal Fortrin](https://github.com/Pascal-Fortin)
- [Shruti Mukhtyar](https://github.com/mukhtyar)
- [Dylan Manchester](https://github.com/dylan-manchester)
- [Liang Chow](https://github.com/liangchow)
