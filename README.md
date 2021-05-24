<!-- Output copied to clipboard! -->




**Sephora Review Analysis**

**Project for Milestone 1, SIADS 591&592**

**Motivation**

Since COVID-19 hit the world, the past year has changed consumers’ everyday routine and home experiences that ultimately impacted the way consumers interact with the beauty industry. According to COVID-19 Trends tracked by Spate NYC, Americans have been adapting to the new lifestyle as well as shifting their consumer behavior and demand. Some shifts are temporary, but some come with a lasting impact on consumers’ daily routine and mentality, which will change the way they engaged with different beauty categories. While it still takes time to go back to normal in the US, Spate mentioned that consumers are adapted to new routines at home, indicating shifts among the main categories that could bring happiness at home during the epidemic.

Sephora, the leader in prestige beauty Omni-retail with a roughly 80% of US market share, operates 2,021 stores in 35 countries worldwide, with an expanding base of over 500 stores across the Americas. Owned by LVMH, the world’s leading luxury goods group, Sephora US reached approximately 1.3 billion dollars of sales volume in 2020. According to the latest financial report, Sephora occupies 97% (2021 out of 2072) stores under the segment of selective retailing and expanded 64 branches globally in 2020. However, because the traffic in stores can easily create a health crisis, Sephora closed more than 90% of stores worldwide for almost two months and responded to the unprecedented success of online sales. Even though stores were gradually reopened from May to the end of June with special attention, the whole segment of selective retailing still went down more than 30%. This demonstrated the resilience of omnichannel strategy during the global health crisis and the substantial negative impact of the epidemic on the beauty industry.

Our proposed project is motivated by our interest in the beauty industry to identify the category and product level trends that have gained traction both post-pandemic and during the pandemic. The main category level contains Fragrance, Skincare, Makeup, Hair, Value & Gifts sets, Tools & Brushes, Bath & Body, Men, Wellness and Nail. To select the top 3 products on the selected main categories, we developed a model using seven indicators to measure what kind of products can bring customers joy during the COVID-19. In this project, we want to answer the following questions on three levels: general level, category level, and specific product level.

1）General: Is there any correlation among price, love, product life, number of reviews, and rating? What are the correlations among price, love, product life, number of reviews, and rating for each main category

2）Category level: Which main category was heavily impacted by the epidemic? Which main category has experienced the highest review changes during the epidemic? 

3）Product level: What kind of products in the top selected categories bring customers happiness during COVID-19?

**Data source: **

We have two data sources:



*   Data source 1 is the _web scraped data_ from the Sephora website (CSV file). It contains the product information (e.g., product name, brand, category, love, price, review count and rating, URL). We also use the URL to get **Product_id**, which is the input for Data Source 2. 






![alt_text](images/image1.png "image_tooltip")


_ Important variables in  data source 2_



*   Data source 2 is the _Bazaarvoice API download_ (JSON file). It contains two levels of information. 
    *   Product level: product name, product id, ratings, reviews, rating distribution, first review submission time. 
    *   Review level: product id, review id, review text, review submission time, user info (e.g., hair color, skin tone, age)






![alt_text](images/image2.png "image_tooltip")


_ Important variables in  data source 2_

We created **_webscrape_sephora_review_data.ipynb_** to scrape data. To test the script, we first took some sample data to estimate the time of scraping. 



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



<table>
  <tr>
   <td>Source: <a href="https://www.sephora.com/">https://www.sephora.com/</a>
<p>
Step1: in total, 335 brands
<ul>

<li>Sample data Location: <a href="https://drive.google.com/drive/folders/1tPsgCU_EbbNfa4PgAxTeojDzERDfjrH9?usp=sharing">google drive link</a> 

<p>
Step2 &3: 
<ul>

<li>Sample test of one brand: acqua-di-parma. 

<li>There are 12 products for the brand. 

<li>Time spent to get Product URL: 20min 

<li>Scrap time per product: 1.67 min. 

