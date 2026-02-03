# EX - 4 IMAGE-TRANSFORMATIONS


## Aim
To perform image transformation such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping using OpenCV and Python.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import necessary libraries such as OpenCV, NumPy, and Matplotlib for image processing and visualization.

### Step2:

Read the input image using cv2.imread() and store it in a variable for further processing.


### Step3:

Apply various transformations like translation, scaling, shearing, reflection, rotation, and cropping by defining corresponding functions:

1.Translation moves the image along the x or y-axis.
2.Scaling resizes the image by scaling factors.
3.Shearing distorts the image along one axis.
4.Reflection flips the image horizontally or vertically.
5.Rotation rotates the image by a given angle.

### Step4:
Display the transformed images using Matplotlib for visualization. Convert the BGR image to RGB format to ensure proper color representation.

### Step5:
Save or display the final transformed images for analysis and use plt.show() to display them inline in Jupyter or compatible environments.
## Software Required:
Anaconda - Python 3.7

### Program:
```
python
## EX-4 : IMAGE-TRANSFORMATIONS ##
## NAME : SHARAN G ##
## REG.NO: 212223230203 ##

import cv2
import numpy as np
# Load the image
image = cv2.imread('bird.jpg') # Replace with your image path
(h, w) = image.shape[:2]
# ----------------------- Translation -----------------------

# Move image 100 pixels right and 50 pixels down

tx, ty = 100, 50
translation_matrix = np.float32([[1, 0, tx], [0, 1, ty]])
translated = cv2.warpAffine(image, translation_matrix, (w, h))
# ----------------------- Scaling -----------------------

# Resize by 1.5x horizontally and 0.75x vertically

scaled = cv2.resize(image, None, fx=1.5, fy=0.75, interpolation=cv2.INTER_LINEAR)
# ----------------------- Shearing -----------------------

# Shear image horizontally

shear_matrix = np.float32([[1, 0.5, 0], [0, 1, 0]]) # x-shear
sheared = cv2.warpAffine(image, shear_matrix, (int(w + 0.5*h), h))
# ----------------------- Reflection (Flipping) -----------------------

# Flip horizontally (mirror image)

h_flip = cv2.flip(image, 1)

# Flip vertically

v_flip = cv2.flip(image, 0)
# ----------------------- Rotation -----------------------

# Rotate by 45 degrees around the center

angle = 45
scale = 1.0
center = (w // 2, h // 2)
rotation_matrix = cv2.getRotationMatrix2D(center, angle, scale)
rotated = cv2.warpAffine(image, rotation_matrix, (w, h))
# ----------------------- Cropping -----------------------

# Crop a region (top-left 200x200)

cropped = image[0:200, 0:200]
import matplotlib.pyplot as plt
# ----------------------- Display Results with Matplotlib -----------------------

titles = [
    "Original", "Translated", "Scaled", "Sheared",
    "Horizontally Flipped", "Vertically Flipped",
    "Rotated", "Cropped"
]
images = [
    image, translated, scaled, sheared,
    h_flip, v_flip, rotated, cropped
]
plt.figure(figsize=(12, 10))
for i in range(len(images)):
    plt.subplot(3, 3, i + 1)  # 3 rows, 3 columns
    plt.imshow(images[i])
    plt.title(titles[i], fontsize=10)
    plt.axis("off")

plt.tight_layout()
plt.show()

```
## Output:



<img width="1190" height="989" alt="download" src="https://github.com/user-attachments/assets/d9152316-c051-4b2c-9df4-e7ddd0226c27" />


## Result: 

Thus the different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping are done using OpenCV and python programming.
