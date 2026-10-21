# Hyperspectral Satellite Image Classification

Pixel-wise classification experiments for the Indian Pines hyperspectral
dataset. The notebooks compare spectral dimensionality reduction,
traditional machine-learning classifiers, and spatial post-processing
techniques.

## Highlights

- Principal Component Analysis (PCA) for spectral dimensionality reduction
- PCA followed by Linear Discriminant Analysis (LDA)
- SVM, k-nearest neighbors, Random Forest, and XGBoost classifiers
- Majority-filter spatial smoothing as a practical MRF-style post-processing
  step
- Gabor and Random Patch Convolution (GRPC) spatial-spectral features
- Accuracy and classification-report evaluation in the experiment notebooks

## Repository layout

```text
dataset/
├── Indian_pines_corrected (1).mat   # Hyperspectral image data
├── Indian_pines_gt.mat              # Ground-truth labels
└── pixels.csv                       # Flattened pixel-level representation

research/
├── data_analysis.ipynb
├── dataset_setup.ipynb
├── GRPC-based Hyperspectral Image Classification.ipynb
├── PCA+classification.ipynb
└── PCA+LDA+Markov Random Field.ipynb
```

## Dataset

The project uses the [Indian Pines dataset](https://www.ehu.eus/ccwintco/index.php/Hyperspectral_Remote_Sensing_Scenes).
The image contains 200 usable spectral bands over a 145 × 145 pixel scene.
Ground-truth label `0` represents background and is excluded from the
training examples in the notebooks unless otherwise noted.

The `.mat` files are loaded directly by the notebooks. `pixels.csv` provides
a flattened view for workflows that prefer tabular data.

## Experiments

Open the notebooks in `research/` with Jupyter Notebook, JupyterLab, or
another compatible environment. The main workflows are:

| Notebook | Description |
| --- | --- |
| `data_analysis.ipynb` | Dataset inspection and visualization |
| `dataset_setup.ipynb` | Dataset preparation and pixel extraction |
| `PCA+classification.ipynb` | PCA with SVM, Random Forest, k-NN, and XGBoost |
| `PCA+LDA+Markov Random Field.ipynb` | PCA/LDA classification and spatial smoothing |
| `GRPC-based Hyperspectral Image Classification.ipynb` | Gabor and RPC spatial-spectral features |

Reported results are notebook outputs and can vary with preprocessing,
random seeds, train/test splits, and library versions. The existing
experiments include the following indicative results:

| Method | Accuracy | Notes |
| --- | ---: | --- |
| Raw SVM (200D) | 55.8% | High spectral dimensionality and longer training |
| PCA (22D) + XGBoost | 85.0% | Reduced noise and faster prediction |
| PCA (22D) + Random Forest | 82.0% | Stable ensemble baseline |
| GRPC + SVM | 99.91% | Strong spatial-spectral representation; computationally intensive |

## Getting started

1. Clone the repository:

   ```bash
   git clone https://github.com/rayenelatti-svg/hyperspectral-satellite-image-classification.git
   cd hyperspectral-satellite-image-classification
   ```

2. Install the notebook dependencies used by the experiments:

   ```bash
   pip install jupyter numpy pandas scipy scikit-learn matplotlib seaborn xgboost
   ```

3. Launch Jupyter:

   ```bash
   jupyter lab
   ```

4. Open a notebook from `research/` and run its cells from top to bottom.

Some notebooks perform computationally expensive operations, especially the
GRPC feature-extraction workflow. A machine with sufficient memory is
recommended.

## References

- [Hyperspectral Remote Sensing Scenes - Indian Pines](https://www.ehu.eus/ccwintco/index.php/Hyperspectral_Remote_Sensing_Scenes)
- Shenming Q. et al. (2022), [A new hyperspectral image classification
  method based on PCA, LDA and extended hidden Markov random
  fields](https://www.nature.com/articles/s41598-022-05422-5)
- TV Bandos et al. (2009), [Classification of Hyperspectral Images With
  Regularized Linear Discriminant Analysis](https://rslab.disi.unitn.it/papers/R68-TGARS-Bandos.pdf)
- Datta D. et al. (2022), [Hyperspectral Image Classification: Potentials,
  Challenges and Future Directions](https://pmc.ncbi.nlm.nih.gov/articles/PMC9071975/#sec4)
- [Hyperspectral Imaging](https://arxiv.org/html/2508.08107v1)
- J. Li et al. (2024), [A new hyperspectral image classification method based
  on spatial-spectral features](https://rdcu.be/eYsGq)

## License

No license is currently provided. All rights are reserved unless otherwise
stated by the copyright holder.
