# Adaptive-Preprocessing-Pipeline-for-IOPA-X-ray-DICOM-Images
## Introduction
Digital dental radiographs, and in particular IOPA X-rays, are crucial tools for detecting lesions, infections, and anatomical variations in bony structures. However, raw DICOM images frequently include artifacts, for example noise, low contrast, and inconsistent sharpness often due to inconsistent acquisition protocols, ultimately leading to variability in the original images that include the artifacts. This project tackled these problems by developing an adaptive preprocessing pipeline that automatically evaluates image quality parameters and intelligently improves these parameters. The preprocessing pipeline ensures that all input images have standardization and optimized input for further analysis with AI models, resulting in more accurate and reliable outputs.

## Problem Statement
- **Inconsistency in Image Quality**: DICOM IOPA images vary in contrast, brightness, and sharpness.
- **Noise Artifacts**: Many images include salt-and-pepper or Gaussian noise, affecting diagnostic value.
- **AI Readiness**: Variability in input quality hinders the performance of automated diagnostic systems.
