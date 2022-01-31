# Facebook Data Analysis Using Hadoop and Hive #

There have been many procedure and equally many types of analysis methods applied to arrive at conclusions. This project is all about analyzing the facebook dataset with hadoop and Hive:

In this project I will find out the following result from Facebook data.
  
  * Find out the total number of users in this dataset.
  * Find out the number of facebook users above the age of 25.
  * Do male or female facebook users tend to have more friends? 
  * How many likes do young people recieve on facebook opposed to older people? 
  * Find out the count of facebook users for each birthday month.
  * Do young members use mobile phones or computer for facebook browsing?
  * Do adult members use mobile phones or computers for facebook browsing?

## Data Set Description ##

  Column 1  :   userid	
  
  Column 2  :   age				
  
  Column 3  :   dob_day
  
  Column 4  :   dob_year	
  
  Column 5  :   dob_month
  
  Column 6  :   gender
  
  Column 7  :   tenure
  
  Column 8  :	  friend_count
  
  Column 9  :	  friendships_initiated
  
  Column 10 : 	likes
  
  Column 11 :	  likes_received
  
  Column 12 :	  mobile_likes	
  
  Column 13 : 	mobile_likes_received
  
  Column 14 :	  www_likes	
  
  Column 15 :   www_likes_received
  
The facebook data set have been given in this repository in fb_data file. Store the data in HDFS.

### Create a table in Hive ###
```hive
create table facebook_data(id int, age int, day int, year int, month int, gender string, tenure int, friends int, \\
friend_init int, likes int, likes_recd int,mlikes int, mlikes_recd int, wlikes int, wlikes_recd int) \\
row format delimited \\
fields terminated by ',';

```
### To load the fb_data csv file into Hive
```
load data local inpath '/home/hduser/fb_data.txt' into table facebook_data;
```

Run and execute the following hive commands for the following problem statements.

### 1. Find out the total number of users in this dataset.

```hive
select count(*) from facebook_data;
```
![image](https://user-images.githubusercontent.com/52828894/123734781-9b3ecc00-d8bb-11eb-833b-ef60fc9dfc21.png)

### 2. Find out the number of facebook users above the age of 25.

```hive
select count(*) from facebook_data where age>25;
```
![image](https://user-images.githubusercontent.com/52828894/123734933-e5c04880-d8bb-11eb-826a-24ac425d9dfd.png)

### 3. Do male or female facebook users tend to have more friends? 

```
select gender,avg(friends) from facebook_data group by gender;
```
![image](https://user-images.githubusercontent.com/52828894/123735023-0dafac00-d8bc-11eb-8250-c6460beba242.png)

### 4. How many likes do young people recieve on facebook opposed to older people.
```
select avg(likes_recd) from facebook_data where age>=13 AND age<=25; 
```

```
select avg(likes_recd) from facebook_data where age>25;
```
### 5. Find out the count of facebook users for each birthday month.
```
select month,count(*) from facebook_data group by month;
```
![image](https://user-images.githubusercontent.com/52828894/123735197-667f4480-d8bc-11eb-9566-b6900ffa682b.png)

### 6. Do young members use mobile phones or computer for fb browsing?
```
select avg(mlikes),avg(wlikes) from facebook_data where age>=13 AND age<=25;
```
![image](https://user-images.githubusercontent.com/52828894/123735407-c83fae80-d8bc-11eb-874a-32c7f3cc7b87.png)

### 7. Do adult members use mobile phones or computer for fb browsing?
```
select avg(mlikes),avg(wlikes) from facebook_data where age>=35;
```
![image](https://user-images.githubusercontent.com/52828894/123735465-e4435000-d8bc-11eb-8a37-f438a6eb4ead.png)

#### Make sure your hadoop cluster is running before executing the hive file. ####