<li>Estimated time for all products (10,000): approx. 278 hours  
</li>
</ul>
</li>
</ul>
   </td>
   <td>Source: Bazaarvoice API (<a href="https://api.bazaarvoice.com/data/reviews.json?Filter=contentlocale%3Aen*&Filter=ProductId%3AP470507&Sort=SubmissionTime%3Adesc&Limit=6&Offset=0&Include=Products%2CComments&Stats=Reviews&passkey=caQ0pQXZTqFVYA1yYnnJ9emgUiW59DXA85Kxry8Ma02HE&apiversion=5.4&Locale=en_US">example</a>) 
<p>
Step 4: 
<ul>

<li>Sample test of scraping reviews of the first ten products

<li>Time spent: 20 seconds for 361 reviews 

<li>Time spent per review: 0.063 sec

<li>Estimated time for all reviews (2,586,652) of all products: approx. 40 hours
</li>
</ul>
   </td>
  </tr>
</table>


The estimated hours to scrape complete data is more than 300 hours, which is not realistic. Therefore, we decided to limit the scope. 

**Sephora Selected data used in the Project **(Data source 1 & 2)**- **time of scraping: **14 hours.**

**Data Source 1:**



*   Due to time limitations, we decided to utilize the dataset downloaded from Kaggle and limit the scope of the products in the analysis. It will save our time getting Data source 1 and give us the ratings and reviews snapshot for each product before **April 2020**. 

**Data Source 2:**



*   Based on Product Data from Kaggle, the median of review counts is 50. There are 12 products with reviews counts above 10,000. Due to the time limitations, in Data Source 2, we decided to download the latest **(April/May 2021**) up to 3,100 reviews for each product. In this case, we will still cover all reviews for 98% of the selected product in Data source 1. 
*   We also split the products into 13 batches to download.

With two data sources, we can compare the ratings and reviews before the Pandemic (April 2019 - March 2020) and during the Pandemic (April 2020 -April 2021) in the US. 



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")



<table>
  <tr>
   <td><strong>Product Data (Kaggle)-</strong>Data Source1
<ul>

<li>Location: <a href="https://drive.google.com/drive/u/2/folders/1Xw4U0PpjKCBi13XMWUDufactY0RJPrfA">google drive  link</a>

<li>Access: Download from Kaggle (<a href="https://www.kaggle.com/raghadalharbi/all-products-available-on-sephora-website">link</a>)

<li>Format: CSV

<li>Size & Records: 22.18 MB, 9169 records * 21 columns

<li>Size & Records used : 3960 records (rating >= 5 & review count >=50)

<li>Period Covered: Product information by April 2020
</li>
</ul>
   </td>
   <td><strong>Product & Review Data </strong>- Data Source 2
<ul>

<li>Location: <a href="https://drive.google.com/drive/u/2/folders/1Xw4U0PpjKCBi13XMWUDufactY0RJPrfA">google drive  link</a>

<li>Access:Bazaarvoice API (details see below)

<li>Format: JSON

<li>Size & Records:  6.42GB (13 files)

<li>Period Covered: Product information by April 2020; 

<li>Review information: latest 3100 reviews 
</li>
</ul>
   </td>
  </tr>
</table>


How to use Bazaarvoice API:** **We use python requests.get to download review data and we can also set different parameters to limit the scope (see below). 

 url = '[https://api.bazaarvoice.com/data/reviews.json](https://api.bazaarvoice.com/data/reviews.json)'; params = { 'Filter': f'ProductId:{p_id}',  'Sort': 'SubmissionTime:desc', 'Limit': 100,  'Offset': 0, 'Include': 'Products,Comments', 'Stats': 'Reviews', 'passkey': 'caQ0pQXZTqFVYA1yYnnJ9emgUiW59DXA85Kxry8Ma02HE','apiversion': 5.4,'Locale': 'en_US' }

