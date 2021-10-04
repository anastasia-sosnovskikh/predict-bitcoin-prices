# bitcoin
Predict the Closing Price of Bitcoin in the Next 6 Months
---
### Time Series Forecasting

Please refer to  the `research-proposal-and-discussion` for the research rationale and background literature, `presentation` for the quick summary of the project, and the rest of the files for the actual code and analysis.

##### Quick Glance at the Methods: 
* Unsupervised
 * **K-means** (tuned based on TSS)
 * **K-Means with Differencing**: detrending the series to avoid the autocorrelation
* Supervised
 * **ARIMA** (tuned based on AIC)
 * **Single Exponential Smoothing (SES) with Seasonal and Trend decomposition using Loess (STL) Decomposition**
 * **Holt-Winters method**
 * **ARIMA with CV** (tuned based on AIC)

---
#### 0. Get the Data
Scraping the complete Bitcoin Data from 2009 as well as gettingthe following exogenous variables:
* Gold
* Crude Oil
* S&P 500
* Vanguard Financials Index Fund ETF
* Vanguard Information Technology Index Fund ETF
* NVIDIA

The exogenous variables are chosen from the background literature search and current market analysis.

#### 1. Exploratory Data Analysis and Preprocessing

Libraries used: `numpy`, `pandas`, `statsmodels`, `seaborn`, `matplotlib`

EDA and preprocessing include changing column names, data types, missing values, uniques values.  
Visualizations are done without any transformation and then with `log` transformation because of drastically different scale of bitoin prices over time.   
The graphs include:
  * line plots
  * box plots
  * violin plots
  * bar plots
  * **lag** plots
  * **autocorrelation** plots

There are also **time series decomposition plots** done.  
Observed and seasonally adjusted trends are compared. 

#### 2. Unsupervised Learning

Libraries used: `sklearn`.

##### Models
* Clustering (with tuning)
  * **K-means**
  * **K-Means with Differencing**: detrending the series to avoid the autocorrelation.

**Total within sum of squares (TSS)** was used to choose the *optimal number of clusters*.

#### 2. Supervised Learning

Libraries used: `sklearn`, `statsmodels`, `itertools`.

##### Methods:
* **ARIMA** 
* **Single Exponential Smoothing (SES) with Seasonal and Trend decomposition using Loess (STL) Decomposition**
* **Holt-Winters method**
* **ARIMA with CV**

**Akaike Information Criterion (AIC)** was used to choose the best tuning parameters for ARIMA models.

**Root Mean Square Error (RMSE)** was used to choose the best performing model.
