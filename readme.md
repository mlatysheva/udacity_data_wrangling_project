
# Udacity Data Analyst Nanodegree

## Data Wrangling Project

### We Rate Dogs from Twitter

Prepared by Maria Latysheva, August 2020


This is the Data Wrangling project as part of the Udacity Data Analyst Nanodegree. The purpose of the project is to use all the knowledge from the course on wrangling and analysing data to create an interesing analysis about We Rate Dogs account from Twitter.

The goals of the projects are:
- to gather data from three different sources
- to clean the data and put it in one or several cleaned master dataframe
- to analyse the dataset and create interesting insights based on the We Rate Dogs data
- to vizualise one of the insights

## Gather Data

We gather data on We Rate Dogs from three different sources.

#### 1) WeRateDogs Twitter archive

#### 2) Tweet image predictions

Download tweet image predictions programmatically from the file `image_predictions.tsv`, which is hosted on Udacity's servers. We will use the `Requests` library and the following URL: https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv

#### 3) Twitter JSON data via Twitter API

Note: Unfortunately, Twitter did not approve my developer's application :-( Although I used the sample wording provided in the project description. I cannot say for sure why this happened but guess that the thing could lie in my country of origin, being Russia at the moment.

For this reason I have to use the txt file provided by Udacity.


## Assess Data

I will assess the data in the three dataset keeping in mind the following Project requirements:
- We only want original ratings (no retweets) 
- The ratings must have images
- We need to assess and clean at least 8 quality issues and at least 2 tidiness issues in these datasets.


### Issues identified in the course of visual and programmatic data assessment that will be cleaned

#### Quality

##### `twitter archive` table
1) Some tweets are retweets and some are replies. We are interested, however, only in original tweets.

2) The columns relating to retweets and replies are not relevant to our analysis. Same is true about the column `source`.

3) There are some entries without images. We are interested only in entries with images. So these will be classified as missing data.

4) The `name` column contains invalid names like the words "a", "one", etc.

5) The columns `timestamp` and `retweeted_status_timestamp` have type `str` but should be of the `datetime` type.

6) Some rating numerators are either wrong or way too big. Should be limited to the number that appears logical and frequent in many tweets.

7) Some rating denominators are not equal to 10 and are way too big. All denominators should be 10.

##### `image predictions` table

8) Some breeds start with low case letter, some with capital. If breeds contain two words, they are separated by underscore.

##### `twitter json` table
No quality issues detected.

#### Tidiness
1) The dog status in the `twitter archive` table is split into four columns. There should be one column for the dog status.

2) Some `expanded_urls` entries in the `twitter archive` table contain duplicate urls split by a comma. Only one url should be for each entry.

3) Retweets and favourite counts in the `twitter json` table should be part of the `twitter archive` table.

4) The data in columns p1, p2 and p3 of the `image predictions` table, as well as the data in columns p1_conf, p2_conf, and p3_conf are data of the same types. We can drop unnecessary columns and merge the remaining predictions with the `twitter archive` table.

## Clean Data

Each issue identified is cleaned by defining the issue, coding and testing the result.

The cleaned datasets are merged into one master dataset.
Rearranged the columns by moving the text columns to the right of the table
Renamed 'p1', 'p1_conf' and 'p1_dog' columns to make their names more explicit
Saved the cleaned dataset to a master csv file



## Analyse and Visualise Data

In the analysis, I answered the following questions about the We Rate Dogs dataset:

1) Is there a strong correlation between retweets and favourite counts? Is there a strong correlation between the favourite counts and the rating?

2) What are the top ten favourite breeds?

3) Which dog status has the highest average rating?

4) What is the distribution of ratings? Which rating is most common?

I provided visualisations for the analysis and drew conclusions.