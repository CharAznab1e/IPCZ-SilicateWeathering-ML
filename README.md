==========================================
Multi-Model Ensemble Weathering Flux Predictor
==========================================

A MATLAB ensemble machine learning tool for predicting silicate weathering fluxes
in the Indo-Pacific Convergence Zone during Quaternary glacial cycles.

== OVERVIEW ==

This program implements a multi-model ensemble approach that combines five
machine learning algorithms to predict silicate weathering fluxes with enhanced
robustness and accuracy. The ensemble employs R²-weighted averaging, where
better-performing models contribute more to the final prediction.

Associated Research: This code accompanies the manuscript "Rainfall amplified
sea-level control on silicate weathering in the Indo-Pacific Convergence Zone
during Quaternary glacials" (currently under review in Communications Earth & Environment).

== KEY FEATURES ==

Ensemble Models:

GANs-GRU-LSTM – Deep learning for complex temporal patterns

Bagging – Bootstrap aggregating for variance reduction

Random Forest – Ensemble of decision trees

SVM – Support Vector Machine for robust classification

Boosting – Gradient boosting for sequential error correction

Outputs:

Individual model predictions

R²-weighted ensemble prediction

Uncertainty range (min-max across models)

Visualizations of model comparisons

== REQUIREMENTS ==

Software:

MATLAB (R2020a or later recommended)

Statistics and Machine Learning Toolbox

Deep Learning Toolbox (for GANs-GRU-LSTM)

Data Files:
The program expects the following directory structure:

Project Folder/
├── Machine Learning Models/ # Pre-trained models folder
│ ├── GANs_GRU_LSTM.mat
│ ├── Bag.mat
│ ├── SVM.mat
│ ├── RandomForest.mat
│ └── Boosting.mat
├── ModelInput.xlsx # Training data reference
└── Clim.xlsx # Test climate data

== QUICK START ==

Setup Directory
Place the program file (main_ensemble_prediction.m) in your project root folder
with the structure above.

Prepare Input Data
The test data (Clim.xlsx) should contain:

Column 1: Age (kyr BP)

Column 2: CO₂ concentration

Column 3: Temperature

Column 4: Sea level

Note: The test data provided is from Willeit et al. (2019) and is for
demonstration only. For scientific applications, use appropriate paleoclimate
reconstructions as described in our manuscript.

Run the Program
In MATLAB command window:
main_ensemble_prediction

View Results
The program generates two figures:

Figure 1: Individual model predictions with ensemble average

Figure 2: Ensemble prediction with uncertainty range

== MODEL WEIGHTS ==

Weights are calculated based on test R² scores:
Weight_i = R²_i / Σ(R²_j) for j=1 to 5

This ensures models with better validation performance contribute more to the
final ensemble prediction.

== CUSTOMIZATION ==

For Different Time Periods:
Modify the time selection in Section 2:
idx = find(age_input <= YOUR_AGE_LIMIT);

For Different Input Variables:
Update the feature matrix in Section 2:
% Current features: sea level, temperature, CO₂
X = [sealevel, temp, co2];
% Add/remove variables as needed

For Different Output Normalization:
Adjust the denormalization parameters in Section 3 if your target variable has
different ranges.

== IMPORTANT NOTES ==

Data Sources:

Test Data: Clim.xlsx contains data from Willeit et al. (2019) for testing purposes only

Training Data: ModelInput.xlsx contains the reference data used for model training and denormalization

Reproducibility:
The .mat files contain models trained in this study. Detailed methodology can be
found in our manuscript. We used a fixed random seed (rng(42)) to ensure
reproducibility of our results.

Citation Requirements:
If you use this code in your research, please cite:

Our main manuscript (once published)

The original machine learning algorithms as appropriate

Any input data sources used

Publication Status: This code accompanies a manuscript under review. Please do
not cite or distribute until the associated paper is formally published.

== CONTACT ==

Scientific Inquiries:

Dr. Zhaokai Xu: zhaokaixu@qdio.ac.cn

Dr. Debo Zhao: zhaodebo@qdio.ac.cn

Code & Technical Questions:

Yifei Yang: yangyifei@qdio.ac.cn

Test Data Reference:
Willeit, M., Ganopolski, A., Calov, R., & Brovkin, V. (2019). Global mean CO₂,
temperature and sea level data from transient model simulations of Quaternary
glacial cycles. PANGAEA. https://doi.org/10.1594/PANGAEA.902277

==========================================
END OF README
==========================================

