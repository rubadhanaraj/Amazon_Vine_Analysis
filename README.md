# Amazon_Vine_Analysis
## Overview of the analysis
The purpose is to analyse Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Using PySpark, Pandas, or SQL we need to determine if there is any bias toward favorable reviews from Vine members in the dataset. The other objectives of this Big Data analysis  were to
* Define big data and describe the challenges associated with it.
* Define Hadoop and name the main elements of its ecosystem.
* Explain how MapReduce processes data.
* Define Spark and explain how it processes data.
* Describe how NLP collects and analyzes text data.
* Explain how to use AWS Simple Storage Service (S3) and relational databases for basic cloud storage.
* Complete an analysis of an Amazon customer review.
The softwares used for this analysis are PySpark which was used to extract the dataset, transform the data, connect to AWS RDS instance and load the transformed data into pgAdmin. Google Colaboratory was used to import PySpark libraries and connect to Postgres to create SQL tables.

## Results
Using PySpark, Pandas, or SQL, it has been determined if there is any bias towards reviews that were written as part of the Vine program and determine whether having a paid Vine review makes a difference in the percentage of 5-star reviews.
1. The data from 'https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Electronics_v1_00.tsv.gz' was extracted and transformed into a dataframe using Pyspark. The transformed data was cleaned and filtered. A new DataFrame was created to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful.

![Total_votes](https://user-images.githubusercontent.com/108298416/196324151-c184c7d2-709f-464a-931a-84b0e03681b3.PNG)

2. The dataframe which was created in Step 1 was filtered and a new dataframe was created to retrieve all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%.

![votes_percentage](https://user-images.githubusercontent.com/108298416/196324449-58d9ce5d-5c63-4727-b09b-b97f5bb81cbc.PNG)

3. The dataframe which was created in Step 2 was filtered and a new dataframe was created to retrieve all the rows where a review was written as part of the Vine program (paid), vine == 'Y'.

![paid_reviews](https://user-images.githubusercontent.com/108298416/196324576-84b6ac64-9c30-4aa4-bc40-d47fa69244c9.PNG)

4. The dataframe which was created in Step 2 was filtered and a new dataframe was created to retrieve all the rows where a review was written as part of the Vine program (paid), vine == 'N'.

![unpaid_reviews](https://user-images.githubusercontent.com/108298416/196324636-728243b4-854d-417d-8cd1-aa6bdbd50a2d.PNG)

5. The total number of reviews, the number of 5-star reviews, and the percentage of 5-star reviews for the two types of review (paid vs unpaid) were determined using Pyspark functions.

![Total_reviews](https://user-images.githubusercontent.com/108298416/196324761-7ad8a9d8-af69-49b4-a08d-941e28cfcda6.PNG)

*  The number of vine reviews are 1,080 and non-vine reviews are 49659.
*  There were 454 5-star ratings out of 1080 vine reviews and 23034 5_star ratings out of 49659 reviews
*  42% of Vine reviews were 5 stars and 46% of non-Vine reviews were 5 stars

## Summary
* We results of this analysis shows that the vine members were not biased while reviewing the products considering the percentage of 5-star reviews of both the vine and non-vine members. 
* However, we can't conclude it this way because the reviews would depend on the particular product. We need to consider the product and analyse the reviews from vine members and non-vine members to actually understand whether there is a bias from vine members. This additional analysis can be done by adding the product_id and product_title columns to the dataframe, to understand which product has got more reviews and whether the reviews are biased or not. 



