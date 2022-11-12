
# Twitter bot for Northeastern-Course-Repository

The overall goal of this project is to create a database containing all relevant resources. The first step towards this is by using data extracted via Twitter pertinent to programs, courses, and resources offered by Northeastern university. We have written a twitter bot that gets tweets, user details, tweet tags, and tweet mentions relevant to our project- Northeastern-Course-Repository. 

## UML diagram for the Northeastern-Course-Repository Twitter domain

![UML](https://user-images.githubusercontent.com/106060204/201489210-287e63f5-70ca-4102-910c-6990316e603e.jpeg)



# USE-CASES, SQL STATEMENTS, AND RELATIONAL ALGEBRA

**1.** **Use Case:** Which tags are mostly used while posting tweets for the NEU course repo page? 

Description: The user tweets a comment/question for the NEU course repo. 

Actor: User

Precondition: When a user wants to ask a question regarding anything related to NEU, they tweet using the screen name of the NEU course repo. 

Actor action: The user request a response

System Responses: The requested Twitter handle replies back. 

Post Condition: Customer query successfully answered

Alternate Path: The user question is not relevant or they don’t receive a response. 

**SQL Statement:  **

 SELECT 
    t1.tags, t2.tweet
FROM
    Tweet_Tag t1
        RIGHT JOIN
    Tweet_Details t2 ON t1.tweet_id = t2.tweet_id
WHERE
    t1.tags IS NOT NULL;

**Relational Algebra:**

π t1 . tags, t2 . tweet
 σ NOT (t1 . tags = NULL)
  (ρ t1 tweet_tag ⋈ t1 . tweet_id = t2 . tweet_id
   ρ t2 tweet_details)

**2. Use Case:** Which users are requesting information on Twitter related to career Events offered by Northeastern University and how many followers do they have? 

Description: The user tweets a comment/question using relevant keywords: jobs, neujobs, jobsearch.

Actor: User

Precondition: The user wants to ask a question regarding jobs related to programs offered at NEU. 

Actor action: The user request a response

System Responses: Users are directed to relevant job postings and informational websites. 
Alternate Path: The user question is not relevant or they don’t receive a response. 

**SQL Statement:**

SELECT 
    t1.name, t1.twitter_handle, t3.followers_count, t2.tags, t1.tweet
FROM
    Tweet_Details t1
        JOIN
    Tweet_Tag t2 ON t1.tweet_id = t2.tweet_id
       JOIN
	User t3 ON t1.twitter_handle = t3.twitter_handle
WHERE
    tags LIKE '%careers%';

**Relational Algebra:**

π t1 . name, t1 . twitter_handle, t3 . followers_count, t2 . tags, t1 . tweet
 σ tags LIKE "%careers%"
  (ρ t1 tweet_details ⋈ t1 . tweet_id = t2 . tweet_id
   ρ t2 tweet_tag ⋈ t1 . twitter_handle = t3 . twitter_handle
    ρ t3 user)


# Team Members: 

Utkarsha Shirke (email: shirke.u@northeastern.edu )
Supriya Tripathi (email: tripathi.su@northeastern.edu)
Ishika Misal (email: misal.i@northeastern.edu)

# Project Description: 

The goal of this project is to create a database containing all relevant resources. The resources database will include: 

Programs offered on the Boston campus of Northeastern University in the College of Engineering, and details about their duration, offerings, and specializations. 
The relevant study material (paid and free resources) for all courses offered by COE. 
Tools and software required by the courses.  
Program contacts (Professors/Advisors/Current Teaching Assistants). 
Future career outcomes post-degree completion. 

We aspire to help learners through our initiative by helping them collate the resources they need to navigate their course. 

# Future Direction:

We are planning to web scrape the NEU’s website and other educational platforms extensively to gather data. 
We would research and conduct surveys to collate the best fit for our database. 
We would be then using the above information to create the resources database for any particular course offerings. 

# Outcome:

A consolidated resource repository as a database that is publicly available on GitHub. This will include documentation on how to use the database and a detailed walkthrough by the end of the project. 


