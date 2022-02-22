# Exploring UK PLC Director Gender Diversity and Connectedness: <br /> Data Analysis of Companies House Data

Using data downloaded and scraped from Companies House in March 2021, I investigated the gender diversity and connectedness of UK Public Limited Company Officers. 

## Table of Contents
* [Project Goals](#project-goals)
* [Data Source](#data-source)
* [Data Extraction](#data-extraction)
* [Gender Diversity](#gender-diversity)
* [Connectedness](#connectedness)
* [Future Ideas](#future-ideas)


## Project Goals
I was interested to see the details of the officers (Directors and Company Secretaries) of larger UK public companies (PLC's - companies whose shares can be freely traded and so tend to be larger and are subject to more regulations). More specifically, I was interested in two areas - the actual gender diversity as well as how connected the director pool was (i.e. a look at the size of the issue of a small number of people controlling a large number of companies actually was).


**Goals:** Discover the actual gender diversity of UK PLC Officers and establish how interconnected UK PLC boards are <br />

## Data Source
* [UK Companies House](#uk-companies-house-) 
 

#### UK Companies House <br />
[UK Companies House](https://www.gov.uk/government/organisations/companies-house). This gives the latest data for all UK companies (private and public). There is a statutory requirement for all UK companies to keep their information up to date.

---


## Data Extraction

The starting point was the basic company data dataset available from companies house. This dataset (available [here](http://download.companieshouse.gov.uk/en_output.html)) gives a snapshot of basic data of all live companies in the UK - unfortunately not including officer details.<br />

The next steps were to iterate through the companies listed in the snapshot to extract the PLC's and iterate through the PLC's to scrape the officer details from the Companies House website.


## Gender Diversity

The next step was to extract the gender of each officer based solely on the names recorded at Companies House. This was not entirely straightforward for two reasons;<br /> 
* it is possible for a company to be another company's officer
* the multiple nationalites involved required both European trained and Indian trained gender guessers to be used ( [gender_guesser](https://pypi.org/project/gender-guesser/) and [guess_indian_gender](https://pypi.org/project/guess-indian-gender/))

Plotting the results obtained from analysing the percentage of female officers by size of company board, we can see that overall the female representation is not marvellous at 17%, but with some encouraging signs of a trend to higher percentages with larger boards (with anomalies). Plenty of room for improvement!<br />

<img src = "assets/percentfemoffs.png"><br />

## Connectedness

The last part of the exercise was to look at how interconnected UK PLC boards were. I did this using networkx to explore the size of the largest connected node in the data, as well as to explore the degrees of connectedness in the data.<br />
For this part of the exercise, I looked at a subset of the data (with board sizes of 5 or more) to enable usable output. I looked at two areas;<br />
* the connected nodes - firstly the whole dataset;<br />

<img src = "assets/5all.png"><br />

and secondly the largest component - this seems to be large, indicating a significant number of multiple directorships;<br />


<img src = "assets/5largestcomponent.png"><br />
 
* the degree of connectivity (how many connections each director has) - firstly a histogram of the distribution (which seems to have high frequencies in the 5 and 10 directorship buckets);<br />

<img src = "assets/deg5hist.png"><br />

and secondly the most connected officers (consistent with the above - showing an area for attention regarding multiple directorships);<br />

<img src = "assets/deg5top.png"><br />

## Future Ideas
There are certainly plenty of areas for further exploration, but the most interesting from my point of view would be;<br />
* Rerunning the exercise on an annual basis to see how things are changing
* Drill into more detail in the multiple directorships (do we see the same combinations of people on different boards? Is gender significant for multiple directorships?) 
* Are there other areas we could analyse? Is it possible to derive any reliable ethnicity data from the raw data that we have?
* Can we compare with equivalent data from other countries - where would we start?

