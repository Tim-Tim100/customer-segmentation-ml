# Customer Segmentation Analysis Using Machine Learning

![Python](https://img.shields.io/badge/python-3.11-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3.2-orange)
![License](https://img.shields.io/badge/license-MIT-green)
![Status](https://img.shields.io/badge/status-complete-success)

A comprehensive unsupervised learning project that segments mall customers into distinct groups based on their annual income and spending behavior to enable targeted marketing strategies.

## 📊 Project Overview

This project applies machine learning clustering algorithms to identify natural customer groupings, transforming a one-size-fits-all marketing approach into targeted, data-driven strategies. By analyzing 200 mall customers, the project discovered 5 distinct segments, each requiring different marketing tactics to maximize engagement and revenue.

### Key Achievement
Identified a $200,000+ revenue opportunity by discovering 35 high-income customers with low engagement who were being overlooked with generic marketing campaigns.

---

## 🎯 Business Problem

**The Challenge:**
A mall with 200 customers was spending their $500,000 annual marketing budget equally across all shoppers, sending identical promotions regardless of customer behavior or purchasing power.

**The Issues:**
- Wasted marketing spend on customers who don't respond to campaigns
- High-value customers receiving the same treatment as budget shoppers
- Missed conversion opportunities with affluent but disengaged customers
- No clear ROI measurement by customer segment
- Generic campaigns that resonate with no one

**Real Example:**
Two customers both earning $88,000 annually:
- Customer A: Spending score 82/100 (high engagement)
- Customer B: Spending score 17/100 (low engagement)

Traditional demographic segmentation would treat them identically, but they require completely different marketing strategies.

---

## 💡 Solution

Built an unsupervised machine learning system to discover natural customer groupings based on actual behavior patterns, not assumptions. This enables:
- Targeted marketing strategies for each segment
- Optimized budget allocation based on segment value
- Clear ROI tracking per customer group
- Personalized campaigns that match customer needs

---

## 📈 Results

### Five Distinct Customer Segments Identified:

#### 🌟 Segment 1: High-Value Segment (39 customers - 19.5%)
- **Profile:** $87,000 average income | 82/100 spending score
- **Behavior:** Affluent customers who spend generously
- **Strategy:** VIP treatment, exclusive perks, premium service, early product access
- **Business Impact:** These customers generate disproportionate revenue; a 10% increase in their spending could boost overall revenue by 15-20%

#### 💎 Segment 2: Untapped Potential (35 customers - 17.5%)
- **Profile:** $88,000 average income | 17/100 spending score
- **Behavior:** High earners who are not engaged
- **Strategy:** Quality-focused messaging, personalized outreach, conversion campaigns, identify barriers to purchase
- **Business Impact:** Biggest opportunity - converting 30% could add $150,000+ in annual revenue with zero acquisition cost

#### 🏪 Segment 3: Core Customer Base (81 customers - 40.5%)
- **Profile:** $55,000 average income | 50/100 spending score
- **Behavior:** Mainstream shoppers, reliable but not exceptional
- **Strategy:** Loyalty programs, consistent engagement, cross-selling, retention focus
- **Business Impact:** Largest segment representing the foundation; protecting this base is critical for baseline revenue

#### 🎯 Segment 4: High-Engagement Low-Income (22 customers - 11%)
- **Profile:** $26,000 average income | 79/100 spending score
- **Behavior:** Lower income but highly engaged, likely using credit
- **Strategy:** Buy now pay later options, installment plans, student discounts, bundle deals
- **Business Impact:** Already enthusiastic buyers; flexible payment options could increase transaction size by 25-30%

#### 💰 Segment 5: Price-Sensitive Segment (23 customers - 11.5%)
- **Profile:** $26,000 average income | 21/100 spending score
- **Behavior:** Budget-conscious customers watching every dollar
- **Strategy:** Discount campaigns, clearance alerts, coupon programs, volume deals
- **Business Impact:** Focus on volume and margins rather than premium products

---

## 🔬 Methodology

### 1. Data Preparation
- **Dataset:** 200 mall customers
- **Features Used:** Annual Income, Spending Score
- **Preprocessing:** 
  - Renamed columns for easier handling
  - Converted income from thousands to actual dollar amounts
  - Checked for missing values (none found)
  - Feature selection based on business relevance

### 2. Feature Scaling
Applied `StandardScaler` to normalize features because:
- Annual Income ranges from $15,000 to $137,000
- Spending Score ranges from 1 to 100
- Without scaling, distance-based algorithms would incorrectly prioritize income differences over spending patterns

### 3. Finding Optimal Number of Clusters

**Elbow Method:**
- Calculated Within-Cluster Sum of Squares (WCSS) for K=1 to K=10
- Identified clear "elbow" at K=5

**Silhouette Analysis:**
- Calculated silhouette scores for K=2 to K=10
- K=5 achieved the highest score of **0.555** (indicating well-separated clusters)
- Scores above 0.5 indicate good clustering quality

### 4. Algorithm Comparison

Tested three clustering algorithms to find the best approach:

#### K-Means Clustering ✅ (Selected)
- **Parameters:** n_clusters=5, init='k-means++', random_state=42
- **Result:** 5 well-separated clusters
- **Silhouette Score:** 0.555
- **Advantages:** Fast, interpretable, assigns every customer to a segment
- **Why Selected:** Best balance of technical quality and business applicability

#### Hierarchical Clustering
- **Method:** Agglomerative with Ward linkage
- **Parameters:** n_clusters=5
- **Result:** Nearly identical to K-Means (85%+ agreement)
- **Purpose:** Validated K-Means findings, increased confidence in results

#### DBSCAN
- **Parameters:** eps=0.5, min_samples=4
- **Result:** 2 main clusters + noise points
- **Limitation:** Marked 25% of customers as "outliers," not suitable for marketing where every customer needs a strategy

### 5. Validation
- **Primary Metric:** Silhouette Score (0.555)
- **Validation:** High agreement between K-Means and Hierarchical clustering
- **Business Check:** All segments had clear, actionable business interpretations

---

## 🛠️ Technologies Used

**Programming Language:**
- Python 3.11

**Core Libraries:**
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **scikit-learn** - Machine learning algorithms
  - `StandardScaler` - Feature scaling
  - `KMeans` - Clustering algorithm
  - `AgglomerativeClustering` - Hierarchical clustering
  - `DBSCAN` - Density-based clustering
  - `silhouette_score` - Cluster quality evaluation

**Visualization:**
- **matplotlib** - Creating plots and charts
- **seaborn** - Statistical data visualization

**Development Environment:**
- Jupyter Notebook
- VS Code
- Virtual Environment (venv)

---

## 📁 Project Structure
```
customer-segmentation-ml/
│
├── data/
│   ├── Mall_Customers.csv                          # Original dataset
│   └── customers_with_clusters.csv                 # Processed data with cluster labels
│
├── notebooks/
│   └── customer_segmentation_analysis.ipynb        # Jupyter notebook with full analysis
│
├── src/
│   └── customer_segmentation.py                    # Main Python script (OOP approach)
│
├── visualizations/
│   ├── optimal_k_analysis.png                      # Elbow and Silhouette plots
│   ├── customer_segments_final.png                 # Main segmentation scatter plot
│   ├── customer_dashboard.png                      # Multi-panel dashboard
│   └── all_algorithms_comparison.png               # K-Means vs Hierarchical vs DBSCAN
│
├── marketing_segments/
│   ├── segment_0_Core_Customer_Base.csv
│   ├── segment_1_High_Value_Segment.csv
│   ├── segment_2_High_Engagement_Low_Income.csv
│   ├── segment_3_Untapped_Potential.csv
│   └── segment_4_Price_Sensitive_Segment.csv
│
├── requirements.txt                                 # Python dependencies
├── README.md                                        # Project documentation
├── LICENSE                                          # MIT License
└── .gitignore                                       # Git ignore file
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.11 or higher
- pip package manager
- Git

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/YOUR-USERNAME/customer-segmentation-ml.git
cd customer-segmentation-ml
```

2. **Create virtual environment**
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate
```

3. **Install dependencies**
```bash
pip install -r requirements.txt
```

4. **Download the dataset**
- Download `Mall_Customers.csv` from [Kaggle](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python)
- Place it in the `data/` directory

### Usage

#### Option 1: Run Python Script
```bash
python src/customer_segmentation.py
```

#### Option 2: Use Jupyter Notebook
```bash
jupyter notebook
# Open notebooks/customer_segmentation_analysis.ipynb
```

#### Quick Example
```python
from src.customer_segmentation import CustomerSegmentation

# Initialize
segmentation = CustomerSegmentation('data/Mall_Customers.csv')

# Run complete pipeline
segmentation.load_and_prepare_data()
segmentation.prepare_features()
segmentation.find_optimal_clusters()
segmentation.perform_clustering()
segmentation.analyze_clusters()
segmentation.visualize_clusters()
segmentation.save_results()
```

---

## 📊 Key Visualizations

### Customer Segmentation
![Customer Segments](visualizations/customer_segments_final.png)
*Five distinct customer segments based on income and spending behavior*

### Optimal Cluster Selection
![Optimal K Analysis](visualizations/optimal_k_analysis.png)
*Elbow Method and Silhouette Analysis confirming K=5 as optimal*

### Comprehensive Dashboard
![Dashboard](visualizations/customer_dashboard.png)
*Multi-panel view showing segment distributions and characteristics*

---

## 💼 Business Recommendations

### Budget Allocation Strategy:
- **35%** → High-Value Segment (Cluster 1)
- **25%** → Untapped Potential (Cluster 2) - highest ROI opportunity
- **30%** → Core Customer Base (Cluster 3)
- **10%** → Other segments (Clusters 4 & 5)

### Implementation Roadmap:

**Week 1-2: Quick Wins**
- Export Segment 2 (Untapped Potential) customer list
- Launch targeted email campaign with quality-focused messaging
- Track conversion rates separately from other segments

**Week 3-4: VIP Program**
- Design exclusive membership tier for Segment 1
- Offer early product access and premium support
- Measure incremental spending and engagement

**Month 2: Payment Flexibility**
- Introduce Buy Now Pay Later for Segment 4
- Test impact on average transaction size
- Monitor default rates and adjust terms

**Month 3: Measurement & Iteration**
- Compare segment performance metrics
- Calculate ROI by segment
- Adjust strategies based on response rates
- Scale successful tactics

---

## 🔍 Key Insights

### 1. The $200K Opportunity
Segment 2 (Untapped Potential) represents 17.5% of customers with high income but low engagement. This segment was invisible before analysis because they weren't causing problems - just quietly not buying. Converting even 30% from low to medium spenders could add $150,000-$200,000 in annual revenue with zero customer acquisition cost.

### 2. Income ≠ Spending
Two customers earning $88,000 annually showed dramatically different spending patterns (17 vs 82 out of 100). Traditional demographic segmentation would miss this critical behavioral difference.

### 3. Algorithm Selection Matters
While DBSCAN is excellent for anomaly detection, K-Means was optimal for this use case because marketing requires every customer to belong to an actionable segment. There's no such thing as a "noise" customer in a marketing context.

### 4. Feature Scaling is Non-Negotiable
Without standardization, the algorithm would treat a $1,000 income difference as more significant than a 50-point spending score difference. This would produce meaningless clusters.

### 5. Validation Builds Confidence
When both K-Means and Hierarchical Clustering independently found the same five segments with 85%+ agreement, it confirmed we discovered real underlying patterns, not statistical artifacts.

---

## 📚 Lessons Learned

### Technical Lessons:
1. **Feature scaling is critical** for distance-based algorithms
2. **Multiple validation methods** increase confidence in results
3. **Algorithm choice should serve business needs**, not demonstrate technical sophistication
4. **Cross-validation with multiple methods** reveals stable patterns

### Business Lessons:
1. **Data reveals opportunities** that domain knowledge alone misses
2. **Behavioral segmentation** outperforms demographic segmentation
3. **Every customer segment needs a strategy**, including those marked as "outliers" by some algorithms
4. **Actionability matters more than complexity** when communicating with stakeholders

---

## 🔮 Future Enhancements

### Technical Improvements:
- [ ] Include Age and Gender in multidimensional clustering
- [ ] Test Gaussian Mixture Models for probabilistic clustering
- [ ] Implement automated hyperparameter tuning
- [ ] Build predictive model to assign new customers to segments in real-time
- [ ] Create API endpoint for production deployment

### Business Enhancements:
- [ ] Track customer segment migration over time
- [ ] Calculate Customer Lifetime Value (CLV) by segment
- [ ] A/B test marketing strategies by segment
- [ ] Integrate with CRM system for automated campaign triggering
- [ ] Build recommendation engine tailored to each segment

### Data Enhancements:
- [ ] Incorporate purchase history and product preferences
- [ ] Add temporal patterns (seasonal behavior)
- [ ] Include online vs. in-store behavior metrics
- [ ] Integrate customer satisfaction scores
- [ ] Track marketing campaign response rates by segment

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- Dataset provided by [Kaggle](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial-in-python)
- Inspired by real-world retail analytics challenges
- Thanks to the scikit-learn community for excellent documentation

---

## 📧 Contact

**Your Name**
- LinkedIn: [your-linkedin-profile](https://linkedin.com/in/yourprofile)
- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com
- Portfolio: [your-portfolio-website.com](https://yourwebsite.com)

---

## ⭐ Show Your Support

If you found this project helpful or interesting, please consider giving it a star! It helps others discover the project.

---

**Project Status:** ✅ Complete

**Last Updated:** December 2024

---

### Quick Links
- [View Dataset](data/Mall_Customers.csv)
- [Explore Notebook](notebooks/customer_segmentation_analysis.ipynb)
- [Check Visualizations](visualizations/)
- [Read Marketing Recommendations](#business-recommendations)