r = requests.get(url, params=params, proxies={"http": proxy, "https": proxy}, timeout=15)

**Data Manipulation**

The packages we used in this section are documented in [requirements.txt](https://drive.google.com/drive/folders/1Bjil5EROv8y4I9qsrU5WSqMnCaMb8z64?usp=sharing). The data from two data sources seemed without significant NaN or other issues. We have six steps in Data Manipulation:






![alt_text](images/image5.png "image_tooltip")


**Step 1: Consolidate files and remove duplicates.**

There are in total 13 files downloaded from Bazaarvoice API. We created the below functions to get Product level data frame up to April 2021 and Review the level data frame:



*   _get_review_product_df( product_id,file_name )_: the function is to get Product level data for each product. Important variables include below:
    *   ProductId, name, brand, category, Total Reviews, AverageOverallRating
*   _get_review_level_df( product_id,file_name _): the function is to get Review level data for each product. Important variables include below:
    *    FirstSubmissionTime, Rating, ContextData: eye color, hair color, etc.
*   _extract_all_product(file_name_): the function is to extract all products and create two data frames: **Product level data frame up to April 2021 **(14,789 records) and **Review level data frame **(2,700,551 records).

SKU_id is one level of detail below Product_id. It means the same product may have different variants: package size, color, etc. However, the review and product information is the same for SKUs in a given product id. Thus, we need to remove duplicated lines. 

**Challenge: **In this step, we encountered the biggest **challenge **to manipulate data: the data is more than 6 GB, while my RAM is only 8 GB. To avoid system slowdown or crash, we first selected columns needed for analysis and deleted the loaded data from memory in each iteration when combining files.  After removing the duplicates, we saved the two data frames into two files: **all_products_no_dup.pk**l and **all_reviews_no_dup.pkl. **The two files are held [here](https://drive.google.com/drive/folders/1Bjil5EROv8y4I9qsrU5WSqMnCaMb8z64?usp=sharing). <span style="text-decoration:underline;">You can use these two files for the following data manipulation and analysis parts.  </span> Some variables have dictionaries as values. Therefore, we cannot save them as CSV or parquet files. To open the pickle files, you would need to have Python 3.8 as indicated in the requirement.txt.

**Step 2: Create data frame Product data 2020_2021**



*   Create below functions to combine product dataframe from two products related dataframes (Dataframe1 2020: Kaggle data snapshot at April 2020 and Dataframe2 2021: Webscrap data snapshot at April 2021 ): 
    *   _create_product_df_2020(df_product_list)_
    *   _create_product_df_2021(df_product, df_product_b42020_temp)_
    *   _combine_two_product_df(df_product_b42020_temp, df_product_af2020_temp)_
*   The dataframe contains following important variables:
    *   'Product_id','name','size','brand','category','love','price','value_price','URL'
    *   'Number_of_reviews_2020','rating_2020','number_of_reviews_2021','rating_2021'
*   Create new features to support later analysis：
    *   Re-map category: the categories from the data source are at the lowerest level, which is not suitable for our analysis. We have to create [category_map.csv](https://drive.google.com/drive/folders/1Bjil5EROv8y4I9qsrU5WSqMnCaMb8z64?usp=sharing) to re-map the product categories manually. We created function _create_category_level1_and_level2_map()_ to re-map the products into 10 categories. 
    *   Covert _review submission time_ to date format YYYY-MM-DD
    *   Create variable '_product_life'_: the years since first review submission. 1) we use the first _review submission time _as the proxy of product launched time on the website. 2) The product_life can help us tag whether a product has a life above one year or two years. It will also enable us to calculate the average review count per year.

**Step 3: Create reviews related data frames: **



*   To compare the review counts and ratings before and during the pandemic, we built below two functions to get data frame **Review Data during April 2019 -April 2020** and **Review Data during April 2020 -April 2021. **In the function, we selected the periods April 2019 -April 2020 and April 2020 -April 2021and groupby product id to calculate the review counts and average rating for both periods. 
    *   create_product_reviews_2021(df_reviews) and create_product_reviews_2020(df_reviews)
*   Validate the review data completeness: 
    *   There are 99% of products with a product life of more than one year. Due to the limit of scraping, the data frame **Review Data during April 2020 -April 2021** covers 97% of the products. The rest 3% we will fillna with (review count 2021 - review count 2020) and rating 2021 in Step 5. Like products with a product life of more than two years, 85% of products have a product life of more than two years. Our data frame **Review Data during April 2019 -April 2020 **covers 98% of their data. The rest will fillna with Review_count_up_to_2020_normalized and rating 2020 in Step 5. 

**Step 4: Merge three data frames created in Step 2 and 3**



*   We created function _merge_review_to_product(three data frames made in Steps 2 and 3)_ to merge data frames. The key is still the product_id. 

**Step 5: Create new features for analysis**






![alt_text](images/image6.png "image_tooltip")




*   We use function _create_new_features_on_merged_data(df) _to create above features for analysis. Below is the explanation for important variables (review counts and ratings related).  
    *   Ratings related: 'Rating_up_to_2020' and 'Rating_up_to_2021' give the snapshot of rating per product. 'Rating_period_2019-2020' and 'Rating_period_2020-2021' is the average of ratings for all reviews submitted during the periods. For missing values (only 2-3%), we use 'Rating_up_to_2020' and 'Rating_up_to_2021' to fill in.
    *   Review counts related: 'Review_count_up_to_2020_normalized' and 'Review_count_up_to_2021_normalized' are average of review counts per year in 2020 and 2021 separately. We **capped** all values above or equal to zero. We use them to fillna for the **missing values** (only 2-3%) in 'Review_count_period_2019-2020' and 'Review_count_period_2020-2021'. 
*   Lastly, we compared the review counts and ratings between April 2019 - April 2020 (before pandemic) and April 2020 - April 2021(during a pandemic) to help us see what products consumers value more during the pandemic.

**Step 6: Create a time series data frame from the Review Level data frame for visualization.**

In this step, we created the function_ prepare_df_review_time_series_for_charts_ to create a time series data frame for visualization. 



*   We groupby review submission date and category to calculate the review counts/ average rating per month per category in the function. 
*   To plot the time series chart, we put the date in the Index and Category in columns.

**Analysis and Visualization**

**1) General:**

