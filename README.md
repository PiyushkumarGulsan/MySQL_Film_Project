# MySQL_Film_Project #

*"A MySQL project analyzing film inventory, replacement costs, customer rentals, and payment monitoring.  It includes queries for retrieving unique film titles, rental counts, replacement cost analysis, and fraud detection through payment tracking.  The project provides key business insights using structured SQL queries."*

**Situation:   The company needs to renew its insurance policy, and underwriters require updated data from the Maven Movies database to proceed.**

**Objective:   This MySQL project focuses on extracting and analyzing data from various tables to answer key business and insurance-related questions. 
             It includes SQL queries for film inventory, rental patterns, replacement costs, and payment monitoring to provide insights required for policy renewal.**

**Some Of the Question asked by Company :-**

Q 1. We will need a list of all staff members, including their first and last names, email addresses, and the store identification number where they work.
 
Q 2. We will need separate counts of inventory items held at each of our two stores.

Q 3. We will need a count of active customers for each of our stores. Separately.

Q 4. In order to assess the liability of a data breach, please provide a count of all customer email addresses stored in the database.

Q 5. We are interested in how diverse our film offering is as a means of understanding how likely we are to keep customers engaged in the future. Please provide a count of unique film titles we have in inventory 
     at each store and then provide a count of the unique categories of films we provide.

Q 6. We would like to understand the replacement cost of our films. Please provide the replacement cost for the film that is least expensive to replace, the most expensive to replace, and   the average of all 
     films we carry.

Q 7. We are interested in having you put payment monitoring systems and maximum payment processing restrictions in place to minimize the future risk of fraud by our staff. Please provide the average payment we 
     processed , as well as the maximum payment we have processed.

Q 8. We would like to better understand what our customer base looks like. Please provide a list of all customer identification values, with a count of rentals they have made all-time,
     with our highest volume customers at the top of the list.


**Answers:-**


 
**Q1.  We will need a list of all staff members, including their first and last names, email addresses, 
and the store identification number where they work.**

```
 Use mavenmovies;

select 
     first_name,
     last_name,
     email,
     store_id
FROM staff;
```

![image](https://github.com/user-attachments/assets/21e14b7e-a796-4b89-9e2b-a2d7d496496a)



**Q2. We will need separate counts of inventory items held at each of our two stores.**

```
select
     store_id,
     COUNT(inventory_id) AS inventory_items
From inventory
Group By 
	 store_id;
```

![image](https://github.com/user-attachments/assets/31e372de-c924-4c23-aec4-9ab101c99aa1)

     
**Q3. We will need a count of active customers for each of our stores. Separately.**
```
Select 
     store_id,
     Count(customer_id) AS active_customer
From customer
WHERE active = 1
GROUP By 
    store_id;
 ```
![image](https://github.com/user-attachments/assets/f841dbe8-cc07-4aa9-9e4a-622d1d9c100f)

**Q4. In order to assess the liability of a data breach, please provide a count of all customer email addresses stored in the database.**

```
Select 
      count(email) AS emails
From customer;
```
![image](https://github.com/user-attachments/assets/950b8fde-b727-435e-8f75-557f74cb3283)

**Q5.We are interested in how diverse our film offering is as a means of understanding how likely you are to keep customers engaged in the future. Please provide a count of unique film titles we have in inventory at each store and then provide a count of the unique categories of films we provide.**

```
select 
      store_id,
      Count(distinct film_id) AS unique_films
 FROM inventory
 GROUP BY 
       store_id;
```
![image](https://github.com/user-attachments/assets/963f1192-26c1-4fa3-aac5-09568bc1c4de)


```
SELECT 
      COUNT(Distinct name) AS Unique_categories
From category;
```
![image](https://github.com/user-attachments/assets/d19febf7-63dc-436b-bf15-ea52914bbc68)


**Q6. We would like to understand the replacement cost of our films. Please provide the replacement cost for the film that is least expensive to replace, the most expensive to replace, and   the average of all films we carry.**


```
SELECT 
     MIN(replacement_cost) AS least_expensive,
     MAX(replacement_cost) AS most_expencsive,
     AVG(replacement_cost) AS average_replacement_cost
From film;
```

![image](https://github.com/user-attachments/assets/77a56341-0f3e-43d8-aeeb-40967afd2bc1)

**Q7. We are interested in having you put payment monitoring systems and maximum payment processing restrictions in place to minimize the future risk of fraud by our staff. Please provide the average payment we processed , as well as the maximum payment we have processed.**

```
SELECT
     AVG(amount) AS average_payment,
     MAX(amount) AS max_payment
From payment;
```
![image](https://github.com/user-attachments/assets/4d65e765-9032-44f6-ba91-3eb64dee5088)

**Q8. We would like to better understand what our customer base looks like. Please provide a list of all customer identification values, with a count of rentals they have made all-time, with our highest volume customers at the top of the list.**


```
SELECT
     customer_id,
     COUNT(rental_id) AS number_of_rentals
From rental
Group By 
      customer_id
Order By
	Count(rental_id) DESC;
```
![image](https://github.com/user-attachments/assets/266c1049-0785-40e8-8ea9-a8f67870f2a8)


**💡 Suggestions for Business Improvement**

*✔️ Staff & Store Management*

***If some stores have lower inventory levels, increase stock of popular films to maintain customer engagement.
Conduct regular staff training to improve customer service.***

*✔️ Film Inventory Optimization*

****Analyze rental trends to stock more films from popular categories.
Reduce inventory of less-rented films to optimize space.***

*✔️ Customer Engagement & Marketing*

***Reward top customers (high rental count) with discounts or loyalty programs.
Identify inactive customers and send promotional emails to encourage rentals.***

*✔️ Fraud & Payment Monitoring*

***Implement alerts for unusually high payments to prevent fraud.
Set a maximum transaction limit for online payments.***

*✔️ Data Privacy & Security*

***Encrypt customer emails in the database to prevent breaches.
Conduct regular security audits on customer data.***

