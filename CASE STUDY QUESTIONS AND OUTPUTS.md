# Note
I will only be displaying the first ten results of my query, if the output is more than 10.

 ## Question 1
 •	What is the average age of customers who have made claims?
 
 You need to Calculate the age of each customer by subtracting their birth year from the current year, then
 Calculate the average of the calculated ages.
 
 `SELECT ROUND(AVG(YEAR(current_date())-YEAR(birthdate)),2) AS avg_age
FROM car_insurance.vcars
WHERE claim_freq !=0;`
 ## Output
 ![A1](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261868337-9d158246-eda6-492a-a72d-bd0dd8fdf234.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051401Z&X-Amz-Expires=300&X-Amz-Signature=c01e97aad3a187c0063444776093a09af50cd3e1b06449c5a13b67c5b956d4a8&X-Amz-SignedHeaders=host)

 ## Question 2
 •	How does marital status correlate with claim frequency and claim amount?
 
 Calculate the average claim frequency and average claim amount for each "marital_status" group and round it to three decimal places.

 `SELECT marital_status, ROUND(AVG(claim_freq),3) AS avg_claim_freq, ROUND(AVG(claim_amt),3) AS avg_claim_amt
FROM car_insurance.vcars
GROUP BY marital_status
ORDER BY avg_claim_amt DESC;`
## Output
![A2](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261868674-6d458e11-c7e9-4389-addd-525a6b28ab93.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051433Z&X-Amz-Expires=300&X-Amz-Signature=f6290c92df80b58a68a48a5fe00df20a23e53e2210459de9c4a0101d62ded5a8&X-Amz-SignedHeaders=host)

## Question 3
•	What is the most common car color among customers with private car use?

Calculate the count of rows (number of cars) for each unique car color and assigns it the alias "car_color_count then 
filter the data to include only rows where the "car_use" column has the value 'Private', indicating private car usage.

`SELECT car_color, COUNT(*) AS car_color_count
FROM car_insurance.vcars
WHERE car_use = 'Private'
GROUP BY car_color
ORDER BY car_color_count DESC
LIMIT 1;`

![A3](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261868886-11610d28-3eac-4ae2-86c5-ed8f31d24699.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051456Z&X-Amz-Expires=300&X-Amz-Signature=7cde45d2160eedf42b524ff783431c9e2f3275ce845f6b7ebf3ab55e33af20e9&X-Amz-SignedHeaders=host)

## Question 4
•	How many customers have cars that are more than 5 years old and have made claims?

Count the number of rows (cars) that meet the specified conditions and assign it the alias "cars_more_than_5yrs_old then 
filter the data using the where clause to include only rows that meet the two conditions.

`SELECT COUNT(*) AS cars_more_than_5yrs_old
FROM car_insurance.vcars
WHERE car_year<=YEAR(curdate())-5
 AND claim_freq !=0;`
 
![A4](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261869123-92431627-29d6-44fd-a046-36c762f5581a.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051514Z&X-Amz-Expires=300&X-Amz-Signature=1196ed37a696db9365877664b26f148e0ba69b4f957d9fa1a438620eca4d2760&X-Amz-SignedHeaders=host)

## Question 5
•	Which coverage zone has the highest average claim amount?

Calculate the average claim amount for each "coverage_zone" group and round it to three decimal places.
Group the data by the "coverage_zone" column. This allows calculations to be performed for each unique coverage zone.
Limit the result set to only one row, which will be the coverage zone with the highest average claim amount.

`SELECT coverage_zone, ROUND(AVG(claim_amt),3) AS avg_claim_amt
FROM car_insurance.vcars
GROUP BY coverage_zone
ORDER BY avg_claim_amt DESC
LIMIT 1 ;`
 
![A5](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261869384-35517339-eb88-4cca-9158-b995775e15f6.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051529Z&X-Amz-Expires=300&X-Amz-Signature=3224439ff73f9b40e6991d9338be9ed9b71cc4578ac7e91a28c16bf5a9e1776f&X-Amz-SignedHeaders=host)

## Question 6
•	What is the total number of claims for customers with commercial car use?

 Calculate the sum of claim frequencies for all rows that meet the condition,
 "car_use" column has the value 'commercial', indicating commercial car usage, and assigns it the alias "total_claims
 
`SELECT SUM(claim_freq) AS total_claims
FROM car_insurance.vcars
WHERE car_use = 'commercial';`

![A6](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261869600-6b0f9129-7c78-4aac-bb1e-aea444176cb3.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051558Z&X-Amz-Expires=300&X-Amz-Signature=407c630f2fa796f05345089bcb43b9bc81ed6ebc262856fea42aa666fa2552ce&X-Amz-SignedHeaders=host)

## Question 7
 •	Do parents have a higher claim frequency compared to non-parents?

