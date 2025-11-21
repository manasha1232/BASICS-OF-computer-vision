# BASICS-OF-computer-vision
Day 1 of my 30-Day Computer Vision Challenge: Basics of image reading, drawing shapes, and edge detection using Python and OpenCV.
# 30-Day Computer Vision Challenge – Day 1: Basics

## Description
Welcome to **Day 1** of my 30-Day Computer Vision Challenge!  
Today, I explored the **fundamentals of computer vision** using Python and OpenCV. The goal was to understand **how to read images, draw shapes, and detect edges**.

**Key Learnings & Features:**
- Read and display images with OpenCV.
- Draw **lines, rectangles, and circles** on images.
- Perform **edge detection** using the Canny algorithm.
- Handle images of **any size safely**.
- Build a **template for future CV tasks**.

---

## Code Example

```python
import cv2
import numpy as np
import os

# --- IMAGE READING ---
image_path = os.path.join('.', 'whiteboard.png')
img = cv2.imread(image_path)

if img is None:
    print("Image not found!")
    exit()

# --- GET IMAGE SIZE ---
height, width = img.shape[:2]

# --- DRAWING SHAPES ---
cv2.line(img, (0, 0), (min(300, width-1), min(300, height-1)), (255, 0, 0), 3)
cv2.rectangle(img, (50, 50), (min(200, width-1), min(200, height-1)), (0, 255, 0), 2)
cv2.circle(img, (min(150, width-1), min(150, height-1)), 50, (0, 0, 255), 3)

# --- EDGE DETECTION ---
edges = cv2.Canny(img, 100, 200)
edges_dilated = cv2.dilate(edges, np.ones((3,3), dtype=np.uint8))

# --- SHOW IMAGES ---
cv2.imshow("Original Image with Shapes", img)
cv2.imshow("Edges", edges_dilated)

cv2.waitKey(0)
cv2.destroyAllWindows()

