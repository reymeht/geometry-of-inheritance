# The Geometry of Inheritance
### Reyansh Mehta

I wanted to interpret human genetic variation through the contours and colors I work with as an artist. Using public genotype records from the 1000 Genomes Project, I developed a NumPy autoencoder and mathematical rules for generating three-dimensional surfaces. I experimented with their geometry and color, and additionally selected three forms to prepare in Blender and fabricate through 3D printing.

This notebook brings together the model, rendering code, and experiments presented in my MIT maker portfolio.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/reymeht/geometry-of-inheritance/blob/main/RM_Geometry_of_Inheritance_Final.ipynb)

[View the notebook](RM_Geometry_of_Inheritance_Final.ipynb) and [Watch or download the 40-second video](construction_40s.mp4)

## To Run the Code in Browser

1. Click **Open in Colab** above.
2. Sign in to Google if prompted.
3. Select **Run all**.

A CPU runtime is sufficient. The genotype data is all included in the notebook.

To generate the figures without rendering the videos, change `render_videos = True` to `render_videos = False` in the settings cell before running. Video rendering takes a bit longer than running the other cells.

You can also change `sample_index` to any number between 0 and 2503 to generate a surface from another record. The random-genotype experiment also constructs an input of 768 randomly sampled dosages and passes it through the fitted model.

## Method

Each input contains alternate-allele dosages at 768 selected sites on chromosome 22. After preprocessing, a denoising autoencoder compresses these values into twelve latent coordinates. The network has dimensions 768 → 72 → 12 → 72 → 768. Training uses NumPy implementations of backpropagation and Adam, starting from randomly initialized weights. The twelve coordinates control layered radial waves and additional surface deformations. A discrete cosine transform of the same vector supplies coefficients for three color anchors and spatial blending fields. Geometry and color depend on the genotype-derived values.

## Experiments

The notebook includes:

- PCA and autoencoder reconstruction comparisons
- Raw and bounded wave amplitudes
- Alternative wave profiles and pleat strengths
- Latent-coordinate sensitivity and single-site genotype edits
- Random-genotype comparisons
- Discrete frequency thresholds
- Palette calculations and harmonic color blending
- Mesh resolution, seam correction, and boundary closure
- Construction animations and OBJ/STL exports

The animation follows one surface through construction and color assignment, then expands to a 10 × 10 grid of different genotype samples.

## Run locally

Download the repository and extract it. From that folder, run:

    python -m pip install -r requirements.txt
    python -m jupyterlab

Open `RM_Geometry_of_Inheritance_Final.ipynb` in JupyterLab and run the cells in order.

Rendering MP4 files also requires FFmpeg to be installed and available on your system path. Set `render_videos = False` to run without it.

## Data and references

Genotype data come from the [1000 Genomes Project Phase 3 collection](https://www.internationalgenome.org/data-portal/data-collection/phase3), using chromosome 22 records from 2,504 individuals.

Method references and acknowledgments are included at the bottom of my notebook.
