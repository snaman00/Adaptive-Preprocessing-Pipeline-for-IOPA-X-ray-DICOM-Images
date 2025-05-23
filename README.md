# Adaptive-Preprocessing-Pipeline-for-IOPA-X-ray-DICOM-Images
## Introduction
Digital dental radiographs, and in particular IOPA X-rays, are crucial tools for detecting lesions, infections, and anatomical variations in bony structures. However, raw DICOM images frequently include artifacts, for example noise, low contrast, and inconsistent sharpness often due to inconsistent acquisition protocols, ultimately leading to variability in the original images that include the artifacts. This project tackled these problems by developing an adaptive preprocessing pipeline that automatically evaluates image quality parameters and intelligently improves these parameters. The preprocessing pipeline ensures that all input images have standardization and optimized input for further analysis with AI models, resulting in more accurate and reliable outputs.

## Problem Statement
- **Inconsistency in Image Quality**: DICOM IOPA images vary in contrast, brightness, and sharpness.
- **Noise Artifacts**: Many images include salt-and-pepper or Gaussian noise, affecting diagnostic value.
- **AI Readiness**: Variability in input quality affects the performance of automated diagnostic systems.

## Dataset Description

- **Format**: `.dcm` (DICOM) files simulating real-world clinical IOPA X-ray images.
- **Variability**:
  - Some images are too dark or overly bright.
  - Others suffer from motion blur or lack sharpness.
  - Some image's contains noise.
- **Metadata Included**: 
  - Patient Name, Modality, SOP Class UID
  - Pixel Spacing, Photometric Interpretation

These images are used to simulate a realistic diagnostic pipeline in dental radiography.


## Methodology

### 1. DICOM Image Handling
- Extracts pixel arrays and metadata from DICOM files using `pydicom`.
- Displays patient-specific information for reference and analysis.

### 2. Quality Assessment
- **Brightness**: Mean intensity of the image.
- **Contrast**: Standard deviation of pixel intensities.
- **Sharpness**: Measured using Laplacian variance.
- **Noise Level**: Estimated using edge detection techniques.

### 3. Image Enhancement Techniques
#### a. Static Processing
- Applies fixed contrast stretching, sharpening, and Gaussian denoising.

#### b. Adaptive Processing
- Dynamically adjusts:
  - Brightness and contrast using histogram analysis.
  - Sharpness using Laplacian feedback loops.
  - Noise reduction based on estimated noise levels.

### 4. Quality Evaluation Metrics
- **PSNR (Peak Signal-to-Noise Ratio)**: Measures image fidelity.
- **SSIM (Structural Similarity Index)**: Measures similarity with the original image.
- **Sharpness Score**: Laplacian-based evaluation.
- **Edge Clarity**: Canny edge detection output.

### 5. Grading System
- Normalizes and weights all metrics to assign a **grade (A to D)** reflecting the final image quality.


## Results & Evaluation

### Visual Comparisons
- **Side-by-side plots** of original, static processed, and adaptively enhanced images clearly show improvement.
- Adaptive enhancement preserves anatomical features while reducing noise effectively.

### Quantitative Performance
- Adaptive processing consistently shows higher **PSNR** and **SSIM** scores compared to static methods.
- **Sharpness** and **edge clarity** significantly improved.
- Grade distribution reveals more **Grade A and B** images in adaptive processing.

| Metric       | Original | Static  | Adaptive |
|--------------|----------|---------|----------|
| PSNR (avg)   | 22.5     | 25.1    | 29.3     |
| SSIM (avg)   | 0.72     | 0.79    | 0.87     |
| Sharpness    | Low      | Medium  | High     |
| Final Grade  | C        | B       | A        |


## Discussion & Future Work

### Key Achievements
- Successfully implemented a robust, adaptive preprocessing pipeline.
- Enhanced image quality across multiple dimensions, making them more AI-ready.
- Developed a reproducible and explainable grading system.

### Limitations
- Processing speed can be further optimized for real-time applications.
- Grading system thresholds may require fine-tuning for other imaging modalities.

### Future Directions
- Integrate lightweight deep learning models for real-time image enhancement.
- Extend pipeline for other dental X-ray formats like OPG or CBCT.
- Train AI models using the enhanced images for disease detection and classification.

## Instructions

### Prerequisites
Install the following libraries:

```bash
pip install pydicom numpy matplotlib opencv-python scikit-image pandas
```

### How to Run

1. Clone the repository:
```bash
git clone https://github.com/yourusername/AdaptiveIOPA.git
cd AdaptiveIOPA
```

2. Place your DICOM images in the `input_images/` folder.

3. Run the Colab notebook:
```bash
colab notebook DobbleAI.ipynb
```

4. Follow each section:
   - Load and visualize images
   - Analyze image quality
   - Apply static and adaptive enhancement
   - Compare results visually and quantitatively
