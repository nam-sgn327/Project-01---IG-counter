# Lede 2023 Project 01
 I try to see who the most popular weightlifter on [hookgrip](https://www.instagram.com/hookgrip/) is. 

# Data sources
I used [APIFY's Instagram Post Scraper API](https://apify.com/apify/instagram-post-scraper) to scrape over 2,000 posts on hookgrip's instagram from 21st June 2023 to their first post in 2013.  

# Analysis
Using the number of times hookgrip mentions about a particular athlete, I attempt to quantify who the most popular weightlifter is, broken down by gender and year. There were more weightlifters than I expected so I didn't get a chance to include everyone, jus the ones that appeared a lot.

# Caveats 
The number times a weightlifter appears on Hookgrip is a function of 
- how many times they compete
- how 'impressive' their lifts are 

Given these two points, a more accurate description of this analysis would probably be 'who the most filmed weightlifter on hookgrip is'. 

Counting by other metrics, like number of followers, would probably paint a different picture. Some lifters are super popular but don't compete that often. For a more holistic analysis, I could do a composite metric like how many times an athlete appeared, how many likes and comments posts about them generate but in the interest of time, that's a task for another day. 

# Repository contents
1. `data` folder contains:
- the `raw json` folder contains `hookgrip.json` that I called with an API using `requests`
- the `cleaned_csvs` folder contains and pivoted dataframe on jupyter that I exported to datawrapper or rawrgraphs 
2. the `notebooks` folder contains 2 drafts of the code I used
- `hookgrip_mostpopular.ipynb` is the notebook where I did it the super manual way with copy paste between Excel and Jupyter. I gave up making a dataframe from this workbook
- `hookgrip_mostpopular_v2.ipynb` is where I took a step back and restructured my data so that rawrgraphs won't hate me and so I can pivot it on my own
3. the `docs` folder contains:
- `pictures` folder with images exoported from rawgraphs and images used in the website 
- `soma_style.css` that I stole from Soma 
- `index.html` main website

# Findings
1. `Lasha Talakhadze` is the most popular weightlifter on hookgrip. I wouldn't be surprised if this was the same with any other instagram page page like atg or weightliftinghouse considering he is by far the strongest weightlifter there has ever been. 
2. `Mattie Rogers` is the 2nd most popular, not far after Lasha. This surprised me, I was expecting a Chinese lifter but the American women did very well. This made more sense once I remebered she is very outspoken and active on social media and has been medalling consistently at international comepition in years
3. hookgrip probably has a regional bias. Some lifters are a lot more prolific but get featured less often. Could be because their ground team don't get a chance to go to competitions inside of China? Some of the American lifters that featured prominently on the page don't compete at large international meets that often (or at least don't rank well enough for a casual to notice) like C.J. Cummings for example. 

# Data collection and analysis process
Steps of the data analysis process:
1. Find the `mentions` key in the json and loop through each name, I can usually tell who the lifter is by instagram handle, so this wasn't too time consuming. What was difficult was trying to get a list of all the handles that a person used to have e.g. they changed their surname to their spouse's name, the json scraper would randomly add punctuation at the end of the handle like `rahmat_erwin_` becomes `rahmat_erwin,` or `rahmat_erwin's`
2. For some atheltes that don't have an instagram and can't be tagged, get a list of names that they could be referred to as e.g. for Asian names like 'Shi Zhiyong' could be written as `Shi Zhiyong`, `Shi Zhi-yong` etc... and check if the list of names is in the `captions` key of the json, to mixed effect...I checked and the counts for Shi Zhiyong don't make sense, some athletes have a count of 0 when I can see they've been mentioned 
3. Defined a function `count_compete` to count the amount of times the atlete was on film at a competition, regardless of whether they have an instagram account. 
4. Make two dictionaries `m_dict` for the men and `w_dict` for the women and add to a dataframe `df_women`. `df_men` `df_all` just in case. I used the `explode` function to get a matrix for my table and make sure the same lifter appears on multiple rows so I can pivot and graph with rawrgraphs


# Skills and learnings
1. As a lifter I follow said "Slow is smooth and smooth is fast". Don't try to brute force it, even though there are "only" about 80 rows and it seems managable. It's really not. 
- Once I thought about how I could structure my data, I used some lists to populate each column in `hookgrip_mostpopular_v2.ipynb` then pivot and group after rather than doing it beforehand in `hookgrip_mostpopular.ipynb` and then adding to a separate column. 
- I wasted so much time trying to figure out if I should pivot the data first (bad idea) or leave it in its raw form work before realising rawgraphs will pivot for me and won't accept data from 2 columns anyway

2. I *really* got to learn how to use dictionaries and functions properly and actually thinking about how to structure the data. 
- From the start there was a CSV format that I could have downloaded and use to but I guess I wanted to make my life harder. On a more practical side I can't imagine how I would loop through each name in the mentions list if the file format was a csv

3. I learnt a new function `explode` from stack overflow, which was fun cause I felt like my brain was also about to explode with this project. 
- I knew I had to use the apply method to get the formula to copy paste but it was hard and Python got angry at me. Explode was pretty helpful for duplicating the names across multiple rows to conveniently group and pivot. 

4. In times of stress you go back to what you're used to. At one point I used Excel to concat my python code and copy paste it back into Jupyter, like a sinner. 
- This project was like API on steroids and once Soma hinted that I could restructure the data, it was a lot easier and could be coded in a lot fewer lines. 

5. I didn't think I would finish the project but here we are. Still looking forward to that code review though so I can figure out how to properly use regex functions to match instagram handles. 