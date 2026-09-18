Week 02 — SVD Image Compression
Image sources and licence
No images are uploaded or hand-fetched from a URL. `images/` is populated
at notebook run-time straight from `scikit-image`'s bundled sample
dataset, so anyone with `pip install scikit-image` gets byte-identical
images with zero setup — no re-uploading a file, no hunting down a working
link:
`moon_smooth.png` ← `skimage.data.moon()` — smooth / low-detail: mostly
flat black sky with a gently shaded lunar disc. Bundled with
scikit-image, BSD-3-Clause (package licence; no separate per-image notice
is documented by the project for this file, it's one of the long-standing
classic scikit-image test images).
`grass_textured.png` ← `skimage.data.grass()` — high-detail / textured: a
real macro photograph of grass. Per scikit-image's own docstring, this
was downloaded from DeviantArt and is licensed CC0 (public domain
dedication); scikit-image redistributes a cropped, greyscale 512x512 crop
of it.
`text_page.png` ← `skimage.data.page()` — the "of your choosing" image: a
scanned page of printed text (flat background + many sharp small-scale
edges). Bundled with scikit-image, BSD-3-Clause.
`astronaut_colour.png` ← `skimage.data.astronaut()` — used only for the
R7 colour-space stretch (the other three images are single-channel and
have no real colour to exploit). A NASA photo of astronaut Eileen
Collins; per scikit-image's docstring it has no known copyright
restrictions and is in the public domain.
`scikit-image` itself is BSD-3-Clause licensed
(https://github.com/scikit-image/scikit-image/blob/main/LICENSE.txt).
How to run
Google Colab
`File > Upload notebook` and select `NaveenKumar_project2_svd.ipynb` (or drag it
onto the Colab file picker). No other file needs uploading — the
notebook creates `images/` itself in the Colab runtime's local storage
and pulls the four sample images straight out of `scikit-image`.
In the first code cell, add one line above the imports to make sure
`scikit-image` (already preinstalled on Colab, but occasionally an
older version) and `jupytext` are current:
```python
   !pip install -q --upgrade scikit-image jupytext
   ```
`Runtime > Run all`. Every image, plot and metrics table regenerates
from scratch in a couple of minutes — nothing is loaded from a file you
have to provide.
To get the images or figures back out of the Colab VM (e.g. to check
into git), either `Files > images/ > Download`, or run in a cell:
```python
   from google.colab import files
   import shutil
   shutil.make_archive("images", "zip", "images")
   files.download("images.zip")
   ```
`project2_svd.py` (jupytext "percent" format) is the plain-text source for
`project2_svd.ipynb`. Colab doesn't edit `.py` files directly, so if you
want to work from the text source instead: upload `project2_svd.py`,
`!pip install -q jupytext`, then in a cell
`!jupytext --to notebook project2_svd.py -o project2_svd.ipynb`, then open
the resulting `.ipynb` from the file browser on the left.
`load_images.py` is a small standalone script that does the same image
export on its own — in Colab: upload it and run `!python3 load_images.py`
— useful if you just want the PNGs in `images/` without running the whole
notebook.
Local Jupyter (alternative)
```bash
pip install numpy scipy matplotlib pillow scikit-image jupytext jupyter nbconvert pandas
jupyter notebook NaveenKumar_project2_svd.ipynb
# or, to re-execute headlessly and refresh all outputs:
jupyter nbconvert --to notebook --execute --inplace project2_svd.ipynb
```
Contents
`NaveenKumar_project2_svd.ipynb` — the full analysis (R1–R6, plus an R7 colour-space
stretch): loading, greyscale conversion, SVD, truncated reconstructions,
honest storage/error/energy metrics, break-even rank, three k-selection
criteria, cross-image comparison, and a noise/denoising experiment.
`images/` — source PNGs (written out by the notebook/`load_images.py`)
and every figure the notebook saves.
