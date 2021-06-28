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
  
The facebook data set have been given in this repository in facebook_data file. Store the data in HDFS.

### Create a table in Hive ###
```terminal
create table facebook_data(id int, age int, day int, year int, month int, gender string, tenure int, friends int, \\
friend_init int, likes int, likes_recd int,mlikes int, mlikes_recd int, wlikes int, wlikes_recd int) \\
row format delimited \\
fields terminated by ',';

```

1. Run the following command to find out the total number of users in this dataset.

```hive
select count(*) from facebook_data;
```
2. Run the following command to find out the number of facebook users above the age of 25.
```hive
select count(*) from facebook_data where age>25;
```
And the execute the following hive commands.


