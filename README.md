# Lede 2023 Project 01
 I try to see who the most popular weightlifter on [hookgrip](https://www.instagram.com/hookgrip/) is. 


# Data sources
I used [APIFY's Instagram Post Scraper API](https://apify.com/apify/instagram-post-scraper) to scrape over 2,000 posts on hookgrip's instagram from 21st June 2023 to their first post in 2013.  

# Analysis
Using the number of times hookgrip posts about a particular athlete, I attempt to quantify who the most popular weightlifter is, broken down by gender and year. There aren't *that* many weightlifters which makes my life a bit easier. 

# Caveats 
The number times a weightlifter appears on Hookgrip is a function of 
- how many times they compete
- how 'impressive' their lifts are 
given these two points, a more accurate description of this analysis would probably be 'who the most filmed weightlifter on hookgrip is'. 

With the information available, I could do a composite metric like how many times they appeared, how many likes and comments posts about them generate but in the interest of time, that's a task for another day. 

Counting by other metrics, like number of followers, would probably paint a different picture. Some lifters are super popular but don't compete that often. I might do that analysis some other time...

# Repository contents
...