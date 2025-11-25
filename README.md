# ClickRank 

ClickRank is a fully-built, production-style machine learning project that simulates a real ad-ranking pipeline used in companies like Meesho, Flipkart, Swiggy, Meta, Google Ads, etc.
It covers the entire lifecycle of an ad prediction system — from synthetic data generation to auction ranking, bandits for cold start, and A/B test simulation.

This project aims to show my skills in data engineering, feature engineering, machine learning, deep learning, experimentation, and ranking algorithms.

## Project Features

1. Data Simulation

Generates realistic users, ads, impressions, CTR patterns, device behaviour, time-of-day effects, and auction-level structures.

2. Feature Engineering

Includes:
	•	One-Hot Encoding
	•	Standardization
	•	Rich handcrafted features

All optimized using a ColumnTransformer.

3. CTR Modeling

Trains multiple industry-standard CTR models:
	•	Logistic Regression
	•	Random Forest
	•	XGBoost
	•	LightGBM
	•	Wide & Deep Neural Network (PyTorch)

Each model is evaluated on:
	•	AUC
	•	LogLoss
	•	PR-AUC
	•	Accuracy
	•	Brier Score

4. Ranking & Auction Simulation

Implements:
	•	Bid-based ranking
	•	Predicted CTR ranking
	•	eCPM ranking (bid × pCTR)

Measures:
	•	CTR uplift
	•	Revenue per impression
	•	Winner distribution

5. Bandit Algorithms for Cold Start

Implements and compares:
	•	Epsilon-Greedy
	•	UCB1
	•	Thompson Sampling

Tracks:
	•	Regret
	•	Reward curves
	•	Convergence behaviour

6. A/B Testing Simulation

Builds a full statistical testing pipeline:
	•	Variant simulation
	•	CTR comparison
	•	Two-proportion Z-test
	•	p-value computation
	•	Required sample size estimation for target power


# Results

1. CTR Models (Baseline ML Models)

Model	Train AUC	Val AUC	Train LogLoss	Val LogLoss	PR-AUC (Val)	Accuracy (Val)
LightGBM	0.5993	0.5466	0.6676	0.6723	0.5988	0.5968
XGBoost	0.5857	0.5468	0.6687	0.6719	0.5979	0.5974
Random Forest	0.6024	0.5465	0.6676	0.6721	0.5974	0.5966
Logistic Reg	0.5447	0.5468	0.6882	0.6878	0.5996	


LightGBM and Random Forest performed the best
Validation AUC ~0.547 is reasonable for synthetic ad-CTR data.

2. Wide & Deep Model (Deep Learning)

Epoch	Train AUC	Val AUC	Train LogLoss	Val LogLoss
1	0.5384	0.5473	0.6819	0.6730
2	0.5475	0.5474	0.6733	0.6721
3	0.5515	0.5474	0.6724	0.6725
4	0.5600	0.5469	0.6714	0.6727

The Wide & Deep model converges similarly to LightGBM, with stable validation curves.
Deep models usually show meaningful improvements only on much larger real datasets.

3. Auction Strategy Comparison

Strategy	CTR	Revenue	Revenue / Impression
Bid Only	0.5859	1,249,986	3.1249
pCTR (LGBM)	0.6399	979,195	2.4479
eCPM = Bid × pCTR	0.5975	1,265,390	3.1634

4. Bandit Algorithms (Cold Start)

Policy	Total Clicks	Average CTR	Final Regret
Epsilon Greedy	7085	0.1417	415.0
UCB1	6586	0.1317	914.0
Thompson Sampling	7380	0.1476	120.0

Thompson Sampling performs best

5. A/B Test Simulation

Observed CTRs:
	•	Variant A: 0.0559
	•	Variant B: 0.0597

Z-test Results:
	•	Z-score: 3.64
	•	p-value: 0.00013 (significant)
	•	Required sample size: 34,025 per group

B is statistically significantly better than A