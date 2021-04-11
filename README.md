# Sephora_Review_Analysis
Team members: Person 1 (diludl), Person 2 (***uniqname***)

### 1. Summarize your proposed project in a few sentences.
What is your proposed project and why are you proposing it? 
- Top beauty products that can bring customer happiness during COVID-19
- Analyzing Sephora reivews and Google search trends to find top beauty products that can bring people happiness during COVID-19. The proxies of happiness are high rating in customer reviews with key words related to happiness and high increase in search trends during COVID-19.
- 
What are the question(s) you want to answer, or goal you want to achieve? 

### 2.Describe your primary dataset. How was it collected and how will you access it? Please share what features in the dataset are relevant to your topic. At a minimum, include the following information:
- Short description (i.e., 1-3 sentences) of its key features
  - There are three types of datasets:
     1. Sephora products datasets(pre-pandamic(before April 2020), Pandamic (April 2020 - April 2021). The dataset will include product information (name, category, size, price), customer reivew, likes
     2. Sehpora products review datasets (accessed in April 2021). The dataset will include rating, review details, customer profile
     3. Google trend datasets (access in April 2021). The dataset will include the google search trend for product category and selected product.
- Estimated size (in records and/or bytes)
   - Sephora products datasets: two files, each file contains about 9000 records * 22 columns
   - Sehpora products review datasets : 190k records * 90 columns
   - Google trend datasets: 
     1. product category: 260 records * 143 columns
     2. selected product: tbd
- Location (give the URL or other access method)
   - Sephora products datasets:
     1. pre-pandamic(before April 2020): Kaggle [link](https://www.kaggle.com/raghadalharbi/all-products-available-on-sephora-website)
     2. Pandamic (April 2020 - April 2021): GitHub [link](https://github.com/einslulu/Sephora_Review_Analysis/tree/main/data)
   - Sehpora products review datasets: GitHub [link](https://github.com/einslulu/Sephora_Review_Analysis/tree/main/data)
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
