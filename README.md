# assignment_data_modeling
Mmmmm.... dataaaaa....

*Include your ERM modeling "pseudocode" in the space below*


Name: Nicholas Romeo, Renzo Tomlinson


<!--Basic-->

<!--You are building a free online learning platform which will be used by students who are exclusively online (but don't need to be logged in or kept track of). You offer many different courses, each with a title and description, and each course has multiple lessons which can be displayed. Lesson content consists of a title and body text. What are the Goals? Entities? Attributes, types and constraints? Relationships? Design the data model for this web app.-->

We need to anonymously browse classes and lessons

Courses

id: INT
title: VARCHAR
description: VARCHAR
Created_At: DATE
Updated_At: DATE


Lessons

id: INT
course_id: INT
title: VARCHAR
body: TEXT

1:m

<!--You are building the profile page for a new User on your login site. You are already storing your User's username and email, but now you want to collect demographic information like City, State, Country, Age and Gender. Think -- how many profiles should a User have? How would you relate this to the User model? Design the data model for this web app.-->

User

id: INT
username: VARCHAR
email: VARCHAR
profile_id: (foreign key)

Profile:

id: INT
City: VARCHAR
State: VARCHAR
Country: VARCHAR
Age: INT
Gender_id: gender_id (foreign key)
user_id: INT (foreign key)

Gender:

id: INT
gender: VARCHAR(1)

User:Profile 1:1
Profile:Gender 1:1

<!--You want to build a message board like Hacker News. Users can post links. Other users can comment on these submissions or comment on the comments. How would you make sure a comment knows where in the hierarchy it lives? Design the data model for this web app.-->

Users

id: INT

Posts

id: INT
body: TEXT
user_id: INT

Comments

id: INT
body: TEXT
user_id: INT
parent_id: INT (composite key)
post_id: INT (composite key)

<!--You want to build an e-commerce site like a very simplified Amazon.com. You'll need to keep track of products, users, orders, shipments and all the bits and pieces necessary to glue them all together. Design the data model for this web app. How can you handle the quantity of items in each order? How do you know where an order has been shipped? Bonus: What happens to your historical data if a user opts to delete their account? How might you handle this?-->

Products

id: INT
name: VARCHAR
description: VARCHAR

Users

id: INT
addressNumber: INT
street: VARCHAR
zip: INT
city: VARCHAR
state: VARCHAR

Orders

id: INT
user_id: INT
shipment_id: INT

Shipments

id: INT
order_id: INT

Order_Products

order_id: INT
products_id: INT
product_quantity: INT

user and orders: one to many
order and shipment: one to one
orders and products: many to many (join table with order_id and products_id)
(shipment has access to user through order, access to products through order)

<!-- (Optional) You want to collect analytics data for visitors and logged-in-users who are visiting your website. This includes basic information like page views and more advanced things like link clicks and time on page. You ideally want to tie this information back to a given user if possible. Design the data model for this analytics infrastructure. You'll have to use your judgement about what additional attributes would be interesting to track -->

Users
id: INT
username: VARCHAR

UserSession
id: INT
user_id: INT (foreign key)
start_time: DATE
stop_time: DATE

Webpage
id: INT

Links
id: INT
webpage_id: INT

WebpageSessions
id: INT
webpage_id: INT
usersession_id:INT
duration:INT
exit_link: VARCHAR

WebpageClickEvent
id: INT
WebpageSession_id: INT


LinksClickEvent
id:INT
link_id:INT
WebpageSession_id:INT

User can have many usersessions, usersessions have one user
user-sessions can have many webpage-session, webpage-sessions can have one usersessions
Webpage can have many webpage-sessions, webpage-session can only have one webpage





