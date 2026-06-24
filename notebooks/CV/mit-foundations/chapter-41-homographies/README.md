# Chapter 41 Homographies

This notebook is an educational homography demo for Chapter 41. It covers a PyTorch implementation of DLT/RANSAC/inverse warping on synthetic data, including homography estimation, noisy correspondences, RANSAC validation, parameter sweeps, failure cases, and a synthetic perspective-correction example with a checkerboard.

It also explains the core counting argument behind DLT: a homography is written as a 3x3 matrix but is defined only up to scale, so it has 8 degrees of freedom rather than 9. Each point correspondence contributes two constraints, which is why four non-collinear point pairs are the minimum needed for homography estimation with DLT, while larger correspondence sets give an overdetermined least-squares problem.

Run it on CPU from the project root with a Python environment that has `torch` and `matplotlib`, then open:

```bash
jupyter notebook notebooks/CV/mit-foundations/chapter-41-homographies/index.ipynb
```

The notebook includes figures for the original and transformed point grids, noisy correspondences, RANSAC inlier classification, parameter-sweep plots, failure-case visualizations, and an original / perspective-distorted / rectified checkerboard comparison. The parameter sweeps are meant to show that increasing noise gradually raises reprojection error, while increasing outlier ratio makes plain DLT fragile and eventually makes robust sampling harder for RANSAC.

Reported validation metrics include scale-normalized homography matrix error against ground truth, mean reprojection error over correspondences, RANSAC precision and recall for inlier detection, RANSAC success rate under an outlier sweep, and rectification mean absolute error over valid rectified pixels for the synthetic perspective-correction example.

Limitations: this is a synthetic perspective-correction example with perfect planar geometry, fixed random seeds, noise-free checkerboard corner correspondences, no lens distortion, and no occlusions. The notebook also demonstrates that nearly collinear correspondences are a failure case because they do not constrain the full 2D projective warp. The implementation stays intentionally educational and does not add a full degeneracy-filtering system for DLT or RANSAC samples, even though production implementations often do. The rectification MAE is mainly driven by interpolation and repeated resampling, so it should not be read as exact pixel recovery. The notebook should be read as a concise PyTorch implementation of DLT/RANSAC/inverse warping, not as a production-level panorama or full image stitching system.
