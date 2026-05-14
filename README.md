# Employee Sentiment Analysis

## Project Overview
This project analyzes employee engagement through email sentiment analysis. Using a dataset of **2,191 email messages** from **10 employees** spanning **January 2010 to December 2011**, we perform sentiment labeling, exploratory data analysis, scoring, ranking, flight risk identification, and predictive modeling.

## How to Run

### Prerequisites
- Python 3.8+
- Required packages: `pip install -r requirements.txt`

### Execution
1. Open `Employee_Sentiment_Analysis.ipynb` in Jupyter Notebook or JupyterLab
2. Run all cells sequentially
3. Outputs will be saved in the `visualizations/` folder

---

## Key Findings

### Sentiment Distribution
| Sentiment | Count | Percentage |
|-----------|-------|------------|
| Positive  | 1,144 | 52.21%     |
| Neutral   | 817   | 37.29%     |
| Negative  | 230   | 10.50%     |

### Top 3 Most Positive Employees (Overall)
| Rank | Employee       | Total Score |
|------|----------------|-------------|
| 1    | Lydia Delgado  | 123         |
| 2    | John Arnold    | 110         |
| 3    | Sally Beck     | 96          |

### Top 3 Most Negative Employees (Overall)
| Rank | Employee       | Total Score |
|------|----------------|-------------|
| 1    | Rhonda Denton  | 59          |
| 2    | Kayne Coulter  | 75          |
| 3    | Bobette Riner  | 88          |

### Flight Risk Employees
Employees flagged with **4+ negative emails within a rolling 30-day window**:

| Employee          | Status     |
|-------------------|------------|
| Lydia Delgado     | ⚠ At Risk  |
| Johnny Palmer     | ⚠ At Risk  |
| John Arnold       | ⚠ At Risk  |
| Eric Bass         | ⚠ At Risk  |
| Patti Thompson    | ⚠ At Risk  |
| Sally Beck        | ⚠ At Risk  |
| Bobette Riner     | ⚠ At Risk  |
| Rhonda Denton     | ⚠ At Risk  |

### Predictive Model Performance (Linear Regression)
| Metric | Value  |
|--------|--------|
| R²     | 0.7606 |
| RMSE   | 1.4466 |
| MAE    | 1.0300 |

---

## Insights & Recommendations

1. **Positive Culture:** Over 52% of messages are positive, indicating a generally healthy communication environment.
2. **Monitor Low Scorers:** Employees like Rhonda Denton and Kayne Coulter consistently show lower sentiment scores and should be monitored for engagement.
3. **Flight Risk Alert:** 8 out of 10 employees were flagged as flight risks at some point, suggesting periodic bursts of negativity that merit investigation.
4. **Predictive Power:** The linear regression model (R² = 0.76) shows that negative message ratio is the strongest predictor of low sentiment scores, followed by positive message ratio.
5. **Actionable Patterns:** Message frequency and content length have secondary but meaningful effects on sentiment scores.

---

## Project Structure
```
springer/
├── Employee_Sentiment_Analysis.ipynb  # Main analysis notebook
├── test (1).xlsx                      # Original dataset
├── requirements.txt                   # Python dependencies
├── README.md                          # This file
├── Final_Report.docx                  # Detailed report
└── visualizations/                    # All generated charts
    ├── sentiment_distribution.png
    ├── sentiment_over_time.png
    ├── employee_sentiment_breakdown.png
    ├── employee_monthly_scores.png
    ├── employee_rankings.png
    ├── flight_risk_employees.png
    ├── model_performance.png
    ├── feature_importance.png
    ├── message_frequency_heatmap.png
    ├── message_length_analysis.png
    └── polarity_distribution.png
```

## Methodology
- **Sentiment Labeling:** TextBlob NLP library with polarity thresholds (>0.05 = Positive, <-0.05 = Negative)
- **Scoring:** +1 (Positive), -1 (Negative), 0 (Neutral) aggregated monthly
- **Flight Risk:** Rolling 30-day window with ≥4 negative messages threshold
- **Modeling:** Scikit-learn Linear Regression with 80/20 train/test split
