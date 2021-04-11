# Sephora_Review_Analysis
Team members: Person 1 (diludl), Person 2 (***uniqname***)

### 1. Summarize your proposed project in a few sentences.
What is your proposed project and why are you proposing it? 
- Top beauty products that can bring customer happiness during COVID-19
- Analyzing Sephora reviews and Google search trends to find top beauty products that can bring people happiness during COVID-19. The proxies of happiness are high rating in customer reviews with key words related to happiness and high increase in search trends during COVID-19.

Why Sephora: 
Consumer behavior change: long time stay at home, less social work and outdoor activities,  more anxiety from news, environment and feeling of uncertainty. 



What are the question(s) you want to answer, or goal you want to achieve? 

### 2.Describe your primary dataset. How was it collected and how will you access it? Please share what features in the dataset are relevant to your topic. At a minimum, include the following information:
- Short description (i.e., 1-3 sentences) of its key features
  - There are three types of datasets:
     1. Sephora products datasets(pre-pandemic(before April 2020), Pandemic (April 2020 - April 2021). The dataset will include product information (name, category, size, price), customer review, likes
     2. Sephora products review datasets (accessed in April 2021). The dataset will include rating, review details, customer profile
     3. Google trend datasets (access in April 2021). The dataset will include the google search trend for product category and selected product.
- Estimated size (in records and/or bytes)
   - Sephora products datasets: two files, each file contains about 9000 records * 22 columns
   - Sephora products review datasets : 190k records * 90 columns
   - Google trend datasets: 
     1. product category: 260 records * 143 columns
     2. selected product: tbd
- Location (give the URL or other access method)
   - Sephora products datasets:
     1. pre-pandemic(before April 2020): Kaggle [link](https://www.kaggle.com/raghadalharbi/all-products-available-on-sephora-website)
     2. Pandemic (April 2020 - April 2021): GitHub [link](https://github.com/einslulu/Sephora_Review_Analysis/tree/main/data)
   - Sephora products review datasets: GitHub [link](https://github.com/einslulu/Sephora_Review_Analysis/tree/main/data)
   - Google trend datasets: GitHub [link](https://github.com/einslulu/Sephora_Review_Analysis/tree/main/data)
- Format (CSV, JSON, etc.)
   - parquet
   - CSV
   - JSON
- Access method (download, web scraping, API, etc.)
   - Kaggle download: Kaggle
   - web scraping: www.sephora.com
   - API:
      1. bazaarvoice
      2. google search trend 
### 3. Describe your secondary dataset. How was it collected and how will you access it? Please share what features in the dataset are relevant to your topic and describe the data types you’re expecting.  At a minimum, include the following information:
- Short description (i.e., 1-3 sentences) of its key features
  - Google trend datasets (access in April 2021). The dataset will include the google search trend for product category and selected product.
- Estimated size (in records and/or bytes)
   - Google trend datasets: 
     1. product category: 260 records * 143 columns
     2. selected product: tbd
- Location (give the URL or other access method)
   - Google trend datasets: GitHub [link](https://github.com/einslulu/Sephora_Review_Analysis/tree/main/data)
- Format (CSV, JSON, etc.)
   - parquet
- Access method (download, web scraping, API, etc.
   - API: google search trend 

### 4. [Yes] Please check this box to confirm that your primary and secondary datasets are accessible and available to your classmates and the instructional team. 

### 5. How will you join your primary and secondary datasets? What challenges, if any, do you anticipate?
- There are three datasets in primary datasets. They will join together with product ID 
- Primary and secondary dataset will join with product category name or product name 

### 6. Describe any analyses you plan to undertake. For each, please give the technique or approach and briefly explain what you expect to learn from it. 
- to understand what beauty products can bring happiness to consumer during pandemic by analyzing the top beauty products that have high rating and big interest increase during pandemic. We will focus on data transformation and EDA.
- to bring customize happiness for different customer profiles. We will focus on recommender system technique

### 7. Describe in 1-3 sentences at least one data visualization you plan to create. Include the chart type (e.g. bar chart, scatterplot, SPLOM, etc.) as well as the variables (features) you intend to plot. 
- top beauty product: 
  - bar chart 
  - Variables: product name, rating, like, review count, search trend 
- xxxx

### 8. Does your choice of data raise any ethical issues? If so, briefly describe the concern and how you plan to mitigate it. 
	- Potential bias: the analysis might only represent the people who like online shopping, tend to leave review and their profile information 

