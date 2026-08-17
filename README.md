# SmartCart Customer Segmentation

SmartCart is an unsupervised machine-learning project that groups retail customers by income, spending, household profile, purchase behavior, and campaign response. The resulting segments can help a retailer replace broad marketing campaigns with more relevant offers for high-value, price-sensitive, and low-engagement customer groups.

## Problem

Retail customer data contains many overlapping behavioral and demographic signals. Looking at any one feature—such as income or recent purchases—does not reveal the distinct groups needed for useful targeting. This project builds an end-to-end segmentation workflow that cleans those signals, reduces their dimensionality, and identifies interpretable customer clusters.

## Approach

The notebook performs the following steps:

1. Fills missing income values with the median.
2. Engineers age, customer tenure, total spending, total children, education level, and living arrangement.
3. Removes implausible age and income outliers.
4. One-hot encodes categorical features and standardizes numeric features.
5. Uses Principal Component Analysis (PCA) for three-dimensional representation.
6. Compares candidate cluster counts using the elbow method and silhouette score.
7. Applies K-Means and agglomerative clustering.
8. Profiles each cluster using purchasing, income, household, and response characteristics.

## Key result

The elbow and silhouette analyses support **four customer segments**. The saved analysis identified groups broadly characterized as:

| Segment | General profile |
| --- | --- |
| 0 | Low-to-moderate income and spending, living with a partner |
| 1 | High income and spending, living with a partner |
| 2 | Lower income and spending, generally living alone |
| 3 | Moderate-to-high income and high spending, generally living alone |

The higher-spending segments also show more web, catalog, and store purchases and fewer monthly web visits, providing practical signals for channel and offer selection.

## Technology

- Python
- pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- K-Means and agglomerative clustering
- PCA
- KneeLocator

## Repository contents

```text
SmartCart-/
├── SmartCart_Customer_Segmentation.ipynb
├── requirements.txt
└── README.md
```

## Run locally

```bash
git clone https://github.com/yash807/SmartCart-.git
cd SmartCart-
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter notebook SmartCart_Customer_Segmentation.ipynb
```

Place the source dataset at the repository root as:

```text
smartcart_customers.csv
```

The dataset must contain the customer demographic, purchase-channel, campaign-response, and product-spending columns referenced in the notebook.

## Notebook viewing

The notebook outputs are intentionally cleared in Git to keep the repository lightweight and make GitHub rendering reliable. Run all cells locally to regenerate the tables and visualizations.

If GitHub's notebook preview is temporarily unavailable, open the notebook with [nbviewer](https://nbviewer.org/github/yash807/SmartCart-/blob/main/SmartCart_Customer_Segmentation.ipynb).

## Limitations and next steps

- Cluster labels describe this dataset and should be validated before business use.
- The current notebook is exploratory and does not serve predictions through an API.
- Future work could add cluster stability tests, reusable preprocessing pipelines, automated reports, and a dashboard for segment exploration.
