clickrank/
├─ README.md
├─ requirements.txt
├─ data/
│  ├─ raw/
│  ├─ processed/
├─ notebooks/
│  ├─ 01_simulate_ad_clicks.ipynb
│  ├─ 02_feature_engineering.ipynb
│  ├─ 03_ctr_model_training.ipynb
│  ├─ 04_ranking_and_auction.ipynb
│  ├─ 05_bandits_for_cold_start.ipynb            ← Bandits
│  ├─ 06_deep_ctr_wide_and_deep.ipynb            ← Deep Learning (optional)
│  └─ 07_ab_test_simulation.ipynb
└─ src/
   ├─ simulate_data.py
   ├─ ranking_utils.py
   ├─ bandit_utils.py                            ← Bandit Algorithms
   ├─ deep_ctr.py                                ← Wide&Deep Model
   └─ ab_test_utils.py