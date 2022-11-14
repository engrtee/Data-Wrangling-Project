## Reporting: Data Wrangling for the WeRateDog tweets

The data wrangling steps are highlighted as follows

1. Data Gathering

2. Data Assessment

3. Data Cleaning


### DATA GATHERING

Gathering of Data was carried out from the three sources below

1. Tweeter Archive data for WeRateDogs tweets in a CSV file provided by Udacity. This file was programatically downloaded in the python notebook using the link provided in the resources tab of the Udacity project

2. The image prediction file for dogs also provided by Udacity in a tsv file. This file was also programatically downloaded using the requests library and saved in the workspace

3. Retweet and favorite counts for each tweet in the archive data. This data was pulled from twitter by querying the twitter API using pythons tweepy library.

### DATA ASSESSMENT

Data Assessment was carried out visually and programatically on all the datasets. 

###### The following quality issues where detected

1. It was observed that the source column is in HTML- formatted string

2. The columns for dog ratings which has numerator and numerator needs to be worked on.

3. Removal of records that are not needed such as retweets leaving only original tweets. 

4. Missing values are observed in some columns namely retweeted_status_id, retweeted_status_timestamp, in_reply_to_user_id,retweeted_status_timestamp, retweeted_status_user_id, in_reply_to_status_id,retweeted_status_id,in_reply_to_user_id

5. There are lots of missing names from the list under 'None' and random names like 'a' and 'an' would likely be parts of string that got taken out of context.

6. Observation of invalid dataypes for columns timestamp and tweet_id

7. To ensure uniformity across the data sources the column id in the tweet api table should be changed to tweet_id.

8.  Some tweets had "\&amp" combined with ";" which is the html code to display just the ampersand


###### The following Tidiness issues where detected
1. pupper, puppo, floofer and doggo columns should be combined to form on column named "dog_stage"

2. The three tables should be merged to form one table





### Data Cleaning

The define-code-test framework was used extensively in the process of cleaning the data. The resolved tidiness and quality issues are outlined below.

###### Fixing Quality issues
1. Removal of the HTML formatting from the source column 

2. Removal of Ratings denominators which had zero values , conversion of the numerator's data type to float and denominator's data type to int. Creation of a new column for rating by division of the numerator by the denominator.

3. Removal of replies and retweets from the twitter archive dataset in order to ensure we have just orignal tweets.

4. Removal of unneeded columns from the twitter archive dataset namely  retweeted_status_timestamp, retweeted_status_user_id, in_reply_to_status_id,retweeted_status_id,in_reply_to_user_id.

5. Cleaning of the dog name column was carried out to get rid of invalid dog names

6. Conversion of the data type for the time stamp column to datetime64.

7. Conversion of the column id name in the tweet api table to tweet_id to ensure uniformity of tweet_id.

8. Cleaning process was carried out on the text data which resulted in the removal of the html code &amp and the links included in the text






######  Fixing Tidiness issues

1. pupper, puppo, floofer and doggo columns were merged into one column named "dog_stage"

2. The three tables were merged to one table and the result was saved to twitter_archive_master.csv in the workspace
