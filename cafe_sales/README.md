# Cafe Sales Data Cleaning & EDA Project 📊☕

A comprehensive data cleaning and exploratory data analysis project using a synthetic cafe sales dataset with 10,000 transactions from 2023.

**Authors:** Kaung Khant Lin, Pyae Sone Aung  
**Date:** December 14, 2025

---

## 🎯 Project Overview

This project demonstrates end-to-end data cleaning techniques on a deliberately "dirty" dataset containing real-world data quality issues like missing values, error codes, and inconsistent formats. The goal was to restore as much usable data as possible and derive actionable business insights.

### Key Results
- **Data Recovery Rate:** 99.7% (9,974 out of 10,000 records)
- **Total Revenue:** $89,042 in 2023
- **Average Order Value:** $8.93
- **Business Model:** 70% Takeaway orders
- **Payment Preference:** 55% Digital Wallets

---

## 📊 Interactive Dashboard

<div class='tableauPlaceholder' id='viz1765705791594' style='position: relative'><noscript><a href='#'><img alt='Cafe Sales Summary 2023 ' src='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Ca&#47;CafeSalesSummary2023&#47;CafeSalesSummary2023&#47;1_rss.png' style='border: none' /></a></noscript><object class='tableauViz'  style='display:none;'><param name='host_url' value='https%3A%2F%2Fpublic.tableau.com%2F' /> <param name='embed_code_version' value='3' /> <param name='site_root' value='' /><param name='name' value='CafeSalesSummary2023&#47;CafeSalesSummary2023' /><param name='tabs' value='no' /><param name='toolbar' value='yes' /><param name='static_image' value='https:&#47;&#47;public.tableau.com&#47;static&#47;images&#47;Ca&#47;CafeSalesSummary2023&#47;CafeSalesSummary2023&#47;1.png' /> <param name='animate_transition' value='yes' /><param name='display_static_image' value='yes' /><param name='display_spinner' value='yes' /><param name='display_overlay' value='yes' /><param name='display_count' value='yes' /><param name='language' value='en-US' /></object></div>
<script type='text/javascript'>
    var divElement = document.getElementById('viz1765705791594');
    var vizElement = divElement.getElementsByTagName('object')[0];
    if ( divElement.offsetWidth > 800 ) { vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} 
    else if ( divElement.offsetWidth > 500 ) { vizElement.style.width='100%';vizElement.style.height=(divElement.offsetWidth*0.75)+'px';} 
    else { vizElement.style.width='100%';vizElement.style.height='2277px';}
    var scriptElement = document.createElement('script');
    scriptElement.src = 'https://public.tableau.com/javascripts/api/viz_v1.js';
    vizElement.parentNode.insertBefore(scriptElement, vizElement);
</script>