Calculate the sum of claim frequencies for all rows that meet the condition, and assign it the alias "total_claims
filter the data to include only rows where the "car_use" column has the value 'commercial', indicating commercial car usage.

`SELECT parent, AVG(claim_freq) AS avg_claim_freq
FROM car_insurance.vcars
GROUP BY parent
ORDER BY avg_claim_freq DESC;`

![A7](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261870544-7a89456e-105d-4bea-bcd1-cbd43ca9f893.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051620Z&X-Amz-Expires=300&X-Amz-Signature=2d4b047e785004998833203d0655c3a44ee96e11f83e09d04daf28fd3817fdbd&X-Amz-SignedHeaders=host)

## Question 8
 •	What is the average claim amount for parents compared to non-parents?

 Calculate the average claim amount for each unique value in the "parent" column and rounds it to three decimal places.
 
`SELECT parent, ROUND(AVG(claim_amt),3) AS avg_claim_amt
FROM car_insurance.vcars
GROUP BY parent
ORDER BY avg_claim_amt DESC;`

![A8](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/261870771-b5dfed75-df1d-4c91-be05-eebbbeb7e61d.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051634Z&X-Amz-Expires=300&X-Amz-Signature=49a917345d2031bd37aca36cd23d5a8a27e5e2915bdedcdda186c98fa50e8cc3&X-Amz-SignedHeaders=host)

## Question 9
 •	How does education level correlate with household income?

Retrieve the average household income for each education level from the "car_insurance.vcars" table. Group the data by education level calculate the average income, round it to three decimal places, and presents the results in descending order of average household income to provide insights into the relationship between education and income levels among the insurance clients.

`SELECT education, ROUND(AVG(household_income),3) AS avg_household_income
FROM car_insurance.vcars
GROUP BY education
ORDER BY avg_household_income DESC ;`

![A9](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262443276-f01df95a-4092-41eb-a12b-d0a66b44cb2a.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051651Z&X-Amz-Expires=300&X-Amz-Signature=5f43c546f1aa4f79c9b1048319df50857d23cd8d6d73a09ed275a411b8c9a51b&X-Amz-SignedHeaders=host)

## Question 10
•	What is the average claim frequency for male and female customers?

Retrieve the average claim frequency for each gender from the "car_insurance.vcars" table. Calculates the average claim frequency for male and female insurance clients, group the data accordingly, and present the results in descending order of average claim frequency to identify whether there's any difference in claim frequency between male and female customers.

`SELECT gender, AVG(claim_freq) AS avg_claim_freq
FROM car_insurance.vcars
GROUP BY gender
ORDER BY avg_claim_freq DESC;`

![A10](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262444727-e5eee591-2d30-426c-b4f2-80422d716566.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051706Z&X-Amz-Expires=300&X-Amz-Signature=0e31d98ab9c0f952bea435832c777fd75017a6e02810fc11265b787a5c114ce7&X-Amz-SignedHeaders=host)

## Question 11
•	Is there a correlation between the car's manufacturing year and claim frequency?

Get the average claim frequency for each car manufacturing year from the "car_insurance.vcars" table. Calculate the average claim frequency for different car years, group the data, and present the results in descending order of average claim frequency. The LIMIT 10 ensures that only the top 10 results are displayed, giving insight into the years with the highest claim frequencies.

`SELECT car_year, AVG(claim_freq) AS avg_claim_freq
FROM car_insurance.vcars
GROUP BY car_year
ORDER BY avg_claim_freq DESC
LIMIT 10;`

![A11](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262445854-0f90dadd-d167-4149-8b42-fb493827d69e.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051722Z&X-Amz-Expires=300&X-Amz-Signature=a48f97ef8341bbac100b9d8e3cb003b3d81b6222b78b5f3f0d94169677f034e5&X-Amz-SignedHeaders=host)

## Question 12
•	What is the average claim amount for cars manufactured before 2010?

calculate the average claim amount for cars manufactured before the year 2010 from the "car_insurance.vcars" table. Filter the data to consider only older cars and calculate the average claim amount for these vehicles. The result gives insight into the average claim amount associated with cars manufactured before 2010.

`SELECT ROUND(AVG(claim_amt),3) AS avg_claim_amt
FROM car_insurance.vcars
WHERE  car_year < 2010;`

![A12](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262446730-ded7cad9-df9e-4e37-a5e9-b6b6ac9116b5.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051733Z&X-Amz-Expires=300&X-Amz-Signature=49f8142b5e21bb4ff0a3cf83624ec597e5df9dd74a4b7762dd5f876095a7c713&X-Amz-SignedHeaders=host)

## Question 13
•	Which coverage zone has the highest claim frequency?

Calculate the total claim frequency for each coverage zone from the "car_insurance.vcars" table. Calculate the total claim frequency for different coverage zones, group the data, and present the result for the coverage zone with the highest total claim frequency. LIMIT 1 ensures that only the top result is displayed, giving insight into the coverage zone with the highest claim frequency.

