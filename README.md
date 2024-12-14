<p align="center">
<b>Batangas State University</b>
  </p>
<p align="center">
<b>The National Engineering University</b>
</p>
<p align="center">
<b>College of Engineering - Department of Electronics Engineering</b>
  </p>
<p align="center">
<b>Bachelor of Science in Mechatronics Engineering</b>
</p>

<p align="center">
<b>MeXE402_4102_Finals_RenzoSamson_JanBenedictApostol</b>
  </p>
<p align="center">
<b>Final Requirement for the Course MeXEE 402: Electives II: Data Science and Machine Learning</b>
</p>
<br>
<br>
<p align="center">
<b>Submitted to: Engr. Mikko D. Torres</b>
</p>
<p align="center">
<b>Electives 2 Instructor</b>
</p>
<br>
<br>
<br>
<p align="center">
<b>December 2024</b>
</p>

## Table of Contents
  - [I. Introduction](#i-introduction)
  - [II. Abstract](#ii-abstract)
  - [III. Project Methods](#iii-project-methods)
  - [IV. Conclusion](#iv-conclusion)
  - [V. Additional Materials](#v-additional-materials)
  - [VI. References](#vi-references)
  - [VII. Pair](#vii-pair)
<hr>

# Reducing Noise in Photos


## I. Introduction

<p align="justify"> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Noise reduction is essential in digital image processing, as noise can severely degrade the quality of images. It arises from various sources like sensor limitations, transmission errors, or environmental factors, and often distorts important image details. In the context of computer vision, this problem is significant because noisy images can hinder tasks like object recognition, tracking, and analysis, leading to inaccurate results. This project leverages OpenCV, an open-source computer vision library, to address this issue by applying noise reduction techniques such as Gaussian blurring, median filtering, and bilateral filtering. By improving image quality and preserving key details, the project demonstrates OpenCV’s crucial role in enhancing visual clarity for computer vision applications.

## II. Abstract

<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The quality of digital images is often compromised by noise, which manifests as unwanted variations in pixel values. Traditional noise reduction methods typically apply a uniform filter across the entire image, which may result in the loss of important details. This project, titled "<b>Adaptive Noise Reduction: Smart Filtering for Enhanced Image Quality</b>," introduces a more refined approach to denoising, where the filtering process adapts to the varying characteristics of different image regions. Areas with significant noise receive stronger filtering to smooth out imperfections, while regions with fine textures and important details are preserved to maintain sharpness. Using OpenCV’s denoising code, this method effectively improves image clarity by reducing noise without compromising fine details, as demonstrated by a before-and-after comparison of the processed images. This approach represents a step forward in image processing, offering a smarter and more targeted solution for noise reduction in computer vision applications.

## III. Project Methods

1. Development Environment
   - **Use Visual Studio Code**: Set up Visual Studio Code as the primary IDE for the project.
   - **Create a Jupyter Notebook**: Structure and execute the code in a Jupyter Notebook file for better documentation and interactive analysis.
     
2. Library Import
   - Import the following libraries:
     - ***NumPy*** (`numpy`): For handling array-based image data.
     - ***OpenCV*** (`cv2`): For image processing and denoising functions.
     - ***OS*** (`os`): For file handling and image directory management.
     - ***Matplotlib*** (`matplotlib`): For visualizing and comparing the images.

3. Image Input
   - **Load Images**: Use OpenCV’s imread() function to load the images to be denoised.
   - **Preprocess Images**: Convert images to a suitable format (if needed) before applying filters.
     
4. Image Processing
   - **Masking the Background**
     - Create a mask to differentiate the background from the subject in the image.
     - Use OpenCV functions such as thresholding or color range segmentation to isolate specific regions.
   - **Denoising the Background**
     - Apply OpenCV’s fastNlMeansDenoising() or fastNlMeansDenoisingColored() function for noise reduction.
     - Adjust parameters like the filter strength, template window size, and search window size for optimal results.

5. Visualization
   - **Plot Comparisons**: Use `matplotlib` to create side-by-side visualizations of the original and denoised images.
     - Add titles and labels for clarity.
     - Save the plots as image files for documentation.
     
6. Optimization
   - **Fine-Tune Parameters**: Experiment with different filter strengths and window sizes to balance noise reduction and detail preservation.
     
7. Output
   - **Save Results**: Save the finished jupyter notebook for evaluation.
  
## IV. Conclusion
<p align="justify">
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; This project demonstrated how to navigate one of the techniques in machine learning, particularly in OpenCV, namely "Reducing Noise in Photos." This technique had three variations, namely <i>Median Filtering</i>, <i>Gaussian Filtering</i>, and <i>Non-local Means</i>, or simply <i>NLM</i>. These applications of techniques depend on what type of image will reduce its noise and the intensity of noise in the picture itself. 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Challenges encountered while doing this project is by balancing the noise removal (using the three techniques mentioned above) while preserving the quality of the subject at the same time. As excessive filter may ruin the subject's clarity.

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The project outcomes emphasize the importance of reducing noise of photos in achieving the expected outcome for intention of the user itself. In addition, reducing noise in photos is commonly used in medical field especially in laboratory tests for clarity results.


## V. Additional Materials
<p align="justify">
This section provides the complete code for the Adaptive Noise Reduction: Smart Filtering for Enhanced Image Quality. It includes the results and a side-by-side comparison of the original and denoised images to demonstrate the effectiveness of the approach.

### Whole Code for the Adaptive Noise Reduction: Smart Filtering for Enhanced Image Quality
```
# importing OpenCV, OS, NumPy, MatPlotLib
import cv2
import os
import numpy as np
from matplotlib import pyplot as plt

# Path to the folder containing images
input_folder = 'IMAGES'

# List all image files in the folder
image_files = [f for f in os.listdir(input_folder) if f.endswith(('.jpg', '.png', '.jpeg'))]

# HSV background threshold values
lower_bg = np.array([0, 0, 0])  # Lower HSV boundary
upper_bg = np.array([180, 255, 100])  # Upper HSV boundary

# For all images
for image_file in image_files:
    # Load the images
    image_path = os.path.join(input_folder, image_file)
    image = cv2.imread(image_path)
    
    # Convert to HSV for segmentation
    hsv_image = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)
    
    # Create a mask for the background
    background_mask = cv2.inRange(hsv_image, lower_bg, upper_bg)
    
    # Invert the mask for the foreground
    foreground_mask = cv2.bitwise_not(background_mask)
    
    # Apply denoising to the background
    background = cv2.fastNlMeansDenoisingColored(image, None, 11, 20, 7, 21)
    denoised_background = cv2.bitwise_and(background, background, mask=background_mask)
    
    # Keep the original foreground unchanged
    foreground = cv2.bitwise_and(image, image, mask=foreground_mask)
    
    # Combine the denoised background and the original foreground
    result = cv2.add(denoised_background, foreground)
    
    # Display the original, mask, and processed images side by side
    row, col = 1, 3
    fig, axs = plt.subplots(row, col, figsize=(20, 10))
    axs[0].imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
    axs[0].set_title(f'Original Image: {image_file}')
    axs[0].axis('off')

    axs[1].imshow(background_mask, cmap='gray')
    axs[1].set_title('Background Mask')
    axs[1].axis('off')

    axs[2].imshow(cv2.cvtColor(result, cv2.COLOR_BGR2RGB))
    axs[2].set_title('Denoised Background')
    axs[2].axis('off')

    plt.show()
```



### *Basic Reducing Noise in Photos*

**Recorded Video demonstrating the code running:**

https://drive.google.com/file/d/1brKrj_ODU2RDF8jSD2PjRyPK3yAUBUOD/view?usp=sharing

**Results:**

![image](https://github.com/user-attachments/assets/04d4c27d-dbf1-48f2-a63f-8d472fa5b0ec)



### *Adaptive Noise Reduction: Smart Filtering for Enhanced Image Quality*

**Recorded Video demonstrating the code running:**

https://drive.google.com/file/d/1cGeTKZKecBdatNseLUBuowzocDKN6qN5/view?usp=sharing

**Results:**

![image](https://github.com/user-attachments/assets/5b30169b-4154-4ebb-8ebe-7b49fda3da7e)

![image](https://github.com/user-attachments/assets/d7291f05-62ad-43ff-b608-f8ed1a4ce2e4)

![image](https://github.com/user-attachments/assets/65ddc22f-3107-44c4-8b09-61f1e19886c0)

![image](https://github.com/user-attachments/assets/7ecc19fa-0920-471f-89dc-026151338d6e)

![image](https://github.com/user-attachments/assets/26a6d57d-244e-4aea-8739-fe114ade9356)

![image](https://github.com/user-attachments/assets/fa274982-b98d-40f8-8064-e341fd9e017c)

## VI. References
- [Natural Image Noise Dataset](https://commons.wikimedia.org/wiki/Natural_Image_Noise_Dataset)
- [OpenCV Tutorial](https://www.youtube.com/watch?v=E3Lg4aZVCAU)

## VII. Pair
- Samson, Renzo M.
- Apostol, Jan Benedict D.

