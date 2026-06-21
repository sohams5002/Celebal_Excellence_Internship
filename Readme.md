# Week 1 Task

### Overview

This week one task serves as a complete data processing and statistical analysis pipeline. While the baseline curriculum requirement was to perform core statistical and algebraic operations, I designed this task to resemble a real-world environment. Built entirely using core Python libraries, the pipeline automates data cleaning and hypothesis testing, while also integrating a custom model-monitoring module to detect data degradation and time-series stationarity in real-time.

### Impact & Results

* **Defensive Data Pipeline:** Automated the handling of missing data, such as median and mean interpolation, and categorical filtering using efficient, vectorized Pandas operations. This ensured no data leakage during downstream statistical testing.
* **Production-Grade Monitoring:** Recognizing that static models fail in practice, I implemented a Population Stability Index (PSI) calculator from scratch. This provides a mathematical trigger for Concept and Covariate drift without relying on heavy external machine learning frameworks.
* **Algorithmic Efficiency:** I avoided using heavy machine learning libraries like Scikit-Learn by manually creating model evaluation metrics, including MAE, MSE, RMSE, R-squared, and Adjusted R-squared, using pure NumPy. This drastically reduced the system's memory footprint.

### Proactive Engineering & Conceptual Synthesis

Beyond executing standard Python logic, I designed this task to connect abstract mathematics and applied machine learning:

* **The "Why" Behind Dimensionality Reduction:** Rather than just using a pre-packaged PCA function, I used Singular Value Decomposition (SVD) to manually reconstruct matrices and perform rank-1 approximations. This shows a fundamental understanding of how algorithms find the directions of maximum variance in high-dimensional space.
* **Mathematical Justification for Machine Learning:** Instead of blindly trusting dataset distributions, I created rigorous statistical checks. I used Kolmogorov-Smirnov (KS) tests to validate normality and implemented Augmented Dickey-Fuller (ADF) tests, including differencing, to mathematically prove time-series stationarity. This supports the key assumptions needed for linear models and T-tests to work accurately on messy, real-world data.
* **Geometric Matrix Transformations:** I didn't just calculate Eigenvalues and Eigenvectors; I verified the equation `A @ v = λ * v` and visualized the vectors to show how a matrix "stretches" or "squishes" data geometrically.

### Technologies Used

* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Statistical Modeling & Probability:** SciPy (`scipy.stats`), Statsmodels (`statsmodels.tsa.stattools`)
* **Data Visualization:** Matplotlib

### Challenges Overcome

**Challenge:** Standardizing data visualizations and statistical overlays, like Kernel Density Estimations, while keeping environment dependencies limited to Matplotlib and SciPy, avoiding pre-packaged libraries such as Seaborn to maintain a lightweight system.

**Solution:** I developed a custom visualization pipeline by generating the Kernel Density Estimate using `scipy.stats.gaussian_kde` and mapping it to a linearly spaced NumPy array. This achieved the same analytical result as heavier libraries while keeping the task's dependency footprint optimized and purely mathematical.

### Quick Start / Setup

1. Download this notebook to your local machine.
2. Ensure you have the standard data science tools installed: `pip install numpy pandas scipy matplotlib statsmodels`
3. Open the Jupyter Notebook environment to interact with the pipeline.
4. Run the **Setup Cell** at the top of the notebook to initialize all libraries and load the foundational data arrays before executing specific analysis blocks.