**[View Dashboard on Tableau Public →](https://public.tableau.com/views/CafeSalesSummary2023/CafeSalesSummary2023)**

---

## 🛠️ Tools & Technologies

- **Python**: Pandas, NumPy for data manipulation
- **Jupyter Notebook**: Interactive data cleaning and analysis
- **Tableau Public**: Dashboard creation and visualization
- **Dataset Source**: [Kaggle - Dirty Cafe Sales Dataset](https://www.kaggle.com/) by Ahmed Mohamed (CC BY-SA 4.0)

---

## 🧹 Data Cleaning Process

### Initial Data Issues
The dirty dataset contained severe quality problems:
- Missing values across all columns
- "UNKNOWN" and "ERROR" placeholder strings
- Inconsistent data types
- Invalid date formats

| Column | Missing Values |
|--------|----------------|
| `item` | 969 |
| `quantity` | 138 |
| `price_per_unit` | 179 |
| `total_spent` | 173 |
| `payment_method` | 3,178 |
| `location` | 3,961 |
| `transaction_date` | 460 |

### Cleaning Steps

1. **Type Conversion**
   - Converted numeric columns to proper data types
   - Coerced errors to NaN

2. **Error String Replacement**
   - Replaced "UNKNOWN" and "ERROR" with NaN for consistent handling

3. **Logical Imputation (Financial Data)**
   - Used the relationship: `total_spent = quantity × price_per_unit`
   - Calculated missing values when two out of three were present

4. **Menu-Based Imputation**
   - Created a menu price dictionary:
     ```python
     menu_prices = {
         'Coffee': 2.0, 'Tea': 1.5, 'Sandwich': 4.0,
         'Salad': 5.0, 'Cake': 3.0, 'Cookie': 1.0,
         'Smoothie': 4.0, 'Juice': 3.0
     }
     ```
   - Filled missing items by mapping from known prices
   - Filled missing prices by mapping from known items

5. **Date Handling**
   - Converted to datetime format
   - Used forward-fill and backward-fill for missing dates

6. **Categorical Imputation**
   - Filled missing payment methods with mode (most common value)
   - Filled missing locations with mode

7. **Data Removal**
   - Dropped 26 rows where both `quantity` and `total_spent` were missing (unrecoverable)

### Final Result
✅ **9,974 clean records** ready for analysis

---

## 📈 Key Findings

### Revenue & Sales
- Total revenue of **$89,042** across 9,974 transactions
- Average order value: **$8.93**
- Consistent sales throughout 2023 with minimal seasonal variation

### Top Sellers (by Revenue)
1. **Salad** - $19,903 (Highest revenue generator)
2. **Smoothie** - $15,936
3. **Sandwich** - $15,928

### Customer Behavior
- **Takeaway dominates**: 70% of all orders
- **Digital Wallet preferred**: 55% of transactions
- **Low cash usage**: Indicates tech-savvy customer base

### Location Performance
- In-store and Takeaway channels perform similarly
- Slight preference for Takeaway across most categories

---

## 💡 Business Recommendations

1. **Fix POS System**: High frequency of "UNKNOWN" and "ERROR" values suggests data capture issues at the source. Conduct an IT audit.

2. **Optimize Inventory**: Prioritize fresh ingredients for Salads and Smoothies (top sellers). Prevent stockouts to maximize revenue.

3. **Leverage Takeaway Trend**: Invest in packaging quality and order efficiency. Consider takeaway-exclusive promotions.

4. **Promote Digital Payments**: Offer Digital Wallet exclusive deals to speed up service and reward tech-savvy customers.

5. **Upselling Opportunities**: Bundle low-revenue items (Cookies, Tea) with high-value items (Salads, Smoothies).

---

## 📁 Project Structure

```
data-cleaning-eda-portfolio/
├── README.md
├── requirements.txt
└── cafe_sales/
    ├── dirty_cafe_sales.csv          # Original dataset
    ├── clean_cafe_sales.csv          # Cleaned dataset
    ├── Kino/
    │   ├── clean_eda.ipynb           # Data cleaning notebook
    │   └── dirty_cafe_sales.csv
    └── Dot's work/
        ├── dataCleaning.ipynb
        └── dirty_cafe_sales.csv
```

---

## 🚀 How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/data-cleaning-eda-portfolio.git
   cd data-cleaning-eda-portfolio
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the notebook**
   ```bash
   jupyter notebook cafe_sales/Kino/clean_eda.ipynb
   ```

---

## 📜 License & Credits

- **Dataset**: Created by [Ahmed Mohamed](https://www.kaggle.com/) on Kaggle
- **License**: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- **Analysis**: Kaung Khant Lin, Pyae Sone Aung

---

## 🤝 Connect

If you have questions or feedback about this project, feel free to reach out!
  
**LinkedIn:** [Kaung Khant Lin](https://www.linkedin.com/in/kaung-khant-lin-kino/), [Pyae Sone Aung](https://www.linkedin.com/in/pyae-sone-aung-096291313/)  
**Email:** kaungkhantlin999@gmail.com

---

## 📚 Resources

- **Pandas Cheat Sheet**: https://pandas.pydata.org/Pandas_Cheat_Sheet.pdf

---

*This project showcases practical data cleaning techniques and business intelligence analysis skills applicable to real-world scenarios.*