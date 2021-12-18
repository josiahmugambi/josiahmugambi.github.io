## Making sense of my text messages - especially those from banks and MPESA

### Background
I needed a project to keep myself actively engaged learning AI/ML as so far it's been start-stop. Usually the best way to build up a skill. I've done lots of reading and studying - there are numerous resources online such as  [WQU](https://wqu.org) which has a great data science course. From a data perspective, it has occured to me that I did a fair bit of it while working supporting Telco OSS platforms some years back. 

### Goal
Keeping tabs on personal finance is a useful thing to do. However, most people don't actively or daily track their personal finances and I believe it is primarly because it is a tedious and boring.So I've been thinking about how take care of the mundane using tech, and reduce it to a minimum, while building up my AI/ML and python skills as I create something useful for myself and others.

### The General Plan
- First thing I want to attempt is to classify my text messages - based on sender.
- Next thing will be to make sense of my various finance related text messages and attempt to classify the MPESA transactions.
- Once I have done this well, I'll start on a way for people to upload an MPESA text then have it spit out a spend/income category based on the contents

There are several paths that this could follow after that but first things first.  I'll be using Jupyter-Lab for most of this until I'm at a point when it makes sense to put up a simple site or build an app. 

I'll attempt to 'learn in public' as nudged on by a certain [Eric Gitonga](https://www.linkedin.com/in/egimba/?originalSubdomain=ke), and see how far I go with this - posting periodic updates here.

### Updates (in reverse chronological order)

#### 18th Dec 2021
Goals for the day
- [X] put some content up on learn.mugambi.co.ke
- [X] plan out the next steps

Spent some time putting this up. It's probably the only way I'll be able to keep myself accountable. 

What I probably need to do is to first categorize texts based on sender, content (and possibly date and time). Initially looking at the data, I think the sender is enough in most cases, so this should be straightforward.
Next would be to focus on the financial text messages and further categorize them. (Origin - easy based on sender, type of income/expense? - not straightforward?).

#### 16th Dec 2021

Goals for the day
- [X] label the small dataset
- [X] figure out and implement a better way to do the training/test data split
    there are several ways. will try go through them at different points.
- [ ] explore different classifiers
- [ ] put some content up on learn.mugambi.co.ke

Clearly I am rusty and have lots of way to go. I should have realised that my approach is wrong. But that's part of this process. I managed to label 150 rows but using a classifier this way is probably the wrong approach. 

My current set of text message categories:
- FINANCIAL - Banks, MPESA, Bills - will go deeper
- INFO - (It's amazing how much of this is essentially spam)
- PEOPLE

#### 14th Dec 2021

Goals for the day
 - [x] Organize texts by year (2018,2019,2020,2021) 
 - [X] randomly select ~100-150 rows from 2018. [This](https://datatofish.com/random-rows-pandas-dataframe/) was useful.
 - [X] take ~70% as training data and 30% as test data
 - [ ] label the 70% training data
 - [ ] attempt to classify 2019
 - [ ] put some content up on learn.mugambi.co.ke

Quickly learning that labelling data will take far longer than expected (it's tedious!). Also that I should label the entire dataset. (Yes I forgot)

Also just realized that the meat of the work might be to make sense of the actual text messages?

Future goals: - some NLP on the body of the text in order to determine category, along with sender?

#### 10th Dec 2021
Took a break to catch up on prep for Google's Professional Cloud Architect certification exam (which I passed!). It was hard! I'm hoping to sit the Professional Data Engineer certification exam sometimes in January 2022 so for the next few weeks will be tinkering on GCP's data products along with Jupyter while on this (side) project.

Started on a little feature engineering on Jupyter. A short working session (as it was late Friday). Created new columns from the date column into year, month, day, and hour along with actual time. Useful to analyze later. Added a new column for category. Goal now is to categorize these. Next time - perhaps work with ~100 rows randomly selected to start with, categorize 40 by hand, then see if I can implement a multi-class classifier to do the rest.

I'll also attempt to model the same on BigQuery ML (which I think is pretty cool!) and see how the results vary.

Also a [little reading](https://towardsdatascience.com/stop-persisting-pandas-data-frames-in-csvs-f369a6440af5) on best way to persist Pandas data. Parquet can be natively read into BigQuery. Not sure about Pickle. However Pickle is a native Python format.

Felt very rusty as I haven't done much coding or hacking the last couple of years but I think I now know where I want to go. Stuff will come back to me along with the new things I'm learning, and I'll be able to move faster.

#### 26th Nov 2021
Started by dumping all my text messages then exported them using [SMS Backup and Restore](https://synctech.com.au/sms-backup-restore/). This creates an XML dump. I need to figure out how parse it (shouldn't be too hard) automatically/on demand, but for now I used the tool on the website then copy-pasted to Excel,
Formated the phone numbers as text (Custom -> Chose 0) then exported to CSV
Loaded new CSV as a Pandas Data frame and did some basic cleanup

First thing I want to do is categorize all my text messages.