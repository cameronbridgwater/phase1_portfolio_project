# Facebook Post Interaction Predictor

Analyzes Facebook post metrics to predict Total Interactions (likes + comments + shares) using Linear, Ridge, and Lasso regression models. **Best performing model: Lasso (R² = 0.49 log data, 0.95 original)**.

## 🎯 Project Overview

Built regression models to understand which Facebook post features drive engagement. **Key insights:**
- **Lifetime Post Consumers (+1415)**: More unique people clicking = more interactions
- **Lifetime Post Consumptions (-1248)**: Too many clicks per post = engagement drop-off  
- **Paid posts (+20.8)**: Higher effort content gets more reach
- **Timing matters slightly**: Earlier months/hours perform marginally better

## 📊 Data Overview

**Source**: Facebook Page Posts dataset (~500 posts analyzed)

**Target**: `Total Interactions` = likes + comments + shares

### 📁 Dataset Files

- **raw_facebook_data.csv** — Original imported dataset.  
- **original_cleaned_facebook_data.csv** — Cleaned dataset (no log transformation).  
- **log_cleaned_facebook_data.csv** — Cleaned dataset with log transformation applied.  

These files represent the main stages of data preparation used for the analysis and visualizations in this project.


### 🎯 Key Features (Top Impact)
| Feature | Data Type | Description | Model Coefficient |
|---------|-----------|-------------|-------------------|
| **Lifetime Post Consumers** | Integer | Unique people who clicked post | **+1415** |
| **Lifetime Post Consumptions** | Integer | Total clicks anywhere in post | **-1248** |
| **Paid** | Boolean | Post was paid/boosted | **+20.8** |
| **Post Month** | Integer | Month posted (1-12) | **-7.9** |
| **Post Hour** | Integer | Hour posted (0-23) | **-1.7** |

### 🔧 Preprocessing Applied
- **Log transformation**: Fixed right-skewed distributions
- **Feature selection**: Lasso dropped multicollinear vars (Lifetime Engaged Users)
- **Encoding**: One-hot for categorical (Post Type, Category)

## 🤖 Models & Performance

| Model  | Log Data R² | Original R² | Status     |
|--------|-------------|-------------|------------|
| Linear | 0.27        | 0.92        | Overfits   |
| Ridge  | 0.45        | 0.47        | Stable     |
| **Lasso** | **0.49**  | **0.95**    | **🏆 Best** |

**Lasso automatically dropped multicollinear features** (Lifetime Engaged Users, etc.)

## 📈 Key Insights

| Feature | Coefficient | Interpretation |
|---------|-------------|----------------|
| **Lifetime Post Consumers** | **+1415** | ✅ More unique clickers = More engagement |
| **Lifetime Post Consumptions** | **-1248** | ❌ Too many clicks/post = Fatigue |
| **Paid** | **+20.8** | 💰 Higher effort content performs better |
| **Post Month** | **-7.9** | ⏰ Earlier months slightly better |
| **Post Hour** | **-1.7** | ⏰ Earlier hours slightly better |


## 🚀 Quick Start

# Clone repo
git clone https://github.com/yourusername/facebook-post-predictor.git
cd facebook-post-predictor

# Install dependencies
pip install -r requirements.txt

# Run analysis notebooks
jupyter notebook explore.ipynb
jupyter notebook model.ipynb

# View data files
head data/raw_facebook_data.csv

## 📁 Project Structure

### 📁 Project Structure

- **facebook-post-predictor/**
  - **code/**
    - `explore.ipynb` — EDA & visualizations  
    - `transform.ipynb` — Data cleaning & log transform  
    - `model.ipynb` — Ridge/Lasso modeling  
  - **data/**
    - `raw_facebook_data.csv`
    - `original_cleaned_facebook_data.csv`
    - `log_cleaned_facebook_data.csv`
  - - **docs**
    - 3-Table2-1.png
    - 4-Table3-1.png
    - explore_pairplot.png
    - README.md


## 🛠️ Tech Stack
pandas           # Data manipulation
scikit-learn     # Ridge/Lasso regression
seaborn          # Visualizations
matplotlib       # Charts
numpy            # Log transformations
jupyter          # EDA notebooks

## 📋 Requirements
pandas>=1.5.0
scikit-learn>=1.2.0
seaborn>=0.12.0
matplotlib>=3.6.0
numpy>=1.24.0
jupyter>=1.0.0

## 🎯 Business Recommendations

1. **Create clickable content** - Drive unique consumer engagement (Lifetime Post Consumers +1415)
2. **Avoid click fatigue** - Don't over-optimize single posts (Lifetime Post Consumptions -1248)
3. **Post earlier** in month/hour for slight edge (Month -7.9, Hour -1.7)
4. **Invest in paid** for high-effort posts (+20.8 coefficient)

## 📈 Next Steps

- [ ] Test recommendations on new time periods
- [ ] Add post text sentiment analysis
- [ ] Deploy as Streamlit prediction app
- [ ] A/B test posting timing recommendations
- [ ] Scale to multi-page Facebook dataset


 Built by Cameron Bridgwater | The Knowledge House Data Analytics Fellow | NYC | March 2026