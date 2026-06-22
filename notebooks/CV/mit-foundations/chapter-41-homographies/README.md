# Chapter 41 Homographies

This notebook is an educational homography demo for Chapter 41. It covers a PyTorch implementation of DLT/RANSAC/inverse warping on synthetic data, including homography estimation, noisy correspondences, RANSAC validation, parameter sweeps, failure cases, and a synthetic perspective-correction example with a checkerboard.

Run it on CPU from the project root with a Python environment that has `torch` and `matplotlib`, then open:

```bash
jupyter notebook notebooks/CV/mit-foundations/chapter-41-homographies/index.ipynb
```

The notebook includes figures for the original and transformed point grids, noisy correspondences, RANSAC inlier classification, parameter-sweep plots, failure-case visualizations, and an original / perspective-distorted / rectified checkerboard comparison.

Reported validation metrics include scale-normalized homography matrix error against ground truth, mean reprojection error over correspondences, RANSAC precision and recall for inlier detection, RANSAC success rate under an outlier sweep, and rectification mean absolute error over valid rectified pixels for the synthetic perspective-correction example.

Limitations: this is a synthetic perspective-correction example with perfect planar geometry, fixed random seeds, noise-free checkerboard corner correspondences, no lens distortion, and no occlusions. The rectification MAE is mainly driven by interpolation and repeated resampling, so it should not be read as exact pixel recovery. The notebook should be read as a concise PyTorch implementation of DLT/RANSAC/inverse warping, not as a production-level panorama or full image stitching system.
