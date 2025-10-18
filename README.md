# GEOINT Change Detection Case Study – Solonytsivka, Ukraine (May–June 2022)

## Analyzing Sentinel-1 SAR and Sentinel-2 Optical Imagery for Surface Activity Patterns

This repository demonstrates a complete, reproducible GEOINT/OSINT workflow that detects and analyzes potential logistical ground activity using Sentinel-1 SAR and Sentinel-2 optical imagery.
It focuses on the Ukraine–Russia border region (Solonytsivka, near Kharkiv) between May 2022 and June 2022.

The project blends radar-based change detection, optical visual analysis, and automated reporting to create an open-source intelligence case study that mirrors professional GEOINT production standards.

[See the full walkthrough here](https://medium.com/@avfaulkner/geoint-change-detection-case-study-solonytsivka-ukraine-may-june-2022-walkthrough-1876bb44d933)


## Objective

- Detect physical surface changes from multi-temporal Sentinel-1 and Sentinel-2 imagery..
- Generate heatmaps, overlays, and annotated intelligence visuals.
- Automate the production of analyst-style Markdown and PDF reports.
- Provide a Leaflet-based web viewer for interactive exploration.
- Serve as an educational reference for GEOINT, IMINT, and OSINT investigations.

---

## Repository Structure and File Definitions

| Path | Description |
|------|--------------|
| **data/** | Main data directory containing raw satellite images, outputs, and supporting materials. |
| ├── **satellite_images/** | Source imagery (Sentinel-1 SAR and Sentinel-2 True/False Color) downloaded from EO Browser. |
| │ ├── `solonytsivka_may2022_truecolor.png` | Sentinel-2 optical imagery, True Color composite for May 2022. |
| │ ├── `solonytsivka_jun2022_truecolor.png` | Sentinel-2 optical imagery, True Color composite for June 2022. |
| │ ├── `solonytsivka_may2022_falsecolorurban.png` | Sentinel-2 False Color Urban composite for May 2022. |
| │ ├── `solonytsivka_jun2022_falsecolorurban.png` | Sentinel-2 False Color Urban composite for June 2022. |
| │ ├── `solonytsivka_may2022_sar.png` | Sentinel-1 SAR (VV polarization) image for May 2022. |
| │ └── `solonytsivka_jun2022_sar.png` | Sentinel-1 SAR (VV polarization) image for June 2022. |
| ├── **output/change_maps/** | Auto-generated outputs (change maps, overlays, heatmaps, and annotated products). |
| │ ├── `sar_diff_heatmap.png` | Radar backscatter intensity difference visualization. |
| │ ├── `sar_overlay_truecolor_annotated.png` | Blended SAR + optical (True Color) overlay with red annotations. |
| │ ├── `sar_overlay_falsecolor_annotated.png` | Blended SAR + optical (False Color Urban) overlay with annotations. |
| │ ├── `true_color_heatmap.png` | Heatmap showing detected changes in optical True Color imagery. |
| │ ├── `false_color_heatmap.png` | Heatmap showing changes in False Color Urban imagery. |
| │ └── `*_overlay.png` | Intermediate blended or pre-annotation overlay files. |
| ├── **image_notes/** | Analyst observation notes describing patterns, textures, or anomalies in imagery. |
| │ └── `kharkiv_notes.md` | Example notes documenting contextual analysis near Kharkiv. |
| └── **open_source_reports/** | Placeholder directory for corroborating OSINT or public intelligence documents. |
| **notebooks/** | Jupyter Notebooks implementing each stage of the analysis pipeline. |
| ├── `image_compare_overlays.ipynb` | Generates True vs False Color comparisons and multi-temporal optical overlays. |
| ├── `sar_analysis_change_detect.ipynb` | Computes SAR pixel differences, thresholds, and masks significant changes. |
| ├── `sar_overlay_blended.ipynb` | Blends SAR and optical data, annotates detected regions, and exports intel markdowns. |
| └── `generate_pdf_report.ipynb` | Converts generated Markdown intel summaries into professional PDF reports. |
| **reports/** | Contains analyst reports in both Markdown and PDF format. |
| ├── `true_color_intelligence_report.md` | Analyst findings for optical True Color analysis. |
| ├── `false_color_intelligence_report.md` | Findings for False Color Urban imagery analysis. |
| ├── `sar_intelligence_report.md` | Findings for SAR-based change detection. |
| ├── `sar_blended_intel_report.md` | Combined SAR + optical interpretation summary. |
| ├── `solonytsivka_geoint_report.pdf` | Comprehensive GEOINT case study compiled from all analysis stages. |
| └── `sar_intelligence_report.pdf` | Standalone SAR analysis report in PDF format. |
| **docs/** | GitHub Pages web viewer powered by Leaflet (interactive visualization). |
| ├── **assets/** | Optimized overlay and annotation images used in the web viewer. |
| │ ├── `sar_diff_heatmap.png` | Web copy of the SAR difference heatmap. |
| │ ├── `sar_overlay_truecolor_annotated.png` | Annotated overlay (True Color version) for map layer display. |
| │ └── `sar_overlay_falsecolor_annotated.png` | Annotated overlay (False Color version) for map layer display. |
| ├── `index.html` | Main HTML file initializing the Leaflet map and controls. |
| ├── `script.js` | Handles image overlay logic, opacity, and map interactivity. |
| └── `style.css` | Basic styling for the web viewer interface. |
| **requirements.txt** | Python dependencies required to reproduce all analysis steps. |
| **README.md** | Documentation describing the project’s objectives, workflow, and usage. |

---

## Workflow Overview

| Phase | Script / Notebook | Description | Key Outputs |
|-------|-------------------|--------------|--------------|
| **1. Data Acquisition** | — | Sentinel-1 SAR and Sentinel-2 optical images downloaded via [EO Browser](https://apps.sentinel-hub.com/eo-browser/) | `/data/satellite_images/` |
| **2. Optical Comparison** | `image_compare_overlays.ipynb` | Compares True Color and False Color Urban composites between months | `true_color_heatmap.png`, `false_color_overlay.png` |
| **3. SAR Change Detection** | `sar_analysis_change_detect.ipynb` | Detects radar backscatter differences (May→June) to reveal disturbed ground | `sar_diff_heatmap.png`, `sar_overlay.png` |
| **4. SAR + Optical Fusion** | `sar_overlay_blended.ipynb` | Blends radar change maps with optical context, adds annotations, generates Markdown reports | `sar_overlay_truecolor_annotated.png`, `sar_blended_intel_report.md` |
| **5. Report Generation** | `generate_pdf_report.ipynb`  | Builds the professional GEOINT PDF from imagery and Markdown reports | `solonytsivka_geoint_report.pdf` |
| **6. Web Visualization** | `/docs/index.html`, `/docs/script.js` | Displays all overlays interactively via Leaflet | GitHub Pages map viewer |

---

## Data and Methods

### Imagery Sources

- Sentinel-1 SAR (VV polarization, C-band radar)
- Sentinel-2 optical (True Color, False Color Urban composites)
- Geographic region: Solonytsivka (≈ 49.985° N, 36.168° E)

### Analytic Techniques

- Radar backscatter normalization and Gaussian smoothing  
- Pixel-wise absolute difference computation  
- Threshold-based binary mask and region labeling  
- Optical fusion via `cv2.addWeighted()` blending  
- Annotated overlays using PIL `ImageDraw`  
- Automated Markdown → PDF report generation via `ReportLab`  

---

## Installation

Clone the repository

```bash
git clone https://github.com/avfaulkner/arms-smuggling-geo-osint.git
cd arms-smuggling-geo-osint
```

Create and activate a virtual environment

```bash
python -m venv venv
source venv/bin/activate
```

Install dependencies with pinned versions

```bash
pip install -r requirements.txt
```

### Recommended Environment

| Component | Version | Notes |
|------------|----------|-------|
| Python | ≥ 3.9 | Compatible with NumPy, OpenCV, and ReportLab versions used in notebooks. |
| Jupyter Notebook | ≥ 7.0 | Required for interactive analysis and visualization scripts. |
| Operating System | WSL2 on Windows 10 / 11 or Ubuntu 20.04+ | Both tested successfully. |
| Memory | ≥ 8 GB RAM | Recommended for handling multiple 10-meter Sentinel imagery layers. |

*The Jupyter scripts in this project were run in **VSCode with the Jupyter extension** installed.*

---

## Reproducing the Analysis

This checklist ensures that any researcher, analyst, or reviewer can fully reproduce the GEOINT workflow and verify its outputs.

| Category | Requirement | Details / Notes |
|-----------|--------------|-----------------|
| **Area of Interest (AOI)** | Solonytsivka, Ukraine (approx. 49.985° N, 36.168° E) | Selected for its proximity to Kharkiv and logistical infrastructure. |
| **Date Range** | May 2022 → June 2022 | Chosen to capture activity changes during a known escalation period. |
| **Imagery Sources** | Sentinel-1 (SAR VV polarization) and Sentinel-2 (Optical True/False Color) | Acquired via [Copernicus EO Browser](https://apps.sentinel-hub.com/eo-browser/). |
| **Imagery Format** | PNG (preferred) | High-quality exports from EO Browser; GeoTIFF optional for advanced use. |
| **Directory Setup** | `data/satellite_images/`, `data/output/change_maps/`, `reports/`, `docs/` | Must match repository structure exactly for scripts to run without modification. |
| **Dependencies** | Python 3.9 +, NumPy, OpenCV, SciPy, Rasterio, Pillow, Matplotlib, ReportLab, pypandoc | Install via `pip install -r requirements.txt`. |
| **Workflow Order** | 1. `sar_analysis_change_detect.ipynb` → 2. `sar_overlay_blended.ipynb` → 3. `generate_pdf_report.ipynb` | Must be run sequentially; later notebooks rely on generated files from earlier ones. |
| **Expected Outputs** | Heatmaps, blended overlays, annotated SAR/optical images, intelligence markdowns, final PDF report | Output paths automatically created under `data/output/change_maps/` and `reports/`. |
| **Verification Step** | Visual alignment of annotated overlays and successful PDF generation | Run Leaflet viewer under `/docs/` to verify overlay accuracy. |
| **Version Control** | Commit after each major notebook run | Keeps output hashes consistent across machines. |
| **Optional Enhancements** | Enable tooltips in Leaflet, add GeoJSON annotations, or regenerate SAR difference with updated thresholds | For advanced analysis and interactivity. |

---

### Validation Procedure

1. Confirm that all required input files exist in `/data/satellite_images/`.  
2. Open `sar_analysis_change_detect.ipynb` and run all cells.  
3. Verify that `sar_diff_heatmap.png` appears in `/data/output/change_maps/`.  
4. Run `sar_overlay_blended.ipynb` and ensure annotated overlays (`_annotated.png`) are created.  
5. Open `/reports/` and confirm that Markdown intelligence summaries (`*_intel_report.md`) are generated.  
6. Run `generate_pdf_report.ipynb` to build the professional GEOINT PDF.  
7. Serve or open `/docs/index.html` locally or via GitHub Pages and toggle overlays to confirm spatial alignment.  

---

### Integrity Verification

To ensure your outputs match the baseline results, confirm the following:

- Generated overlay image dimensions match the originals (no compression or aspect distortion).  
- Bounding boxes in annotated images align precisely with visual change areas.  
- The final PDF report (`solonytsivka_geoint_report.pdf`) includes all sections and imagery without missing assets.  
- The Leaflet viewer displays overlays centered at `49.985 N, 36.168 E` with visible annotations.

---

## Deliverables

- Annotated satellite visuals
- Jupyter notebooks documenting geospatial analysis
- Final intelligence reports with findings and tradecraft explanation

---



## Disclaimer

This project reflects open-source GEOINT methodology adapted for public use.
It does not claim to represent operational intelligence conclusions; instead, it serves as an instructional model showing how radar and optical imagery can corroborate potential ground activity in conflict-adjacent regions.
