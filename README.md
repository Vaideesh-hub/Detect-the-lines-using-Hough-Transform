#  Lane Detection

##  Aim

To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

---

## Learning Objective

* Understand each stage of image processing
* Learn how to build a complete computer vision pipeline
* Practice writing code in guided sections

**Important Instruction:**
👉 Write code **ONLY in places marked as `# Your Code Here`**
👉 Do NOT modify any other part of the code

---

##  Software Used

* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

---

##  Algorithm & Explanation

---

###  Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

---

###  Step 2: Read the Image

```python
# Read the image using OpenCV

###
# Your Code Here
###
```

---

###  Step 3: Convert to Grayscale

```python
# Convert to grayscale.

###
# Your Code Here
###
```

---

###  Step 4: Display Images

```python
plt.figure(figsize=(10,5))

###
# Your Code Here
###
```

---

###  Step 5: Thresholding

```python
# Apply thresholding

threshold = 
###
# Your Code Here
###
```

---

###  Step 6: Region of Interest (ROI)

```python
# ROI masking already provided
# (Do not modify)
```

---

### Step 7: Edge Detection (Canny)

```python
# Perform Edge Detection

###
# Your Code Here
###
```

---

###  Step 8: Gaussian Blur

```python
# Apply Gaussian Blur

###
# Your Code Here
###
```

---

###  Step 9: Hough Transform

```python
# Detect lines using Hough Transform

###
# Your Code Here
###
```

---

### Step 10: Lane Detection Logic

```python
# Already implemented
# (Do not modify)
```

---
##  Instructions

* Fill ONLY in `# Your Code Here` sections
* Do NOT change existing code
* Run step-by-step
* Verify outputs

---

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
```
# Read the image using OpenCV

image = cv2.imread('lan_img1.jpg.jpeg')
if image is None:
    raise FileNotFoundError("road.jpg was not found. Place road.jpg in the same folder as this notebook.")
```
```
# Convert to grayscale.

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

```
```
plt.figure(figsize=(10,5))

###
# Your Code Here
plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,2,2)
plt.imshow(gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")

plt.tight_layout()
plt.show()
###
```
## Output

<img width="773" height="252" alt="Screenshot 2026-11-22 114100" src="https://github.com/user-attachments/assets/2905013c-e9a3-452b-9708-12a21c98858d" />

## Program
```
# Apply thresholding

threshold = cv2.threshold(gray, 150, 255, cv2.THRESH_BINARY)

```
```
# ROI masking already provided
# (Do not modify)

height, width = threshold[1].shape

mask = np.zeros_like(threshold[1])

polygon = np.array([[
    (0, height),
    (width // 2 - 60, height // 2 + 60),
    (width // 2 + 60, height // 2 + 60),
    (width, height)
]], np.int32)

cv2.fillPoly(mask, polygon, 255)

roi = cv2.bitwise_and(threshold[1], mask)
```
```
# Perform Edge Detection

###
# Your Code Here
edges = cv2.Canny(roi, 50, 150)
###
```
```

# Apply Gaussian Blur

###
# Your Code Here
blurred = cv2.GaussianBlur(edges, (5,5), 0)
###
```
```
# Detect lines using Hough Transform

###
# Your Code Here
lines = cv2.HoughLinesP(
    blurred,
    rho=1,
    theta=np.pi/180,
    threshold=50,
    minLineLength=50,
    maxLineGap=100
)
###
```
```
# Already implemented
# (Do not modify)

line_image = np.zeros_like(image)

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line
        cv2.line(line_image, (x1, y1), (x2, y2), (0, 255, 0), 5)

final_output = cv2.addWeighted(image, 0.8, line_image, 1.0, 0)

plt.figure(figsize=(16,10))

plt.subplot(2,4,1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(2,4,2)
plt.imshow(gray, cmap='gray')
plt.title("Grayscale Image")
plt.axis("off")

plt.subplot(2,4,3)
plt.imshow(threshold[1], cmap='gray')
plt.title("Thresholded Image")
plt.axis("off")

plt.subplot(2,4,4)
plt.imshow(roi, cmap='gray')
plt.title("ROI Masked Image")
plt.axis("off")

plt.subplot(2,4,5)
plt.imshow(edges, cmap='gray')
plt.title("Edge Detected Image")
plt.axis("off")

plt.subplot(2,4,6)
plt.imshow(blurred, cmap='gray')
plt.title("Smoothed Image")
plt.axis("off")

plt.subplot(2,4,7)
plt.imshow(cv2.cvtColor(line_image, cv2.COLOR_BGR2RGB))
plt.title("Detected Lines")
plt.axis("off")

plt.subplot(2,4,8)
plt.imshow(cv2.cvtColor(final_output, cv2.COLOR_BGR2RGB))
plt.title("Final Lane Detection Output")
plt.axis("off")

plt.tight_layout()
plt.show()
```
## Output

<img width="860" height="331" alt="Screenshot 2026-11-22 114222" src="https://github.com/user-attachments/assets/dfa1c70f-69ca-415b-9f26-b796a4a948ae" />

## Result

Thus, the lane detection pipeline is successfully implemented by completing the missing code sections. The system detects and highlights lane lines effectively.

---

##  Developed By
Vaideeshwaran G


* **Name:** ____________________________
* **Register No:** ______________________
