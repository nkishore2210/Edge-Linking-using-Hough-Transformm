# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## PROGRAM:
### NAME: KISHORE N
### REG NO. 212222240049

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('zenitsu.jpg')  # Replace with your image path

gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)

# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
```
```python
# Input Image 
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')
plt.show()
```
### OUTPUT:
![Screenshot 2024-10-03 161024](https://github.com/user-attachments/assets/d9cc9e35-476d-4ef5-982e-9252fb43a067)

```python
# Greyscale image
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
plt.show()
```
### OUTPUT:
![Screenshot 2024-10-03 161122](https://github.com/user-attachments/assets/a2add0dd-c8cc-46b6-9ca3-8760ce9022d1)

```python
# Canny Edge Detection Output
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
plt.show()
```
### OUTPUT:
![Screenshot 2024-10-03 161214](https://github.com/user-attachments/assets/c0a5bb0b-d72f-4f84-9e72-d1d69fcba2ad)

```python
# Hough Transform Result
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
plt.show()
```
### OUTPUT:
![Screenshot 2024-10-03 161253](https://github.com/user-attachments/assets/38998e9e-b3a8-4ec0-b77d-8dcb462c028d)

