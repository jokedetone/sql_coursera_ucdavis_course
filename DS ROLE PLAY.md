Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

This is a 2-part assignment. In the first part, you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.

In the second part of the assignment, you are asked to come up with your own inferences and analysis of the data for a particular research question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions you are being asked, and your job will be to transfer your answers and SQL coding where indicated into this worksheet so that your peers can review your work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going to use Word or some other page layout application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact for you reviewer.



Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:

SELECT COUNT(*)
FROM Attribute
	
i. Attribute table = 10000 

SELECT COUNT(*)
FROM Business
ii. Business table = 10000 

SELECT COUNT(*)
FROM Category

iii. Category table = 10000 

SELECT COUNT(*)
FROM Checkin

iv. Checkin table = 10000 

SELECT COUNT(*)
FROM elite_years

v. elite_years table = 10000

SELECT COUNT(*)
FROM friend

vi. friend table =  10000

SELECT COUNT(*)
FROM hours

vii. hours table = 10000

SELECT COUNT(*)
FROM photo

viii. photo table = 10000 

SELECT COUNT(*)
FROM review

ix. review table =  10000

SELECT COUNT(*)
FROM tip

x. tip table = 10000 

SELECT COUNT(*)
FROM user

xi. user table = 10000 
	


2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

SELECT COUNT(DISTINCT id) 
from Business

i. Business = 10000 

SELECT COUNT(DISTINCT business_id)
from hours


ii. Hours = 1562  

SELECT COUNT(DISTINCT business_id)
from category

iii. Category = 2643  

SELECT COUNT(DISTINCT business_id)
from Attribute

iv. Attribute =1115  

SELECT COUNT(DISTINCT id) --Used the PK
from review
v. Review = 10000

SELECT COUNT(DISTINCT business_id)
from Checkin

vi. Checkin = 493

SELECT COUNT(DISTINCT business_id)
from Photo

vii. Photo = 6493

SELECT COUNT(DISTINCT business_id) 
from Tip

viii. Tip = 3979 

SELECT COUNT(DISTINCT business_id) 
from User

ix. User = 10000 

SELECT COUNT(DISTINCT user_id) 
from Friend

x. Friend = 11 

SELECT COUNT(DISTINCT user_id) 
from Elite_years

xi. Elite_years = 2780 

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	



3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer: no
	
	
	SQL code used to arrive at answer:
    -- What it does is sum every record in the column. If it is >=, then it means that the column has at least one NULL value.
    
    select sum(
        case
            when ID is null then 1
            else 0
        end
    ) as id_null,
    sum(
        case
            when name is null then 1
            else 0
        end
    ) as name_null,
    sum(
        case
            when yelping_since is null then 1
            else 0
        end
    ) as yelping_since_null,
    sum(
        case
            when useful is null then 1
            else 0
        end
    ) as useful_null,
    sum(
        case
            when funny is null then 1
            else 0
        end
    ) as funny_null,
    sum(
        case
            when cool is null then 1
            else 0
        end
    ) as cool_null,
    sum(
        case
            when fans is null then 1
            else 0
        end
    ) as fans_null,
    sum(
        case
            when average_stars is null then 1
            else 0
        end
    ) as average_stars_null,
    sum(
        case
            when compliment_hot is null then 1
            else 0
        end
    ) as compliment_hot_null,
    sum(
        case
            when compliment_hot is null then 1
            else 0
        end
    ) as compliment_hot_null,
    sum(
        case
            when compliment_more is null then 1
            else 0
        end
    ) as compliment_more_null,
    sum(
        case
            when compliment_profile is null then 1
            else 0
        end
    ) as compliment_profile_null,
    sum(
        case
            when compliment_cute is null then 1
            else 0
        end
    ) as compliment_cute_null,
    sum(
        case
            when compliment_list is null then 1
            else 0
        end
    ) as compliment_list_null,
    sum(
        case
            when compliment_note is null then 1
            else 0
        end
    ) as compliment_note_null,
    sum(
        case
            when compliment_plain is null then 1
            else 0
        end
    ) as compliment_plain_null,
    sum(
        case
            when compliment_cool is null then 1
            else 0
        end
    ) as compliment_cool_null,
    sum(
        case
            when compliment_funny is null then 1
            else 0
        end
    ) as compliment_funny_null,
    sum(
        case
            when compliment_writer is null then 1
            else 0
        end
    ) as compliment_writer_null,
    sum(
        case
            when compliment_photos is null then 1
            else 0
        end
    ) as compliment_photos_null
