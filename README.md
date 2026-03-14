# Digital Image Processing: Key Features and Filters

This document provides summary notes on essential Digital Image Processing (DIP) concepts, specifically focusing on common noise types and filtering techniques used for restoration and enhancement.

---

## 1. Salt and Pepper Noise
**Salt and Pepper Noise**, also known as impulse noise, is a form of noise typically seen on images where certain pixels are very dark and others are very bright.

*   **Appearance**: Randomly scattered black (pepper) and white (salt) pixels.
*   **Causes**:
    *   Transmission errors during data transfer.
    *   Faulty sensor elements in cameras.
    *   Corruption in storage media.
*   **Characteristics**:
    *   Noisy pixels take on extreme values (e.g., 0 or 255 in 8-bit images).
    *   It is considered a high-frequency noise.
    *   Significantly degrades the visual detail of an image.

---

## 2. Gaussian Filter
A **Gaussian Filter** is a linear smoothing filter that uses a Gaussian distribution for determining the weights of a pixel's neighborhood.

*   **Mechanism**: Operates by performing a weighted average of surrounding pixels. Weights decrease with distance from the center pixel according to a bell-shaped Gaussian curve.
*   **Key Parameters**: 
    *   **Kernel Size**: The dimensions of the local window.
    *   **Sigma ($\sigma$)**: The standard deviation, which controls the extent of blurring.
*   **Characteristics**:
    *   Effective at reducing Gaussian (additive white) noise.
    *   Produces a smooth, blurred effect.
    *   Isotropic: Smooths equally in all directions.
    *   *Drawback*: Can significanly blur edges and fine details.

---

## 3. Median Filter
The **Median Filter** is a non-linear digital filtering technique frequently used to remove noise while preserving edges.

*   **Mechanism**: 
    1.  Select a local window (e.g., $3 \times 3$ kernel).
    2.  Sort all pixel values within the window in numerical order.
    3.  Replace the center pixel value with the **median** (the middle value) from the sorted list.
*   **Characteristics**:
    *   **Superior for Salt and Pepper Noise**: Since salt/pepper values are outliers (extreme 0 or 255), they are forced to the ends of the sorted list and almost never selected as the median.
    *   **Edge Preservation**: Better at maintaining sharp edges than linear filters (like Mean or Gaussian) because it doesn't create new "average" values that don't exist in the original neighborhood.

---

## 4. Adaptive Local Filter
**Adaptive Filters** adjust their behavior based on the statistical properties of the local neighborhood of a pixel.

*   **Mechanism**: Unlike standard filters that apply the same operation everywhere, an adaptive filter calculates local statistics (mean, variance) and modifies its response:
    *   **High Variance (Edges)**: The filter reduces its smoothing to preserve detail.
    *   **Low Variance (Smooth areas)**: The filter increases smoothing to effectively reduce noise.
*   **Characteristics**:
    *   Preserves image sharpness and fine details better than non-adaptive filters.
    *   Highly effective when noise distribution is not uniform across the image.
    *   **Adaptive Median Filter**: A variant that dynamically changes window size to handle high-density impulse noise without losing detail.

---

## Summary Comparison

| Filter Type | Category | Best For | Edge Preservation |
| :--- | :--- | :--- | :--- |
| **Gaussian** | Linear | Gaussian / Uniform Noise | Low (Blurs edges) |
| **Median** | Non-linear | Salt and Pepper Noise | High |
| **Adaptive Local** | Adaptive | Variable Noise / Fine Details | Very High |
