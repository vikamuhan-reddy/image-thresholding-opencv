# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding,
and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

-   Global Thresholding
-   Adaptive Thresholding
-   Otsu's Thresholding

## Learning Objectives

-   Understand image segmentation using thresholding techniques.
-   Learn how fixed and adaptive threshold values are applied.
-   Compare Global, Adaptive Mean, Adaptive Gaussian, and Otsu's
    thresholding.

## Software Used

-   Anaconda -- Python 3.7
-   Jupyter Notebook / VS Code
-   OpenCV (`cv2`)
-   NumPy
-   Matplotlib

## Algorithm and Explanation

### Step 1: Import Libraries

``` python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Step 2: Read Image

``` python
image = cv2.imread("C:/Users/vikam/Downloads/exp8_img.png")
```

### Step 3: Convert to Grayscale

``` python
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
```

### Step 4: Global Thresholding

``` python
_, global_thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)
```

### Step 5: Adaptive Thresholding

``` python
mean_thresh = cv2.adaptiveThreshold(
    gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C,
    cv2.THRESH_BINARY, 11, 2
)

gaussian_thresh = cv2.adaptiveThreshold(
    gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
    cv2.THRESH_BINARY, 11, 2
)
```

### Step 6: Otsu's Thresholding

``` python
otsu_value, otsu_thresh = cv2.threshold(
    gray, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU
)
```

### Step 7: Display and Compare Results

``` python
images = [gray, global_thresh, mean_thresh, gaussian_thresh, otsu_thresh]

titles = [
    "Original Grayscale",
    "Global Thresholding",
    "Adaptive Mean",
    "Adaptive Gaussian",
    "Otsu's Thresholding"
]

plt.figure(figsize=(12, 8))

for i in range(5):
    plt.subplot(2, 3, i+1)
    plt.imshow(images[i], cmap='gray')
    plt.title(titles[i])
    plt.axis('off')

plt.tight_layout()
plt.show()

print("Otsu Threshold Value:", otsu_value)
print("Image Segmentation Completed Successfully!")
```

## Expected Output
<img width="1103" height="638" alt="image" src="https://github.com/user-attachments/assets/5dbe0b0f-5c11-41d6-aafb-7e351a200cec" />


### Comparison of Results

-   Displays the grayscale image alongside all four thresholding
    results.
-   Helps compare the segmentation produced by each technique.

## Result

Thus, image segmentation is successfully performed using **Global
Thresholding, Adaptive Thresholding, and Otsu's Thresholding**
techniques in OpenCV.


