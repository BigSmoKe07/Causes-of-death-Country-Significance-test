# Pair-wise UN Causes of death Country Significance test with Welch's t-test

### Proposed Sample Changes
To ```change the countries to be compared for causes of death```, the following things must be changed within the notebook:

1. **Get subset of the main UN causes of death dataset** (Change the country name to your country)<br>
df_india = getSubset(df,**"India"**).sort_index(ascending=True)<br>
df_usa = getSubset(df, **"United States"**).sort_index(ascending=True)

2. **Rertrieve the population in arrays** (Change the country name to your country)<br>
india_population_arr = list(df_population[df_population["Country"]==**"India"**]["Population"])<br>
usa_population_arr = list(df_population[df_population["Country"]==**"USA"**]["Population"])

3. **Normalise the population to 1000,000 scale** (Change the country name to your country)<br>
normalizeDf(df_india,india_population_arr)<br>
normalizeDf(df_usa,usa_population_arr)

4. **Perform t-test** (Change the country name to your country)<br>
usa_india_t_test = t_test(df_india,df_usa)<br>

5. **Visualise the findings** (Change the country name to your country)<br>
finalResult(df_usa,df_india,usa_india_t_test,**"USA"**,**"INDIA"**,0.05,show_only_nnullAcceptance = False)

# Project Related Information
## Introduction
This repository presents a case study on understanding causes of death using inferential statistics and data visualizations. The project aims to analyze the causes of death in five selected countries, namely the United States of America, India, China, United Kingdom, and Somalia. By applying Welch's t-test and visualizing the data, the project explores the variations in mortality rates among these countries. By changing the country parameters, all UN countries can be compared for significance of causes of deaths (per 100,000 of the population).

## Project Components
The repository contains the following components:

**Analysing Deaths by causes (code).ipynb**: This Jupyter Notebook file contains the code used for data preprocessing, statistical analysis, and data visualization. It showcases the step-by-step process of conducting Welch's t-test and generating the visualizations.

**Project Report.pdf**: The project report provides detailed explanations of the research methodology, statistical analysis, and visualizations. It includes insights gained from the comparative analysis of causes of death among the selected countries.

**annual_deaths_by_cause.csv**: This CSV file contains the dataset with annual estimates of deaths per country according to various causes. It serves as the primary data source for the analysis.

**population.xlsx**: The population.xlsx file includes population data for the selected countries. It is used to standardize the deaths data and calculate deaths per 100,000 people.

## Dataset and Research Methodology
The dataset used in this project is sourced from **Oxford University** and contains annual estimates of deaths per country according to various causes. The data spans the years ```1990 to 2019``` and is compiled from reputable sources such as CDC, The Lancet, WHO, and governmental agencies.

To ensure comparability among countries, the data is *standardized* by dividing the deaths by the population size and scaling it up to deaths per 100,000 people. This normalization process allows for meaningful comparisons across countries with varying population sizes.

The research methodology includes two main components: statistical analysis using Welch's t-test and data visualizations.

## Welch's t-test
Welch's t-test, also known as the unequal variance t-test, is employed in this study to test the hypothesis that two populations have equal means. This test is chosen for its reliability in situations where samples have unequal variances and/or sample sizes. It assumes that the samples are normally distributed.

The t-score is calculated using the Welch–Satterthwaite equation, which approximates the degrees of freedom associated with the variance estimate. Python's scipy library is utilized to perform Welch's t-test.

## Data Visualization
In addition to statistical analysis, data visualizations play a crucial role in understanding and interpreting the results. Libraries such as pandas, matplotlib, seaborn, and numpy are used to create informative visualizations that aid in comparing the causes of death among the selected countries.

## Comparative Analysis
The comparative analysis focuses on exploring the causes of death in the selected countries. The analysis is presented in a booklet format, arranged country-wise, with individual tests and their corresponding inferences. The project's source code is provided as a snippet at the end of the report.

The analysis primarily involves the application of Welch's t-test to compare the average deaths caused by different variables in each country. The statistical significance of the differences is evaluated based on the p-value obtained from the t-test. Additionally, data visualizations, including line plots and bar charts, are employed to illustrate the trends and variations in deaths among the countries.

# Sample Screenshots of findings/visualisations

#### Comparing HIV Aids related deaths in India vs USA

<img width="576" alt="image" src="https://cdn.discordapp.com/attachments/1098198554398441544/1235561172720422942/239825895-480cc695-d3d3-40ae-83d1-66d85e917df0.png?ex=6634d183&is=66338003hm=0dec2c600aa23d83fb1484a20be91b4ca4d982907970cb5f93b9ba13fe6dc706">



#### Comparing Meningitis related deaths in India vs USA
<img width="569" alt="image" src="https://cdn.discordapp.com/attachments/1098198554398441544/1235561132647907328/239825679-5893732d-fb13-4973-bc89-d36670fd428f.png?ex=6634d179&is=66337ff9hm=e5f1ef7a73df901de91e378b800335851ee21bd8ec0665d64432409dae75d8d5">

