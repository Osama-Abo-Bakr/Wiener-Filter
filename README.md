

# Wiener Filter

## Explanation
The Wiener filter is a linear filter used to reduce noise and blur in images. It aims to produce an estimate of the original image by minimizing the mean square error between the estimated and true images.

## How It Works
1. **Wiener Filter Equation**:
   $$
   H(u, v) = \frac{H^*(u, v) |F(u, v)|^2}{|H(u, v)|^2 |F(u, v)|^2 + K}
   $$
   where:
   - \( H(u, v) \) is the degradation function.
   - \( H*(u, v) \) is the complex conjugate of \( H(u, v) \).
   - \( F(u, v) \) is the Fourier transform of the degraded image.
   - \( ( K \) is a constant representing the noise-to-signal power ratio.

## Pros and Cons
- **Pros**:
  - Effective at reducing noise and blur.
  - Minimizes mean square error.
- **Cons**:
  - Requires knowledge of the noise characteristics.
  - Computationally intensive.

## When to Use
- Use when you need to reduce noise and blur in images, especially when the noise characteristics are known.

## Sample Code Implementation

Here's a simple implementation in Python using OpenCV:

```python
import cv2
import numpy as np
from scipy.signal import wiener
from matplotlib import pyplot as plt

# Load the image
img = cv2.imread('image.jpg', 0)

# Apply Wiener filter
denoised_img = wiener(img, (5, 5))

# Display the results
plt.subplot(121), plt.imshow(img, cmap='gray'), plt.title('Original Image')
plt.subplot(122), plt.imshow(denoised_img, cmap='gray'), plt.title('Wiener Filtered Image')
plt.show()
