# Crop Field Segmentation using Gaussian Mixture Model (GMM) and Connected Components

## Overview

This project implements an image segmentation algorithm for crop field images using Gaussian Mixture Models (GMM) and Connected Components labeling. The primary goal is to segment out non-crop areas from the field and save the results as separate images.

### Key Features:

- **GMM-Based Segmentation**: Uses Gaussian Mixture Models to classify pixels in the image into different clusters based on their color.
- **Connected Components Labeling**: Identifies and extracts contiguous regions of pixels belonging to the same cluster, allowing for the isolation of specific areas in the image.

### Project Structure

- **images/**: Directory containing the input images.
- **results/**: Directory where the segmented output images will be saved.
- **GMM.py**: Contains the implementation of the Gaussian Mixture Model.
- **Utils.py**: Contains utility functions such as image loading.
- **Maincode.ipynb**: The main script to run the segmentation algorithm.

### Example Results

Below are some example outputs:

- **Original Image**:
  <img src="images/DJI_20240308125440_0001_D.JPG" alt="Original Image" width="300"/>

- **Segmented Output**:
  <img src="results/component_0_1.png" alt="Segmented Component 1" width="300"/>
  <img src="results/component_0_3.png" alt="Segmented Component 2" width="300"/>
  
## Brief Explanation

### Gaussian Mixture Model (GMM)

GMM is a probabilistic model that assumes all the data points are generated from a mixture of several Gaussian distributions with unknown parameters. In the context of image segmentation:

- The algorithm starts by initializing the parameters using K-Means clustering.
- It then iteratively refines these parameters using the Expectation-Maximization (EM) algorithm until the model converges.
- Each pixel is assigned to the Gaussian component that has the highest posterior probability, effectively segmenting the image into `K` clusters.

### Connected Components Labeling

After GMM segmentation, the image is further processed to identify contiguous regions (components) that belong to the same cluster:

- **Binary Mask Creation**: A binary mask is created for each cluster, where pixels belonging to the cluster are marked as `1` and others as `0`.
- **Labeling**: The connected components algorithm labels each contiguous region of `1`s with a unique identifier.
- **Filtering and Saving**: Components with a significant number of pixels are saved as separate images, representing different regions of the field.

## Conclusion

This project is a powerful tool for segmenting crop fields in aerial images, allowing for the identification of non-crop areas. The combination of GMM and connected components labeling ensures accurate segmentation and easy extraction of relevant areas.
