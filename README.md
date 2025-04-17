# Market-Regime-Detection-using-Unsupervised-Learning
Market Regime Detection using Unsupervised Learning

Project Overview
This project aims to segment financial markets into distinct behavioral regimes using unsupervised learning techniques. By analyzing high-frequency limit order book and trade volume data, the goal is to identify whether the market is Trending vs Mean-Reverting, Volatile vs Stable, and Liquid vs Illiquid. These insights are valuable for market strategy development and predictive modeling.

Objective
Detect and segment market regimes based on key factors:

1. Trending vs Mean-reverting

2. Volatile vs Stable

3. Liquid vs Illiquid

Using unsupervised learning on real-time data derived from order book and trade volume features.

Data Sources
The following datasets were used for regime detection:

depth20: The top 20 levels of the order book data (price, quantity for bid/ask)

aggTrade: Aggregate trade volume data (per second or event)

You can access the data here: Data Link

Step-by-Step Breakdown
1. Feature Engineering
Extracted meaningful, hand-crafted features from each timestamp’s data:

Liquidity & Depth Features:

Bid/Ask Spread

Order Book Imbalance (at various levels)

Microprice (weighted average price of bid and ask)

Cumulative Depth

Volatility & Price Action Features:

Rolling Mid-Price Return (log of mid-price change)

Price Volatility (standard deviation of returns)

Volume Features:

Volume Imbalance (buy vs sell volume)

Cumulative Volume (over time windows)

VWAP shift (change in VWAP over short periods)

Derived Features:

Sloped Depth (decay of size away from top of book)

Trade Wipe Level (average number of levels wiped during trades)

2. Data Normalization
Standardization: Z-score or min-max normalization applied.

Dimensionality Reduction: PCA used for feature reduction to capture dominant features.

3. Clustering
Utilized clustering algorithms to segment the market:

K-means: Determined optimal clusters using elbow plot.

HDBSCAN: Identified non-spherical clusters and handled noise.

Gaussian Mixture Models (GMM): Generated soft probabilities for each data point.

Clustering performance was evaluated using metrics like silhouette score and Davies-Bouldin index.

4. Regime Labeling and Analysis
Each timestamp was assigned a market regime label based on clustering results:

Regime Characteristics: Average volatility, typical spread, liquidity, and price directionality.

Regime Examples:

Regime 0: Mean Reverting & Liquid & Stable

Regime 1: Trending & Liquid & Volatile

Regime 2: Trending & Illiquid & Volatile

5. Visualizations
Regime Evolution: Visualized regime labels over time, comparing market behavior.

t-SNE/UMAP: 2D projections of clusters to visualize the separation of regimes.

6. Regime Change Insights
Transition Matrix: Analyzed the probability of transitioning from one regime to another.

Insights: Revealed high self-transition probabilities, indicating stable market regimes.

Results & Insights
PCA and SVD showed that the first component in both methods captured over 99% of the variance in the data, indicating a dominant feature.

Clustering Results: HDBSCAN showed the best cohesion with varying numbers of clusters, while KMeans and GMM provided moderate performance.

Regime Stability: Regimes, especially Regime 2 (Trending & Liquid & Stable), demonstrated high persistence, making them ideal for predictive modeling.

Regime Transitions: The analysis showed low transition rates, suggesting that regimes are relatively stable, which is beneficial for developing specific market strategies.

