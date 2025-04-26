# CYCLISTIC BIKE-SHARE ANALYSIS CASE STUDY


## INTRODUCTION
This capstone project is the final part of completing the Google Data Analytics Professional Certificate course. In this case study I will analyze a public dataset for a fictitious company, Cyclistic. For this analysis, I will be using R programming language because of its statistical computing capabilities, rich ecosystem of packages, and strong visualization tools. To cater the relevant question, I will follow the six phases approach of the data analysis: Ask, Prepare, Process, Analyze, Share, and Act.



## SCENARIO

Cyclistic is a bike-share company in Chicago. In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The company offers three types of flexible pricing plans: single-ride passes, full-day passes, and annual memberships. Single-ride passes and full-day passes riders are referred as casual riders.
The finance analysts at Cyclistic concluded that annual members are much more profitable than the casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Lily Moreno, the director of marketing, is convinced that maximizing the number of annual members will be the key to future growth. Moreno believes there’s a solid opportunity in converting casual riders into full-fledged members, instead of focusing on all-new customers, as casual riders are already familiar with the Cyclistic program and have consciously chosen Cyclistic for their transportation needs.
As a junior data analyst, I will follow the steps of the data analysis process as mentioned above and find out actionable insights for the stakeholders.



## **DATA ANALYSIS PROCESS**

### **1. Ask Phase:**

•	**Business Objective:** The business objective of is to increase the number of annual Cyclistic members in order to enhance profitability and ensure business growth. By converting more casual riders into annual members, Cyclistic aims at creating a more stable revenue stream.

•	**Business Task:** To design effective marketing strategies that focus on encouraging casual riders to purchase annual memberships. 

In order to do this, it is important to first address the following questions by analyzing the Cyclistic historical bike trip data to draw conclusions and identify trends.
1. How do annual members and casual riders use Cyclistic bikes differently? 
2. Why would casual riders buy Cyclistic annual memberships? 
3. How can Cyclistic use digital media to influence casual riders to become members? 

•	**Stakeholders:**

1. *Lily Moreno:* The director of marketing and your manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program. 

2. *Cyclistic’s Marketing Team:* The Marketing Team will be responsible for conducting the analysis and developing the marketing strategy based on the insights gained.

3. *Cyclistic executive team:* The notoriously detail-oriented executive team will decide whether to approve the recommended marketing program.


### **2. Prepare Phase:**

This phase of data analysis involves data collection and preparation. Identifying the data sources, gathering relevant data and verifying if it is accurate and useful for answering the questions.

**Data Description:** For this case study, I’ll be using a public dataset, made available by Motivate International Inc. My focus will be on the data from first quarter of 2019 and 2020, which is organised in two separate CSV files. 2019 first quarter CSV file contains 12 columns and 3,65,070 rows, while 2020 first quarter CSV file contains 13 columns and 4,26,888 rows. The data is organised in a way that will provide an opportunity to conduct a thorough analysis to identify ridership patterns and gain valuable insights. 

* **Data Credibility:** The data used in this study meets the ROCCC standards of data credibility.
1.*Reliable:* The data is trustworthy, accurate, complete, and unbiased, having undergone verification to ensure its suitability for the intended purpose.
2.*Original:* The data is sourced directly from the primary, authentic provider.
3.*Comprehensive:* The data encompasses all essential information necessary to address the question or resolve the problem at hand.
4.*Current:* Given its monthly release schedule, the data remains up-to-date and pertinent.
5.*Cited:* The data is appropriately referenced and attributed in the project.

* **Data Licensing:**
The data for this project is provided by Motivate International Inc. under the [Data License Agreement for Divvy Bikes Data](http://divvybikes.com/data-license-agreement). All personal information has been removed to protect user’s privacy. The data is shared only for analysis purposes as allows by the license.



### **3. Process Phase:**

Given the large-scale nature of the dataset, **R** was selected as the preferred tool because it offers powerful data analysis packages like ggplot2, dplyr and tidyr, etc, which are highly efficient for reshaping, transforming and visualizing the data. 

This phase involves- 

* Combining all the downloaded files into one.
* Cleaning and organizing the data to simplify the analysis.
* Removing the inconsistancies, filling in missing values and,
* Ensuring that the data is ready before starting the analysis. 

First, I installed and loaded all the required R packages and then imported the CSV files.
