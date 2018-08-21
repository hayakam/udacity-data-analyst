
# Wrangling efforts on The WeRateDogs Twitter archive dataset

by Masa, <u>Hayakawa</u>

<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#Wrangling-efforts-on-The-WeRateDogs-Twitter-archive-dataset" data-toc-modified-id="Wrangling-efforts-on-The-WeRateDogs-Twitter-archive-dataset-1">Wrangling efforts on The WeRateDogs Twitter archive dataset</a></span><ul class="toc-item"><li><span><a href="#Summary" data-toc-modified-id="Summary-1.1">Summary</a></span></li><li><span><a href="#1.-Gathering" data-toc-modified-id="1.-Gathering-1.2">1. Gathering</a></span></li><li><span><a href="#2.-Assessing" data-toc-modified-id="2.-Assessing-1.3">2. Assessing</a></span><ul class="toc-item"><li><span><a href="#2-1.-Quality-Issues" data-toc-modified-id="2-1.-Quality-Issues-1.3.1">2-1. Quality Issues</a></span></li><li><span><a href="#2-2.-Tidiness-Issues" data-toc-modified-id="2-2.-Tidiness-Issues-1.3.2">2-2. Tidiness Issues</a></span></li></ul></li><li><span><a href="#3.-Cleaning" data-toc-modified-id="3.-Cleaning-1.4">3. Cleaning</a></span><ul class="toc-item"><li><span><a href="#3-1.-Tidiness-Issues" data-toc-modified-id="3-1.-Tidiness-Issues-1.4.1">3-1. Tidiness Issues</a></span></li><li><span><a href="#3-2.-Quality-Issues" data-toc-modified-id="3-2.-Quality-Issues-1.4.2">3-2. Quality Issues</a></span></li></ul></li><li><span><a href="#4.-Conclusion" data-toc-modified-id="4.-Conclusion-1.5">4. Conclusion</a></span><ul class="toc-item"><li><span><a href="#Limitations" data-toc-modified-id="Limitations-1.5.1">Limitations</a></span></li><li><span><a href="#Future-work" data-toc-modified-id="Future-work-1.5.2">Future work</a></span></li></ul></li></ul></li></ul></div>

## Summary

This report summarizes the data wrangling effort I have conducted as a part of analysing `The WeRateDogs Twitter archive` dataset.

The wrangling efforts on the datasets are conducted through below 3 steps:

1. Gathering
2. Assessing
3. Cleaning

## 1. Gathering

In this project 3 datasets are gathered from 3 different data sources.

* The WeRateDogs Twitter archive: `twitter-archive-enhanced.csv`

    This file is provided by Udacity in csv format.
    

* Tweet image predictions: `image-predictions.tsv'`


    This file is downloaded from the spcified url(`'https://d17h27t6h515a5.cloudfront.net/topher/2017/August/599fd2ad_image-predictions/image-predictions.tsv'`) in tsv format.


* tweet archive: `tweet_json.txt`

    This information is downloaded from Twitter using twitter API. The data was in json format and stored locally with file name of `tweet_json.txt`


## 2. Assessing

After assessing those 3 datasets, in total 8 quality issues and 2 tidiness issues are identified as follows:
    

### 2-1. Quality Issues


* twitter_archive_enhanced:


    * This dataset containing lots of retweets and replies in addition to original tweets.
    * Data type of `timestamp` column is object, not timestamp.
    * `rating_numerator` column contains some value other than rating, such as 1776(year), etc.
    * `rating_denominator` column includes Invalid values, such as zero, etc.
    * `dog name` column includes words that seem to be unlikely to be a name of a dog, such as 'a', 'actually', 'such', 'quite', 'None', 'not', 'his', 'old', 'by', 'light', 'space', 'officially', etc.
    * 1,976 records has none of stages (doggo, floofer, pupper, puppo), evene if tweet text contains stage information. Particularly, 'doggos' is not regarded as 'doggo'.
    * Some of the records has more than 1 stage values at the same time. Should stage be mutually exclusive?

* tweet_json:


    * data type of retweet_count and favorite_count columns are float.

### 2-2. Tidiness Issues

* `twitter_archive_enhanced` dataset has multiple columns (`doggo`, `floofer`, `pupper`, and `puppo`) represents a stage.
        
* All three dataasets can be merged into one dataset.

## 3. Cleaning


Best practice says it is better to resolve tidiness issues prior to dealing with quality issues.

### 3-1. Tidiness Issues

* For `twitter_archive_enhanced` dataset, it is better to consolidate the 4 columns representing dog stages (i.e. doggo, floofer, pupper, and puppo) into one single column `stage`.


* Merge all the three datasets, `twitter_archive_clean`, `tweet_json_clean`, and `tweet_json` into one dataset.

### 3-2. Quality Issues

Below 8 issues identified in Assessing phase are managed as follows:

* Only retained original tweets. The records of retweets and replies were eliminated.
* For records whose `rating_denominator` value is 0, replace with appropriate value. Those records are happened to be eliminated during the above process.
* Converted data type of `timestamp` column from object to timestamp type.
* For records with `rating_numerator` column containing decimal points, replace the value with rounded to integer.
* For records that have the words unlikely to be a name for dog_name, replace with 'None'.
* Although a tweet does not always contain stage info in the text, still some of them are missing even if it was found in the text, particularly, 'doggos' is not regarded as 'doggo'. Therefore, for records without stage info, if the text contains a term 'doggos' regard it as 'doggo' too.
* For the records that have more than 1 stage values, the records with the eldest stage, i.e. 'doggo', was taken.
* Converted data type of retweet_count and favorite_count columns from float to integer.


## 4. Conclusion


### Limitations
* In this project, only 8 quality issues and 2 tidiness issues are cleaned, as hilighted in 3. Cleaning section, though there are some more quality and tidiness issues.

### Future work
* It might be possible to collect some more accurate information from text field, regarding rating numerator, rating denominator, for example.
