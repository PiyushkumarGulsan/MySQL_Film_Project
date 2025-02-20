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

![image](https://github.com/user-attachments/assets/bcd648c7-3c9a-44c6-a12d-67e8bf8f71d2)


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

