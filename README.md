# SAR and Optical Image Preprocessing for Iceberg Detection

This repository contains a Jupyter Notebook and supporting files for preprocessing SAR (Sentinel-1) and optical (JPEG2000) satellite imagery for iceberg detection. The code prepares georeferenced cutouts of SAR and optical images, applies the iDPolRAD filter to SAR data, and generates PNG images for manual analysis or model training. A labelling package can be
used to create the labels/annotations.

# Repository Contents

- `notebook.ipynb` – Jupyter Notebook containing the full preprocessing workflow.
- `README.md` – This file.

# Workflow Summary

1. **Data Input**  
   The notebook reads SAR `.tiff` images (HH and HV polarization), optical `.jp2` images, and land mask data. It ensures that all files exist for each index before processing.

2. **Georeferencing & Cutouts**  
   Rasterio is used to align SAR and optical images in the same georeferenced coordinate system. Images are divided into smaller fixed-size slices for analysis.

3. **iDPolRAD Filter**  
   SAR HH and HV slices are combined using the iDPolRAD formula (Soldal et al., 2019) to enhance iceberg detection. Optional land masking is applied.

4. **Image Export**  
   PNG images of each SAR iDPolRAD slice and corresponding optical slice are created for visual inspection or manual labeling.

5. **Physical Coordinates**  
   The top-left x, y coordinates of each image slice are saved in a CSV file for reference.

6. **Cleanup & Organization**  
   Temporary files are removed, and all processed images are consolidated into dedicated folders for SAR and optical images.

# Requirements

- Python 3.x
- Libraries:
  - `numpy`
  - `matplotlib`
  - `rasterio`
  - `scipy`
  - `PIL` (Pillow)
  - `pandas`
  - `opencv-python`
  - `imageio`
  - `tkinter`

# Install dependencies using pip:

```bash
pip install numpy matplotlib rasterio scipy pillow pandas opencv-python imageio
```

# Usage

Open the notebook in Jupyter.

Adjust global variables such as number_of_images_to_examine_per_row and landmask_limit as needed.

Run the notebook cells in order to generate the image cutouts and CSV files.

# Citation

If you use this code or dataset for research, please cite:

The new paper 

and,

Soldal, I. H., Dierking, W., Korosov, A., & Marino, A. (2019). Automatic detection of small icebergs in fast ice using satellite wide-swath SAR images. Remote Sensing, 11(7), 806.

