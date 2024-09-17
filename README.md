# Amazon ML Challenge Solution

## Overview

This repository contains the solution for the Amazon ML Challenge. The goal of the challenge was to extract entity values and their corresponding units from images and create a submission file in the required format. 

## Approach

### 1. Data Preprocessing

- **Image Downloading:** Downloaded the images associated with the image links in the `train.csv` file using the `download_images` function from the `src/utils.py` script. 
- **Data Organization:** 
    - Created dictionaries to map image links to their entity values and units from the `train.csv` file. 
    - Used Optical Character Recognition (OCR) to extract entity values and units from the images and stored these in separate dictionaries.
    - Consolidated information from the `train.csv`, `test.csv`, and `sample_test_out.csv` files into dictionaries for easy access during model development and evaluation.

### 2. Model Development

- **Initial Attempts:**  
    - Explored using the EfficientDet TFlite model with 500 hand-labeled images, but this approach did not yield satisfactory results.
- **Final Solution:** 
    - Adopted the YOLOv8 object detection model.
    - Trained the model for 50 epochs using 1500 images with a uniform class distribution. 
    - Utilized Tesseract OCR for text extraction from the detected regions.
    - Employed regular expressions (Regex) and the Pint library to clean and standardize the extracted entity values and units. 
    - Achieved an F1 score of 0.209 on a benchmark dataset of 1000 images.

## Libraries Used

* `os`
* `re`
* `pandas`
* `requests`
* `PIL` (Pillow)
* `io`
* `pint`
* `pytesseract`
* `ultralytics`
* `json`

## File Structure

* `solution/`
    * `Utils.ipynb`: Contains helper functions for downloading images and other preprocessing tasks
    * `Predictor.ipynb`: Contains the final model for entity value extraction
    * `ModelTrainer.ipynb`: Contains the model training code

## Conclusion

This solution provides a baseline approach for tackling the Amazon ML Challenge. By leveraging object detection, OCR, and text processing techniques, we were able to extract entity values and units from images with reasonable accuracy. There's significant room for improvement by exploring the suggested enhancements and further refining the model and preprocessing pipeline.

*Disclaimer:* The F1 score of 0.209 mentioned is based on a benchmark dataset and may not reflect performance on the actual test set.