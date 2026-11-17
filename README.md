# Histogram Equalization Using OpenCV (Grayscale & Color Images)

## AIM

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

1. Read and display a grayscale image.
2. Plot the histogram of the grayscale image.
3. Apply histogram equalization on the grayscale image.
4. Read and display a color image.
5. Plot histograms of B, G, R channels.
6. Convert the image to HSV color space.
7. Apply histogram equalization on the Value (V) channel.
8. Convert the enhanced image back to BGR format.
9. Display original and enhanced images with histograms.

## SOFTWARE REQUIRED

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ALGORITHM

**Step 1:** Import the required libraries: OpenCV, NumPy, and Matplotlib.

**Step 2:** Read the image `images.jpg` in grayscale format.

**Step 3:** Display the grayscale image and plot its histogram.

**Step 4:** Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

**Step 5:** Display the original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

**Step 6:** Read the same image in color format.

**Step 7:** Split the image into B, G, R channels and plot their histograms separately.

**Step 8:** Convert the image from BGR to HSV color space.

**Step 9:** Apply histogram equalization on the V (Value) channel.

**Step 10:** Merge the channels and convert the image back to BGR format.

**Step 11:** Display the original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

## PROGRAM DEVELOPED BY

**NAME:** VARUN A

**REG NO:** 212224240178

## PROGRAM

### 1. Import the required libraries and read the image in grayscale format.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

gray_img = cv2.imread('images.jpg', cv2.IMREAD_GRAYSCALE)
```

### 2. Display the grayscale image and plot its histogram.

```python
plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.imshow(gray_img, cmap='gray')
plt.title('Grayscale Image')

plt.subplot(1, 2, 2)
plt.hist(gray_img.ravel(), 256, [0, 256])
plt.title('Histogram')
plt.show()
```

### 3. Apply histogram equalization using cv2.equalizeHist().

```python
enhanced_gray_img = cv2.equalizeHist(gray_img)
```

### 4. Display original grayscale image, its histogram, enhanced image, and its histogram.

```python
plt.figure(figsize=(12, 10))

plt.subplot(2, 2, 1)
plt.imshow(gray_img, cmap='gray')
plt.title('Original Grayscale Image')

plt.subplot(2, 2, 2)
plt.hist(gray_img.ravel(), 256, [0, 256])
plt.title('Original Histogram')

plt.subplot(2, 2, 3)
plt.imshow(enhanced_gray_img, cmap='gray')
plt.title('Enhanced Grayscale Image')

plt.subplot(2, 2, 4)
plt.hist(enhanced_gray_img.ravel(), 256, [0, 256])
plt.title('Enhanced Histogram')

plt.tight_layout()
plt.show()
```

### 5. Read the same image in color format.

```python
color_img = cv2.imread('images.jpg')
```

### 6. Split the image into B, G, R channels and plot their histograms separately.

```python
b, g, r = cv2.split(color_img)

plt.figure(figsize=(15, 4))

plt.subplot(1, 3, 1)
plt.hist(b.ravel(), 256, [0, 256], color='blue')
plt.title('Blue Channel Histogram')

plt.subplot(1, 3, 2)
plt.hist(g.ravel(), 256, [0, 256], color='green')
plt.title('Green Channel Histogram')

plt.subplot(1, 3, 3)
plt.hist(r.ravel(), 256, [0, 256], color='red')
plt.title('Red Channel Histogram')

plt.tight_layout()
plt.show()
```

### 7. Convert the image from BGR to HSV color space.

```python
hsv_img = cv2.cvtColor(color_img, cv2.COLOR_BGR2HSV)
```

### 8. Apply histogram equalization on the V (Value) channel.

```python
h, s, v = cv2.split(hsv_img)

v_eq = cv2.equalizeHist(v)
```

### 9. Merge the channels and convert the image back to BGR format.

```python
hsv_eq = cv2.merge((h, s, v_eq))

color_eq_bgr = cv2.cvtColor(hsv_eq, cv2.COLOR_HSV2BGR)
```

### 10. Convert the original and enhanced images from BGR to RGB format.

```python
color_img_rgb = cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB)

color_eq_rgb = cv2.cvtColor(color_eq_bgr, cv2.COLOR_BGR2RGB)
```

### 11. Display original color image, histogram, enhanced image, and enhanced histogram.

```python
plt.figure(figsize=(12, 10))

plt.subplot(2, 2, 1)
plt.imshow(color_img_rgb)
plt.title('Original Color Image')

plt.subplot(2, 2, 2)
plt.hist(v.ravel(), 256, [0, 256], color='gray')
plt.title('Original V-Channel Histogram')

plt.subplot(2, 2, 3)
plt.imshow(color_eq_rgb)
plt.title('Enhanced Color Image')

plt.subplot(2, 2, 4)
plt.hist(v_eq.ravel(), 256, [0, 256], color='gray')
plt.title('Enhanced V-Channel Histogram')

plt.tight_layout()
plt.show()<img width="1472" height="387" alt="Screenshot 2026-11-17 085944" src="https://github.com/user-attachments/assets/b5e7d054-1413-471e-9609-fe967ed9724e" />

```

## OUTPUT

<img width="1572" height="447" alt="Screenshot 2026-11-17 085911" src="https://github.com/user-attachments/assets/e47af9e3-3eee-4752-b624-06f95d1753ee" />

<img width="1256" height="855" alt="Screenshot 2026-11-17 085933" src="https://github.com/user-attachments/assets/97a77f39-b679-452f-88d5-852c6777cc0d" />


<img width="1472" height="387" alt="image" src="https://github.com/user-attachments/assets/c1992587-9c80-4ba7-9e1e-14ea13eb9c14" />




<img width="1585" height="872" alt="image" src="https://github.com/user-attachments/assets/1ddfbe9f-0704-4e51-b7e9-305127a7a8e5" />



## RESULT

Thus, histogram equalization was successfully performed on both grayscale and color images using OpenCV. The contrast of the images was enhanced by applying histogram equalization to the grayscale image and the Value (V) channel of the HSV color image.