**Is there any correlation among price, love, product life, number of reviews, and rating?**

These five variables that we selected, price, love, product life, number of reviews, and rating in 2021 from data frame ‘df_product_review_finall_all’, all have the potential to impact or reflect customers’ purchasing behaviors. By using seaborn module to create this correlation heatmap matrix, we have some critical findings for further data exploration. 

We discovered that the variable ‘love’, which represents the customers’ likeness and willingness to repurchase the product, has a positive relationship (0.73) with the number of reviews written by the buyers. This indicates that the more people like the products they buy, the higher possibility that they would leave a comment online after using products. We also found that product rating has little correlation with product price (0.07), product life (0.13), number of reviews (0.049), and love for the product (0.043). In other words, price or product life has little impact on customers’ decision on product rating.

**What are the correlations among price, love, product life, number of reviews, and rating for each main category?**

    By using the pairplot function under the module seaborn, we have some interesting findings. For instance, makeup and skincare occupy the largest portion of reviews counts since green (Makeup) and orange (Skincare) dots are located at higher positions compared to other categories that indicate makeup and skincare outperform other main categories in numbers. The fragrance is the most expensive category and has the highest ratings, while makeup and skincare are the least expensive, and the average rating is lower, approximately 4.2. 

**2)Category level:**

**Which main category was heavily impacted by the epidemic?**

We extracted all the review counts from 2016 to 2021 and broke them down into ten main categories. As we can see from the graph, makeup and skincare, which have more review counts than any other categories, went down sharply between 2020 and 2021, during COVID-19. In other words, makeup and skincare are heavily impacted by the epidemic. Meanwhile, the review counts of hair decrease to a level lower than a fragrance that rarely happened within five years.

       

