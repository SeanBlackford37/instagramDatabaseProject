# instagramDatabaseProject
For my Comp 375 class our final project was to take a website/company/app and turn it into what they look like as a database

To open the database run the Pychram file or I have provided the Psql file

-I attempted to recreate what Instagram looks like behind the scenes
-This was our final project for our database class(Comp 375)
-The languages I used were Postgres and python(pycharm)
-Attached is the visualiation of the database 
 

-Age was randomly generated base on stats I pulled from different websites based on actual instagram data
Ages 13–17: 57 million (7%)
Ages 18–24: 270 million (32%)
Ages 25–34: 270 million (32%)
Ages 35–44: 131 million (15%)
Ages 45–54: 68 million (8%)
Ages 55–64: 30 million (3%)
Ages 65+: 18.3 million (2%)


Data that was made up was a public vs private profile 
-Private 40%
-Public 60%


For everything I could do I tried to randomly generate it 
-Post count, post likes, follow count, follower count eat

-I only did the United States for location which is also random
-Users can have from 0 to 50 posts
-Verified Users 5% of the time profile will be verified 
-Profile can't be private if they are verified 


-Not done explore table
-Not done search engine
-Not done search engine list

-Hashtags were selected from the top 25 list of used hashtags 



--This query lets you search a person's post and to limit it based on likeCount
select * from apost where userid = 'QUCE9CXJ3R' and likecount > 10;

--Returns all the posts the given user has ever posted on
select apost.postid,commentid,comments.userid  from comments join apost using(commentid) where comments.userid = 'QUCE9CXJ3R';

--Shows the top 5 most views posts
select * from apost order by postviews desc limit 5;

--Shows the person with the greatest amount of posts limit 1
select count(userid) as postCount, userid from apost group by userid order by postCount desc limit 1;

--Show the person with the greatest amount of followers limit 10
select count(yourid), yourid as followerCount from followers group by yourid order by count(yourid) desc limit 10;

--Shows that the user has a lot of followers but a small amount of people liked the post
select count(yourid) as followerCount ,apost.likecount,yourid from followers join apost using (userid) group by yourid,likecount order by followerCount desc limit 1;
