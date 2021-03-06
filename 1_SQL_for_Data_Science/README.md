# 1. SQL for Data Science

As data collection has increased exponentially, so has the need for people skilled at using and interacting with data; to be able to think critically, and provide insights to make better decisions and optimize their businesses. This is a data scientist, “part mathematician, part computer scientist, and part trend spotter” (SAS Institute, Inc.). The skills necessary to be a good data scientist include being able to retrieve and work with data, and to do that you need to be well versed in SQL, the standard language for communicating with database systems.

This course is designed to give you a primer in the fundamentals of SQL and working with data so that you can begin analyzing it for data science purposes. You will begin to ask the right questions and come up with good answers to deliver valuable insights for your organization. This course starts with the basics and assumes you do not have any knowledge or skills in SQL. It will build on that foundation and gradually have you write both simple and complex queries to help you select data from tables. You'll start to work with different types of data like strings and numbers and discuss methods to filter and pare down your results. You will create new tables and be able to move data into them. You will learn common operators and how to combine the data. You will use case statements and concepts like data governance and profiling. You will discuss topics on data, and practice using real-world programming assignments. You will interpret the structure, meaning, and relationships in source data and use SQL as a professional to shape your data for targeted analysis purposes. 

### Entity Relationship Diagram
![Entity Relationship Diagram](https://github.com/zendegani/SQL/blob/main/1_SQL_for_Data_Science/YelpERDiagram.png?raw=true)

Data Scientist Role Play: Profiling and Analyzing the Yelp Dataset Coursera Worksheet

This is a 2-part assignment. In the first part, you are asked a series of questions that will help you profile and understand the data just like a data scientist would. For this first part of the assignment, you will be assessed both on the correctness of your findings, as well as the code you used to arrive at your answer. You will be graded on how easy your code is to read, so remember to use proper formatting and comments where necessary.

In the second part of the assignment, you are asked to come up with your own inferences and analysis of the data for a particular research question you want to answer. You will be required to prepare the dataset for the analysis you choose to do. As with the first part, you will be graded, in part, on how easy your code is to read, so use proper formatting and comments to illustrate and communicate your intent as required.

For both parts of this assignment, use this "worksheet." It provides all the questions you are being asked, and your job will be to transfer your answers and SQL coding where indicated into this worksheet so that your peers can review your work. You should be able to use any Text Editor (Windows Notepad, Apple TextEdit, Notepad ++, Sublime Text, etc.) to copy and paste your answers. If you are going to use Word or some other page layout application, just be careful to make sure your answers and code are lined appropriately.
In this case, you may want to save as a PDF to ensure your formatting remains intact for you reviewer.



Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:

			i.    Attribute table   = 10000
			ii.   Business table    = 10000
			iii.  Category table    = 10000
			iv.   Checkin table     = 10000
			v.    elite_years table = 10000
			vi.   friend table      = 10000
			vii.  hours table       = 10000
			viii. photo table       = 10000
			ix.   review table      = 10000
			x.    tip table         = 10000
			xi.   user table        = 10000

			/**********SQL Code*********/
			SELECT COUNT(*)
			FROM TABLE
			/***************************/

2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

			i.    Business    = 10000
			ii.   Hours       = business_id: 1562
			iii.  Category    = business_id: 2643
			iv.   Attribute   = business_id: 1115
			v.    Review      = 10000, business_id: 8090, user_id: 9581
			vi.   Checkin     = business_id: 493
			vii.  Photo       = 10000, business_id: 6493
			viii. Tip         = user_id: 537, business_id: 3979
			ix.   User        = 10000
			x.    Friend      = user_id: 11
			xi.   Elite_years = user_id: 2780

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.

			/**********SQL Code*********/
			SELECT COUNT(DISTINCT KEY)
			FROM TABLE
			/***************************/

3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer: No


	SQL code used to arrive at answer:
	
			/**********SQL Code*********/
			SELECT COUNT(*)
			FROM user
			WHERE id IS NULL
				OR name IS NULL
				OR review_count IS NULL
				OR yelping_since IS NULL
				OR useful IS NULL
				OR funny IS NULL
				OR cool IS NULL
				OR fans IS NULL
				OR average_stars IS NULL
				OR compliment_hot IS NULL
				OR compliment_more IS NULL
				OR compliment_profile IS NULL
				OR compliment_cute IS NULL
				OR compliment_list IS NULL
				OR compliment_note IS NULL
				OR compliment_plain IS NULL
				OR compliment_cool IS NULL
				OR compliment_funny IS NULL
				OR compliment_writer IS NULL
				OR compliment_photos IS NULL
			/***************************/


4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

	i. Table: Review, Column: Stars

		min:	1	max:	5	avg: 3.7082


	ii. Table: Business, Column: Stars

		min:	1.0	max:	5.0	avg: 3.6549


	iii. Table: Tip, Column: Likes

		min:	0	max:	2	avg: 0.0144


	iv. Table: Checkin, Column: Count

		min:	1	max:	53	avg: 1.9414


	v. Table: User, Column: Review_count

		min:	0	max:	2000	avg: 24.2995


				/**********SQL Code*********/
				SELECT MIN(COLUMN)
					,MAX(COLUMN)
					,AVG(COLUMN)
				FROM TABLE
				/***************************/


5. List the cities with the most reviews in descending order:

	SQL code used to arrive at answer:
	
				/**********SQL Code*********/
				SELECT city
					,SUM(review_count) AS N_review
				FROM business
				GROUP BY city
				ORDER BY N_review DESC
				/***************************/


	Copy and Paste the Result Below:

				+-----------------+----------+
				| city            | N_review |
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


6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

				/**********SQL Code*********/
				SELECT Stars As 'Star Rating'
					,Count(stars) AS Count
				FROM business
				WHERE city = 'Avon'
				GROUP BY Stars
				ORDER BY Stars
				/***************************/


Copy and Paste the Resulting Table Below (2 columns – star rating and count):

				+-------------+-------+
				| Star Rating | Count |
				+-------------+-------+
				|         1.5 |     1 |
				|         2.5 |     2 |
				|         3.5 |     3 |
				|         4.0 |     2 |
				|         4.5 |     1 |
				|         5.0 |     1 |
				+-------------+-------+

ii. Beachwood

SQL code used to arrive at answer:

				/**********SQL Code*********/
				SELECT Stars As 'Star Rating'
					,Count(stars) AS Count
				FROM business
				WHERE city = 'Beachwood'
				GROUP BY Stars
				ORDER BY Stars
				/***************************/


Copy and Paste the Resulting Table Below (2 columns – star rating and count):

				+-------------+-------+
				| Star Rating | Count |
				+-------------+-------+
				|         2.0 |     1 |
				|         2.5 |     1 |
				|         3.0 |     2 |
				|         3.5 |     2 |
				|         4.0 |     1 |
				|         4.5 |     2 |
				|         5.0 |     5 |
				+-------------+-------+


7. Find the top 3 users based on their total number of reviews:

	SQL code used to arrive at answer:
	
				/**********SQL Code*********/
				SELECT name
					,review_count
				FROM user
				ORDER BY review_count DESC LIMIT 3
				/***************************/


	Copy and Paste the Result Below:
	
				+--------+--------------+
				| name   | review_count |
				+--------+--------------+
				| Gerald |         2000 |
				| Sara   |         1629 |
				| Yuri   |         1339 |
				+--------+--------------+


8. Does posing more reviews correlate with more fans?

	Please explain your findings and interpretation of the results:

It is correlated but not strongly, e.g. in Q.7, we saw that Gerald has the top review_count, but in the table below, his number of fans ranks 4th.
The Ratio column shows the ratio of number of fans wrt the number of review.
As it shows different values, it implies that there are other factors that affect the number of fans.

				+-----------+--------------+------+-------+
				| name      | review_count | fans | Ratio |
				+-----------+--------------+------+-------+
				| Amy       |          609 |  503 |    82 |
				| Mimi      |          968 |  497 |    51 |
				| Harald    |         1153 |  311 |    26 |
				| Gerald    |         2000 |  253 |    12 |
				| Christine |          930 |  173 |    18 |
				+-----------+--------------+------+-------+


				/**********SQL Code*********/
				SELECT name
					,review_count
					,fans
					,fans * 100 / review_count AS Ratio
				FROM user
				ORDER BY fans DESC LIMIT 5
				/***************************/

9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer:
	The number of reviews with the word 'love' is higher than that of those with 'hate'.

				+------+------+
				| Love | Hate |
				+------+------+
				| 1780 |  232 |
				+------+------+

	SQL code used to arrive at answer:
	
				/**********SQL Code*********/
				SELECT COUNT(CASE
							WHEN TEXT LIKE '%love%'
								THEN 1
							END) AS Love
					,COUNT(CASE
							WHEN TEXT LIKE '%hate%'
								THEN 1
							END) AS Hate
				FROM review
				/***************************/



10. Find the top 10 users with the most fans:

	SQL code used to arrive at answer:
	
				/**********SQL Code*********/
				SELECT name
					,fans
				FROM user a
				ORDER BY fans DESC LIMIT 10
				/***************************/


	Copy and Paste the Result Below:

				+-----------+------+
				| name      | fans |
				+-----------+------+
				| Amy       |  503 |
				| Mimi      |  497 |
				| Harald    |  311 |
				| Gerald    |  253 |
				| Christine |  173 |
				| Lisa      |  159 |
				| Cat       |  133 |
				| William   |  126 |
				| Fran      |  124 |
				| Lissa     |  120 |
				+-----------+------+


Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.

				City:		Toronto
				Category:	Food

i. Do the two groups you chose to analyze have a different distribution of hours?
				Yes. The group with higher stars are only open in the afternoon, while the group with the lower stars are open almost the whole day.

				+--------------+-------+------------------------------------------------------------------------------+
				| name         | stars | Opening hours                                                                |
				+--------------+-------+------------------------------------------------------------------------------+
				| Cabin Fever  |   4.5 | 16:00-2:00,18:00-2:00,18:00-2:00,18:00-2:00,18:00-2:00,16:00-2:00,16:00-2:00 |
				| Halo Brewery |   4.0 | 15:00-21:00,15:00-21:00,15:00-21:00,15:00-21:00,11:00-21:00,11:00-21:00      |
				| Loblaws      |   2.5 | 8:00-22:00,8:00-22:00,8:00-22:00,8:00-22:00,8:00-22:00,8:00-22:00,8:00-22:00 |
				+--------------+-------+------------------------------------------------------------------------------+

ii. Do the two groups you chose to analyze have a different number of reviews?
				Yes. The higher the number of review, the higher the rating.

				+--------------+-------+----------+
				| name         | stars | N_review |
				+--------------+-------+----------+
				| Cabin Fever  |   4.5 |       26 |
				| Halo Brewery |   4.0 |       15 |
				| Loblaws      |   2.5 |       10 |
				+--------------+-------+----------+

iii. Are you able to infer anything from the location data provided between these two groups? Explain.
				Not really. Yet it seems the lower rating belongs to the business inside a shopping centre which doesn't apply to the higher ratings ones.'

				+--------------+-------+----------------------+-------------+
				| name         | stars | address              | postal_code |
				+--------------+-------+----------------------+-------------+
				| Cabin Fever  |   4.5 | 1669 Bloor Street W  | M6P 1A6     |
				| Halo Brewery |   4.0 | 247 Wallace Avenue   | M6H 1V5     |
				| Loblaws      |   2.5 | 2280 Dundas Street W | M6R 1X3     |
				+--------------+-------+----------------------+-------------+

SQL code used for analysis:

				/**********SQL Code*********/
				SELECT b.name
					-- 	,b.city
					-- 	,c.category
					,b.stars
					,GROUP_CONCAT(TRIM(DISTINCT (h.hours), '%MondayTuesWednesThursFriSatSun|%')) AS 'Opening hours'
				-- 	,b.review_count As N_review
				-- 	,b.address
				FROM (
					business b INNER JOIN category c ON b.id = c.business_id
					)
				INNER JOIN hours h ON h.business_id = b.id
				WHERE b.city = 'Toronto'
					AND c.category = "Food"
				GROUP BY b.name
					,b.stars
				/***************************/


2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.

i. Difference 1:
				The open ones have higher rating and number of reviews on average.
				
				+-------+----------+--------+
				| Satrs | # Review | STATUS |
				+-------+----------+--------+
				|  3.52 |     23.2 | Close  |
				|  3.68 |     31.8 | Open   |
				+-------+----------+--------+

SQL code used for analysis:

				/**********SQL Code*********/
				SELECT ROUND(AVG(b.stars), 2) AS Satrs
					,ROUND(AVG(b.review_count), 1) AS '# Review'
					,(
						CASE is_open
							WHEN 0
								THEN 'Close'
							ELSE 'Open'
							END
						) AS STATUS
				FROM business b
				GROUP BY b.is_open
				/***************************/

ii. Difference 2:
				The open businesses are received more full text reviews.
				
				+----------+------------+--------+
				| Positive | # FullText | STATUS |
				+----------+------------+--------+
				|       36 |         71 | Close  |
				|      235 |        565 | Open   |
				+----------+------------+--------+

SQL code used for analysis:

				/**********SQL Code*********/
				SELECT Count(CASE
							WHEN lower(r.TEXT) LIKE '%fantastic%'
								OR lower(r.TEXT) LIKE '%good%'
								OR lower(r.TEXT) LIKE '%excellent%'
								THEN 1
							END) AS Positive
					,count(r.TEXT) AS '# FullText'
					,(
						CASE is_open
							WHEN 0
								THEN 'Close'
							ELSE 'Open'
							END
						) AS STATUS
				FROM business b
				INNER JOIN review r ON b.id = r.business_id
				GROUP BY b.is_open
				/***************************/



3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:

i. Indicate the type of analysis you chose to do:
				I want to see if neighborhood affects the ratings.

ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
				To be able to figure out if there is a correlation between the neighborhood and the ratings, we need fair amount of data.
				Therefore I only check neighborhoods that at least have nine reviews.
				To do so I need 'id' 'neighborhood' from table 'business' together with 'id','business_id', and 'stars' from 'review' table.
				I use 'id' from 'business' table and 'business_id' from 'review' to perform 'Inner join'.
				Then we can calculate the total numder of reviews for each neighborhood and filter out the ones that don't have enough reviews.'
				The results show that the neighborhood affects the ratings.
				For example 'Spring Valley' tends to receive highest ratings and 'Southeast' the lowest.

iii. Output of your finished dataset:

				+-----------+---------------+---------+------+----+----+------+------+------+
				| city      | neighborhood  | # Reviw | Avg. | 5* | 4* |   3* |   2* |   1* |
				+-----------+---------------+---------+------+----+----+------+------+------+
				| Las Vegas | Spring Valley |      21 | 4.52 | 17 |  2 | None | None |    2 |
				| Las Vegas | Chinatown     |      16 | 4.06 |  7 |  4 |    4 |    1 | None |
				| Las Vegas | Westside      |       9 |  4.0 |  6 |  1 | None | None |    2 |
				| Las Vegas | The Strip     |      65 | 3.77 | 23 | 23 |    7 |    5 |    7 |
				| Las Vegas | Downtown      |      16 | 3.75 |  4 |  9 | None |    1 |    2 |
				| Las Vegas | Southeast     |      16 | 3.69 |  8 |  3 | None |    2 |    3 |
				+-----------+---------------+---------+------+----+----+------+------+------+

iv. Provide the SQL code you used to create your final dataset:

				/**********SQL Code*********/
				SELECT b.city
					,b.neighborhood
					,Count(r.id) '# Reviw'
					,Round(avg(r.stars), 2) 'Avg.'
					-- 	,min(r.stars) 'Min.'
					-- 	,max(r.stars) 'Max.'
					,sum(CASE
							WHEN r.stars = 5
								THEN 1
							END) '5*'
					,sum(CASE
							WHEN r.stars = 4
								THEN 1
							END) '4*'
					,sum(CASE
							WHEN r.stars = 3
								THEN 1
							END) '3*'
					,sum(CASE
							WHEN r.stars = 2
								THEN 1
							END) '2*'
					,sum(CASE
							WHEN r.stars = 1
								THEN 1
							END) '1*'
				FROM business b
				INNER JOIN review r ON b.id = r.business_id
				WHERE b.neighborhood IS NOT ''
					AND b.city = 'Las Vegas'
				GROUP BY b.neighborhood
				HAVING Count(r.id) >= 9
				ORDER BY avg(r.stars) DESC Limit 10
				/***************************/