Another interesting phenomenon we discovered that, besides the review counts of fragrance increased, the rating of fragrance products went above any other categories during the epidemic. This indicates that, due to the social distance policy, consumers tend to use fragrance to relieve the tensions brought by the virus and leave a higher rating.

**Which main category has experienced the highest variance during the epidemic? **

 Then we take a look at the matrix of review changes versus rating changes by using the review count and rating differences between 2020 and 2021. Each color spot on the four-quadrant represents a product under the main category. Those positions at the first quadrant that have increased in both review counts and ratings are products with good performance and resilience towards health crisis. Those positions at the  third quadrant that have decreased in both review counts and ratings are products with bad performance and volatile to the epidemic. As we can see on the four quadrants, more dots locate on the left side than on the right side, which demonstrates the fact that most beauty products experience a double downturn from both review and rating.

However, there are too many dots on the same graph that we cannot see the tendency of each main category, so we visualized the scatterplots of each main category as below:





![alt_text](images/image7.png "image_tooltip")


We define dots in the first quadrant as ‘good’(green), those in the second or fourth quadrant as usual (grey), and dots in the third quadrant as ‘bad’(red). Among all the main categories, makeup and skincare have more products than other types, meanwhile have more dots on the left side. Alternatively, the fragrance is the big winner since most dots position on the right side,which re-verified the hypothesis of the relief brought to consumers during the epidemic. Men and nails are the least favored product type. All the other categories (Hair, Bath & Body, Wellness, Tools & Brushes, Value & Gift sets) experience the downturn in both review counts and rating during COVID-19, except for the fragrance.

By exploring review texts in ‘df_reviews_2021’, we counted the reviews related to COVID-19 and happiness throughout the epidemic. We filtered review texts related to the virus with words like ‘covid, pandemic and virus’, while for joy we use keywords of ‘happy, joy, happiness and relax’. From the graphs, we see that the most reviews related to the virus (purple area) and happiness are under the skincare category. That is not only because skincare is the largest category in Sephora, but also because skincare is the most common type of beauty product used when staying at home. The fragrance also occupies a large portion of review texts related to happiness. This may explain why the rating increased during the epidemic.

**3)Product level:**

**What kind of products can bring customer happiness during COVID-19?**

In order to find out what specific products of the top 3 categories, which have the highest variance, can bring consumers happiness during the epidemic, we developed our model to measure ‘happiness‘ by using seven indicators. With a total score of 5, ‘love’ weighs 0.5 point, ‘review count up to 2021’ is allocated to 1 point, ‘2 year product review diff’ accounts for 1 point, ‘rating up to 2021’ for 1 point, ‘2 year product rating diff’ for 1, COVID-19 related words mentioned in the review ('#review_covid') for 0.25 points and happiness related words mentioned in the review ('#review_happy') for 0.25 points. Then we normalize different weights using MinMax scaler on all the indicators and sort values by happiness score weight and main category, to get the top 3 products in each category. 

**Conclusion**

**1)General:** review counts have a positive relationship with love, rating has little correlation with product life, love, product price, and the number of reviews. Makeup and skincare outperform other main categories in numbers.

**2)Category level: **makeup and skincare are heavily impacted by the virus and decreased both in review counts and rating, while fragrance has more review counts and higher rating during the epidemic. 

**3)Product level: **fragrance products bring consumers the most happiness during the epidemic. The top 3 products in the skincare, makeup and fragrance category explains the mentality and demand of consumers during the epidemic.

**Statement of Work**

We facilitated the areas that demonstrate our interests while discussing and collaborating on a daily basis. Di Lu led the coding part, including the data collection, manipulation and part of visualization. Jingzhi Chen took the lead on the topic idea, content, analysis and visuals. Both are responsible for the final report.