`SELECT coverage_zone, SUM(claim_freq) AS total_claim_freq
FROM car_insurance.vcars
GROUP BY coverage_zone
ORDER BY total_claim_freq DESC
LIMIT 1;`

![A13](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262447577-b26a46ba-38c4-413d-a0d0-32d818637435.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051744Z&X-Amz-Expires=300&X-Amz-Signature=c0869377f7e9fa50cea733ca3f8926b95ffdb5d9c08c75f1d0b503f81d3923cc&X-Amz-SignedHeaders=host)

## Question 14
•	Is there a relationship between coverage zone and average claim amount?

 Retrieve the average claim amount for each coverage zone from the "car_insurance.vcars" table. Calculate the average claim amount for different coverage zones, group the data, and present the results in descending order of average claim amount to provide insights into the relationship between coverage zones and the average claim amounts associated with them.
 
`SELECT coverage_zone, ROUND(AVG(claim_amt),3) AS avg_claim_amt
FROM car_insurance.vcars
GROUP BY coverage_zone
ORDER BY avg_claim_amt DESC;`

![A14](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262448441-c0e27de8-7841-4379-8172-21d3602787a2.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051802Z&X-Amz-Expires=300&X-Amz-Signature=a8d7fd3488c1c7cef5b853e6de8cb768bcb545f80957957939de34837f06c383&X-Amz-SignedHeaders=host)

## Question 15
•	What is the most common car make and model among customers with high claim amounts?

 Retrieve the total claim amount for each combination of car make and model from the "car_insurance.vcars" table. Calculate the total claim amount for different car makes and models, group the data, and present the result for the combination with the highest total claim amount. LIMIT 1 ensures that only the top result is displayed, giving insight into the car make and model associated with the highest total claim amount.
 
`SELECT car_make, car_model, ROUND(SUM(claim_amt),3) AS total_claim_amt
FROM car_insurance.vcars
GROUP BY car_make, car_model
ORDER BY total_claim_amt DESC
LIMIT 1;`

![A15](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262593044-b29b9827-96e4-45f5-89bf-099aa5ed2a6a.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051824Z&X-Amz-Expires=300&X-Amz-Signature=032363e3342210780da18d2872a8431c99619ac01a89c67bb9370d99eeb82b7a&X-Amz-SignedHeaders=host)

## Question 16
•	Are certain car makes associated with a higher claim frequency?

 Calculate the average claim frequency for each car make from the "car_insurance.vcars" table. Calculate the average claim frequency for different car makes, group the data accordingly, and present the results in descending order of average claim frequency. The LIMIT 10 ensures that only the top 10 results are displayed, giving insight into the car make with the highest claim frequencies.
 
`SELECT car_make, ROUND(AVG(claim_FREQ),3) AS avg_claim_freq
FROM car_insurance.vcars
GROUP BY car_make
ORDER BY avg_claim_freq DESC
LIMIT 10;`

![A16](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262594042-ca211fca-14d9-4ecf-b7f1-8ec8591f8cd5.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051842Z&X-Amz-Expires=300&X-Amz-Signature=747142193be0f0c10e95d40171011bab8bdcb6e2cdb01922799d6719b711ad06&X-Amz-SignedHeaders=host)

## Question 17
•	How does household income relate to claim frequency and claim amount?

Retrieve the average claim amount and average claim frequency for each household income level from the "car_insurance.vcars" table. Calculate these averages, group the data by household income, and present the results based on the specified ordering. The LIMIT 10 ensures that only the top 10 results are displayed, giving insight into the relationships between household income, average claim amount, and average claim frequency.

`SELECT household_income, ROUND(AVG(claim_amt),3) AS avg_claim_amt, ROUND(AVG(claim_freq),3) AS avg_claim_freq
FROM car_insurance.vcars
GROUP BY household_income 
ORDER BY avg_claim_amt,avg_claim_freq DESC
LIMIT 10;`

![A17](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262595364-88499100-d38d-49dc-b7ca-b2d242da3ab5.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051902Z&X-Amz-Expires=300&X-Amz-Signature=6312ee46c8cabbfc91c32284058c11b0e7e62961ade0710ca1f04ef2224420a0&X-Amz-SignedHeaders=host)

## Question 18
•	How does the number of kids driving the same car impact claim frequency and claim amount?

Retrieve the average claim amount and average claim frequency for different categories of "kids_driving" from the "car_insurance.vcars" table. Calculate these averages, group the data by the number of kids driving, and present the results in descending order of the average claim amount. The analysis provides insights into how the number of kids driving the same car relates to average claim amounts and frequencies.

