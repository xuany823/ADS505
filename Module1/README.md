# Charles Book Club Campaign Analysis

##  Project Overview
This project analyzes customer data from **Charles Book Club** to design a more efficient direct-mail campaign for promoting the book *The Art History of Florence*.  
Instead of mailing all members — which is costly and produces a low average response rate: the goal was to use **data mining and predictive modeling** to identify the customers most likely to purchase. By targeting these customers, the business can reduce wasted mailings, improve ROI, and establish a data-driven framework for future campaigns.

---

##  Business Objective
- **Current challenge:** Mailing all customers results in only ~8% responding, meaning high costs with limited payoff.  
- **Objective:** Identify the **segments and customers** most likely to buy *The Art History of Florence*.  
- **Key questions:**  
  1. Which customer segments (RFM categories) have above-average response rates?  
  2. Can predictive models (k-NN, Logistic Regression) outperform the baseline mailing strategy?  
  3. What cutoff strategy should be used to select customers for the next campaign?  

---

## Dataset
- **Source:** Charles Book Club dataset.  
- **Records:** 4000 customers, partitioned into:  
  - Training set: 2400 (60%)  
  - Validation set: 1600 (40%)  
- **Target variable:** `Florence` (1 = purchased the book, 0 = did not).  
- **Predictors (16 total):**  
  - `R`: Recency (months since last purchase)  
  - `F`: Frequency (total purchases)  
  - `M`: Monetary (total spend in dollars)  
  - `FirstPurch`: Months since first purchase  
  - `RelatedPurch`: Past related-category purchases  
  - Additional demographic and purchase history features  

---

##  Methods
1. **Exploratory Data Analysis (EDA)**  
   - Histograms, boxplots, and correlation heatmaps.  
   - RFM segmentation (4×5×3 = 60 combinations).  

2. **Modeling**  
   - **k-NN Classifier (uniform weights):** k = 1–11, best k = 10.  
   - **k-NN Regressor (distance weights):** smoother probability estimates.  
   - **Logistic Regression:**  
     - Full model (16 predictors).  
     - Subset model (key predictors: R, F, M, FirstPurch, RelatedPurch).  

3. **Evaluation Metrics**  
   - Baseline response rate (~8%).  
   - Accuracy and AUC (for validation).  
   - Lift and Gains charts.  
   - Lift@equal-N (targeting as many customers as actual buyers).  

---

##  Results
- **RFM Segmentation:** Identified 22 above-average segments with validation response rates of ~11%.  
- **k-NN (k=10):** Response rate ~12%, Lift ≈ 1.4.  
- **k-NN Regressor:** Lift improved slightly (~1.5), better ranking performance.  
- **Logistic Regression:** With subset predictors, response rate ~12%, Lift 1.4–1.5.  

---

##  Recommendations
- **Adopt targeted mailing:** Focus only on customers with ≥30% predicted likelihood of purchase.  
- **Expected outcome:** Increase response rates from 8% (baseline) to ~12% in targeted groups.  
- **Impact:** Reduced mailing costs, higher ROI, and a repeatable data-driven approach for future promotions.  

---

## Example Visuals
- Distribution plots of R, F, M.  
- Correlation heatmap.  
- Lift and Gains charts for k-NN and Logistic Regression.  

---

## How to Run
1. Clone this repository.  
2. Install dependencies:
   Make sure you have Python 3.9+ and then install the required packages:  
   ```bash
   pip install -r requirements.txt
4.	Open Jupyter/VS Code and run notebooks step by step.

# Contact

Prepared by Michelle Wang  
Applied Data Science, University of San Diego  
Helping Charles Book Club improve ROI through data-driven campaign targeting.