from user
	
	

	
4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

	i. Table: Review, Column: Stars

    select min(stars), max(stars), avg(stars)
    from review
	
		min: 1		max:	5	avg: 3.7082 
		
	
	ii. Table: Business, Column: Stars
	
    select min(stars), max(stars), avg(stars)
    from business
    
		min: 1.0		max: 5.0		avg: 3.6549 
		
	select min(likes), max(likes), avg(likes)
    from tip

	iii. Table: Tip, Column: Likes
	
		min:	0	max: 2		avg: 0.0144 
		
	select min(Count), max(Count), avg(Count)
    from Checkin

	iv. Table: Checkin, Column: Count
	
		min:	1	max: 53		avg: 1.9414 
		
	
	v. Table: User, Column: Review_count
	
		min: 0  	max: 2000  		avg: 24.2995 
		


5. List the cities with the most reviews in descending order:

	SQL code used to arrive at answer:
	
    SELECT city,
    sum(review_count) as cantidad
    FROM business as b
    group by city
    order by cantidad desc
	
	Copy and Paste the Result Below:
        +-----------------+----------+
        | city            | cantidad |
        +-----------------+----------+
        | Las Vegas       |    82854 |
        | Phoenix         |    34503 |
        | Toronto         |    24113 |
        | Scottsdale      |    20614 |
        | Charlotte       |    12523 |
        | Henderson       |    10871 |
        | Tempe           |    10504 |
        | Pittsburgh      |     9798 |
        | Montréal        |     9448 |
        | Chandler        |     8112 |
        | Mesa            |     6875 |
        | Gilbert         |     6380 |
        | Cleveland       |     5593 |
        | Madison         |     5265 |
        | Glendale        |     4406 |
        | Mississauga     |     3814 |
        | Edinburgh       |     2792 |
        | Peoria          |     2624 |
        | North Las Vegas |     2438 |
        | Markham         |     2352 |
        | Champaign       |     2029 |
        | Stuttgart       |     1849 |
        | Surprise        |     1520 |
        | Lakewood        |     1465 |
        | Goodyear        |     1155 |
        +-----------------+----------+
        (Output limit exceeded, 25 of 362 total rows shown)

	
6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

select stars,count(DISTINCT id)
from business
where city='Avon'
group by stars

Copy and Paste the Resulting Table Below (2 columns â€“ star rating and count):
+-------+--------------------+
| stars | count(DISTINCT id) |
+-------+--------------------+
|   1.5 |                  1 |
|   2.5 |                  2 |
|   3.5 |                  3 |
|   4.0 |                  2 |
|   4.5 |                  1 |
|   5.0 |                  1 |
+-------+--------------------+

ii. Beachwood

SQL code used to arrive at answer:


Copy and Paste the Resulting Table Below (2 columns â€“ star rating and count):
		


7. Find the top 3 users based on their total number of reviews:
		
	SQL code used to arrive at answer:
	
		
	Copy and Paste the Result Below:
		


8. Does posing more reviews correlate with more fans?

	Please explain your findings and interpretation of the results:
	

	
9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer:

	
	SQL code used to arrive at answer:

	
	
10. Find the top 10 users with the most fans:

	SQL code used to arrive at answer:
	
	
	Copy and Paste the Result Below:

	
		

Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.
	
i. Do the two groups you chose to analyze have a different distribution of hours?


ii. Do the two groups you chose to analyze have a different number of reviews?
         
         
iii. Are you able to infer anything from the location data provided between these two groups? Explain.

SQL code used for analysis:

		
		
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:
         
         
ii. Difference 2:
         
         
         
SQL code used for analysis:

	
	
3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:
         
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
                           
                  
iii. Output of your finished dataset:
         
         
iv. Provide the SQL code you used to create your final dataset: