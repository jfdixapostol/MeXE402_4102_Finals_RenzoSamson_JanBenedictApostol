# Batangas State University

The National Engineering University

College of Engineering - Department of Electronics Engineering
  
BS Mechatronics Engineering

MeXE402_4102_Finals_RenzoSamson_JanBenedictApostol

Final Requirement for the Course MeXE 402 - Mechatronics Engineering Elective 2: Data Science and Machine Learning

## Table of Contents
  - [I. Introduction](#i-introduction)
  - [II. Abstract](#ii-abstract)
  - [III. Project Methods](#iii-project-methods)
  - [IV. Conclusion](#iv-conclusion)
  - [V. Additional Materials](#v-additional-materials)
<hr> 
<br>

## I. Introduction

<p align="justify"> 
Noise reduction is essential in digital image processing, as noise can severely degrade the quality of images. It arises from various sources like sensor limitations, transmission errors, or environmental factors, and often distorts important image details. In the context of computer vision, this problem is significant because noisy images can hinder tasks like object recognition, tracking, and analysis, leading to inaccurate results. This project leverages OpenCV, an open-source computer vision library, to address this issue by applying noise reduction techniques such as Gaussian blurring, median filtering, and bilateral filtering. By improving image quality and preserving key details, the project demonstrates OpenCV’s crucial role in enhancing visual clarity for computer vision applications.


## II. Abstract

<p align="justify">
The quality of digital images is often compromised by noise, which manifests as unwanted variations in pixel values. Traditional noise reduction methods typically apply a uniform filter across the entire image, which may result in the loss of important details. This project, titled "Adaptive Noise Reduction: Smart Filtering for Enhanced Image Quality," introduces a more refined approach to denoising, where the filtering process adapts to the varying characteristics of different image regions. Areas with significant noise receive stronger filtering to smooth out imperfections, while regions with fine textures and important details are preserved to maintain sharpness. Using OpenCV’s denoising code, this method effectively improves image clarity by reducing noise without compromising fine details, as demonstrated by a before-and-after comparison of the processed images. This approach represents a step forward in image processing, offering a smarter and more targeted solution for noise reduction in computer vision applications.

## III. Project Methods

- Import necessary libraries: numpy, cv2, os, and matplotlib.
- Load the images to be denoised using OpenCV’s imread() function.
- Apply a mask to separate the background from the subject of the image.
- Perform background denoising using OpenCV’s fastNlMeansDenoising() or other denoising functions.
- Use matplotlib to plot side-by-side comparisons of the original and denoised images for visual analysis.
- Fine-tune filtering parameters to balance noise reduction and detail preservation.
- Save the processed images for further evaluation or use.
  
## IV. Conclusion

## V. Additional Materials
