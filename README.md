<img src="https://bit.ly/2VnXWr2" alt="Ironhack Logo" width="100"/>

# Migration and Happiness

*Group project, week 6*  
*Andres, Alex, Imogen*

*August 2020 cohort, Berlin, 18.09.20*

## Content
- [Project Description](#Project_Description)  
- [Questions & Hypotheses](#Questions_&_Hypotheses)  
- [Dataset](#dataset)
- [Workflow](#workflow)
- [Organization](#organization)
- [Links](#links)

## Project_Description
Our group wanted to explore possible correlations between migration and happiness. We merged several csv files from various sources to look for trends, check for correlations and conduct analyses. We utilised Python for table merging, data cleaning, to check correlations and to make regression analyses and we utilised Tableau to visualise our results. 


## Questions_&_Hypotheses

Our guiding question was: Which factors cause migration?  

This question has two parts: 
1. Which factors cause people to emigrate?
2. Which factors influence people's choice of destination country? 

Starting out, we had two main hypotheses:
1. Countries with high emigration rates have a low happiness rating.
2. Countries with high immigration rates have a high happiness rating.


## Dataset
We utilised 3 separate databanks for our analysis.

1. World Happiness Reports for years 2015 - 2019
Source: Gallup World Poll
Link: https://www.kaggle.com/unsdsn/world-happiness
We used all 5 separate csv files (1 per year)

2. Global net migration for every 5 years between 1962 and 2017
Source: United Nations Population Division
Link: https://data.worldbank.org/indicator/SM.POP.NETM?end=1981&start=1981&view=map&year=2017
We used 2 separate csv files (1 main + 1 supplementary including regional and income level categorisations)

3. Global population for years 1960 - 2017
Source: United Nations Population Division
Link: https://data.worldbank.org/indicator/SP.POP.TOTL
We used 1 main csv file

## Workflow

First, we decided on our topic and began a broad search for data. Ideally, we would have liked to do a time series with happiness and migration together. However, since the World Happiness Reports started in 2015 and the UN migration data is only shown for 5 year periods, we were only able to find overlapping data for the year 2017. Therefore, we decided to conduct time series on our migration data and happiness data separately to examine trends and changes over time. We decided to include an additional dataset with global population numbers to merge with our migration dataset, so that we could check the migration as a percentage of the overall population and create an additional column: net migration rate. This allowed us to compare absolute migration numbers with migration rate, which led to some interesting findings. 

We extracted the happiness score for the years 2015 - 2019 into a new data frame and calculated the mean of the years per country. We found that the 5 highest scoring countries are mainly in Northern Europe (except Switzerland) and have remained stable over time. The 5 lowest scoring are mainly in Africa (except Syria), and peaked in 2019. 

Then, we merged the datasets and looked for correlations between happiness and migration for the year 2017, to test our hypotheses. We used linear regression (OLS) to check which features from our collected data were more likely to affect the migration (net and rate). First, we took a general approach, using all the information collected getting a very good approx (~80%). To avoid noise (multicolinearity) in our model, we broke down our analysis using only a few factors for iteration, getting an accuracy only of 19%. So we concluded that among other factors, the happiness score of a country, while having a statistically significant correlation with migration, is not enough to explain migration patterns.

We noticed some gaps in our migration dataset which are likely due to irregular immigration, since this is difficult to record and is often not captured in official UN surveys. For example, as a likely consequence of the still ongoing Venezuelan crisis, we observed in our data emigration from Venezuela in recent years and corresponding expected increased immigration in surrounding countries. However, the data did not reflect earlier well documented migration flows from the 1980s onwards from Colombia to Venezuela, resulting from the conflict taking place in Colombia, lack of opportunities and poor administration management (further information can be found in Martinez's work [here](https://repository.ucatolica.edu.co/bitstream/10983/3107/4/TESINA%20EL%20PROCESO%20MIGRATORIO%20ENTRE%20COLOMBIA%20Y%20VENEZUELA%201989%202014%20%20PRINCIPALES%20CAUSAS%20Y%20EFECTOS%20P.pdf) in Spanish). Language, cultural and geographic proximity are also decisive factors in these circumstances. 
For a future project, it would be interesting to locate additional datasets containing more information on different migration categories, in particular irregular immigration, to reflect immigration flows more accurately. 


## Organization

We created a kanban board on Trello to organise and coordinate work among ourselves. That way, we could distinguish between tasks that needed to be done and tasks that would be nice to have if time permits. The kanban board also allowed us to assign tasks to one or more of us, making it easier to keep track of who was doing what. 

Our repository contains the following files:
- Presentation - *STILL TO ADD*
- Datasets folders containing csv files: 
  - 1_Migration
    - 0_Metadata
    - 1_migation_main (original dataset)
    - 2_migration_countries (original dataset)
    - 3_migration_main_clean (cleaned dataset)
    - 4_migration_countries_clean (cleaned dataset)
  - 2_Population
    - 0_Metadata
    - 1_population_main (original dataset)
    - 2_population_countries (original dataset)
    - 3_population_main_clean (cleaned dataset)
  - 3_Happiness
    - 2015
    - 2016
    - 2017
    - 2018
    - 2019
  - 4_Merged
    - 1_migration_population_merge (merge of 1_migration_main and 1_population_main)
    - 2_migration_population_merge_clean (cleaned version of above dataset)
    - 3_migration_merge_clean_final (merge of 1_migration_population_merge and 2_migration_countries)
    - 4_migration_happiness_merge (merge of 3_migration_merge_clean_final and 2017 Happiness csv)
  - 5_Subsets *- keep this or delete??*
- Notebooks folder containing Jupyter Notebook files:
  - Merge_1_migration_population
  - Merge_2_migration_tables
  - Merge_3_migration_happiness


## Links

[Repository](https://github.com/imogen-rickert/migration_happiness)  

TABLEAU *still to add when finalised*

[Trello](https://trello.com/b/rFmUeEsa/migration-happiness)

[Colombia-Venezuela Migration](https://reliefweb.int/sites/reliefweb.int/files/resources/Venezuela%20Migration%20Crisis%20in%20Colombia.pdf) 
