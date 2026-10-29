# EDGE DETECTION OPEN CV

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** PELLETI SINDHU SRI
- **Register No:** 212224240113 

---
## Program
```
# Step 1: Import all necessary modules
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Load an image using cv2.imread()
image_path = r"C:\Users\admin\little-cat-sitting-grass.jpg"
img_bgr = cv2.imread(image_path)

# Step 3: Convert the image to grayscale
gray_img = cv2.cvtColor(img_bgr, cv2.COLOR_BGR2GRAY)

# Step 4: Apply Sobel Operator ---
sobel_x = cv2.Sobel(gray_img, cv2.CV_64F, 1, 0, ksize=3)
sobel_y = cv2.Sobel(gray_img, cv2.CV_64F, 0, 1, ksize=3)
sobel_combined = cv2.magnitude(sobel_x, sobel_y)
sobel_edge = np.uint8(np.absolute(sobel_combined))

# Step 5: Apply Prewitt Operator (Custom Kernels) ---
kernel_prewitt_x = np.array([
    [-1, 0, 1],
    [-1, 0, 1],
    [-1, 0, 1]
], dtype=np.float32)

kernel_prewitt_y = np.array([
    [-1, -1, -1],
    [ 0,  0,  0],
    [ 1,  1,  1]
], dtype=np.float32)

prewitt_x = cv2.filter2D(gray_img, cv2.CV_64F, kernel_prewitt_x)
prewitt_y = cv2.filter2D(gray_img, cv2.CV_64F, kernel_prewitt_y)
prewitt_combined = cv2.magnitude(prewitt_x, prewitt_y)
prewitt_edge = np.uint8(np.absolute(prewitt_combined))

# Step 6: Apply Roberts Operator (Custom Kernels) ---
kernel_roberts_x = np.array([
    [1,  0],
    [0, -1]
], dtype=np.float32)

kernel_roberts_y = np.array([
    [ 0, 1],
    [-1, 0]
], dtype=np.float32)

roberts_x = cv2.filter2D(gray_img, cv2.CV_64F, kernel_roberts_x)
roberts_y = cv2.filter2D(gray_img, cv2.CV_64F, kernel_roberts_y)
roberts_combined = cv2.magnitude(roberts_x, roberts_y)
roberts_edge = np.uint8(np.absolute(roberts_combined))

# Step 7: Apply Laplacian Operator ---
laplacian = cv2.Laplacian(gray_img, cv2.CV_64F)
laplacian_edge = cv2.convertScaleAbs(laplacian)

# Step 8: Apply Canny Edge Detector ---
canny_edge = cv2.Canny(gray_img, threshold1=100, threshold2=200)

# Step 9: Display all edge-detected images for comparison ---
fig, axes = plt.subplots(2, 3, figsize=(15, 10))

# 1. Original Grayscale
axes[0, 0].imshow(gray_img, cmap='gray')
axes[0, 0].set_title("1. Original Grayscale")
axes[0, 0].axis('off')

# 2. Sobel Edge Detector
axes[0, 1].imshow(sobel_edge, cmap='gray')
axes[0, 1].set_title("2. Sobel Operator")
axes[0, 1].axis('off')

# 3. Prewitt Edge Detector
axes[0, 2].imshow(prewitt_edge, cmap='gray')
axes[0, 2].set_title("3. Prewitt Operator")
axes[0, 2].axis('off')

# 4. Roberts Edge Detector
axes[1, 0].imshow(roberts_edge, cmap='gray')
axes[1, 0].set_title("4. Roberts Operator")
axes[1, 0].axis('off')

# 5. Laplacian Edge Detector
axes[1, 1].imshow(laplacian_edge, cmap='gray')
axes[1, 1].set_title("5. Laplacian Operator")
axes[1, 1].axis('off')

# 6. Canny Edge Detector
axes[1, 2].imshow(canny_edge, cmap='gray')
axes[1, 2].set_title("6. Canny Detector")
axes[1, 2].axis('off')

plt.tight_layout()
plt.show()
```

## Output

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map  

###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges

<img width="1377" height="728" alt="image" src="https://github.com/user-attachments/assets/46896fc6-6175-4cf5-970f-3067dac4c49c" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