`SELECT kids_driving, 
ROUND(AVG(claim_amt),3) AS avg_claim_amt,
ROUND(AVG(claim_freq),3) AS avg_claim_freq
FROM car_insurance.vcars
GROUP BY kids_driving
ORDER BY avg_claim_amt DESC;`

![A18](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262596807-58f0c8da-3579-44e6-ab9a-b7ee1f28e7b0.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051917Z&X-Amz-Expires=300&X-Amz-Signature=aff9c822329b0a8033087a66c1f76e6024c10532e36d5759df2363b1a5899682&X-Amz-SignedHeaders=host)

## Question 19
 •	What is the distribution of claim amounts among customers?

 Retrieve the count of customers for each unique claim amount from the "car_insurance.vcars" table. Calculate the number of customers who made claims of different amounts, group the data by claim amount, and present the results in descending order of claim amount. The LIMIT 10 ensures that only the top 10 results are displayed, giving insight into the distribution of claim amounts and the number of customers associated with them.

`SELECT claim_amt,
       COUNT(*) AS num_customers
FROM car_insurance.vcars
GROUP BY claim_amt
ORDER BY claim_amt DESC
LIMIT 10;`

![A19](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262598090-63a8c681-137c-40ea-823e-51f1f4676b12.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051928Z&X-Amz-Expires=300&X-Amz-Signature=3cca1dd482f7c7f314a07a06a2e349621750e85a9a2022518a4e4240a2094a34&X-Amz-SignedHeaders=host)

## Question 20
 •	What is the proportion of parents among male and female customers?

Calculate the count of customers and calculate the proportion of customers with specific parenting statuses within each gender category from the "car_insurance.vcars" table. Group the data by gender and parenting status. Perform the calculations, and presents the results. The analysis provides insights into the proportion of parents among male and female customers and how parenting status varies based on gender.

`SELECT gender,
       parent,
       COUNT(*) AS num_customers,
       COUNT(*) / SUM(COUNT(*)) OVER (PARTITION BY gender) AS proportion
FROM car_insurance.vcars
GROUP BY gender, parent;`

![A20](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262603153-020d33c4-8f0e-4858-bad7-2fe05280bf61.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051944Z&X-Amz-Expires=300&X-Amz-Signature=616070ec28902f4a8c48f77ee67e381022f9ce95323dddddb2bf596f3387f97e&X-Amz-SignedHeaders=host)

## Question 21
•	Do male or female customers have more kids driving the same car on average?

Calculate the average number of kids driving among customers within each gender category from the "car_insurance.vcars" table. Calculate the average, group the data by gender, and present the results. The analysis provides insights into the average number of kids driving for male and female customers

`SELECT gender,
       AVG(kids_driving) AS avg_kids_driving
FROM car_insurance.vcars
GROUP BY gender;`

![A21](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262604283-680a1d91-c3cf-473c-9b6f-717562da7748.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T051956Z&X-Amz-Expires=300&X-Amz-Signature=f3bcb9db12c1a0812c64cb72b830852a152fa19ca709b90ff1d30597d2382f56&X-Amz-SignedHeaders=host)

## Question 22
•	Is there a difference in claim frequency between customers with private and commercial car use?

Retrieve the average claim frequency for customers within each car use category (private or commercial) from the "car_insurance.vcars" table. Calculate the average claim frequency, group the data by car use, and present the results. The analysis provides insights into the average claim frequency based on the purpose of car use.

`SELECT car_use,
       AVG(claim_freq) AS avg_claim_frequency
FROM car_insurance.vcars
GROUP BY car_use;`

![A22](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262605138-6e14be7e-ee1f-48fd-bb07-883cb5930893.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T052017Z&X-Amz-Expires=300&X-Amz-Signature=5168c8ff6cf95c73cf34e3fac1b5c9555a76093141b5eb8e2188bb5b15265425&X-Amz-SignedHeaders=host)

## Question 23
•	Do customers with commercial car use tend to have higher claim frequencies?

Calculate the average claim frequency for customers with "commercial" car use from the "car_insurance.vcars" table. Calculate the average claim frequency, filter the data for commercial car use, group the data by car use (which is 'commercial' in this case), and present the results. The analysis provides insights into the average claim frequency specifically for customers with commercial car use

`SELECT car_use,
       AVG(claim_freq) AS avg_claim_frequency
FROM car_insurance.vcars
WHERE car_use = 'commercial'
GROUP BY car_use;`

![A23](https://github-production-user-asset-6210df.s3.amazonaws.com/130906675/262606076-c94f16c1-5fdd-4413-9b47-57d23c86239b.jpg?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVCODYLSA53PQK4ZA%2F20250428%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250428T052030Z&X-Amz-Expires=300&X-Amz-Signature=782b700fd1207124614a7c0d2a69f91242b12a98621e5760cc02553b83deede0&X-Amz-SignedHeaders=host)

