
# Documentation of Foot Distance Calculation Methods

This document provides detailed descriptions and mathematical equations for the four methods used to calculate foot distance using the DepthPro model and Mediapipe.

---

## Method 1: Pinhole Camera Model

This method calculates the 3D Euclidean distance between the left and right feet using the pinhole camera model. The pinhole camera model assumes that the intrinsic parameters (focal length and principal point) are known or can be estimated.

### **Mathematical Equations**

![Sample Image](images\1.png)

---

## Method 2: Avoiding Calibration

This method simplifies the calculation by avoiding explicit calibration of intrinsic parameters. It assumes the camera has a normalized field of view and uses the depth directly to scale the 2D coordinates.

### **Mathematical Equations**
![Sample Image](images\2.png)

---

## Method 3: Using Estimated Focal Length and Depth Map

This method uses an estimated focal length provided by the DepthPro model to calculate the 3D coordinates of the feet.

### **Mathematical Equations**
![Sample Image](images\3.png)

---

## Method 4: Focal Length from Shoulder Proportions

This method estimates the focal length based on the shoulder width in pixels and its real-world size, then uses this focal length to calculate the 3D coordinates of the feet.

### **Steps for Focal Length Estimation**
![Sample Image](images\4.png)

![Sample Image](images\5.png)


---

## Summary Table of Methods
![Sample Image](images\11.png)


Each method provides a different approach to calculating the foot distance, leveraging either explicit or implicit assumptions about the camera's intrinsic parameters.