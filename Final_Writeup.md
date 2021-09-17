# Exploratory Data Analysis of MTA Data

Alex Stake

## Abstract

The goal of WTWY and this exploratory data analysis is to increase the overall number of contact points for survey teams to increase the number of email signatures gathered, gala attendance, and overall outreach. This is achieved through looking at MTA turnstile data to gather the number of daily exits at each station over three months of data from 2021. The recommended stations and day for WTWY to post their teams are Grand Central Station and 42nd St, 34th St and Herald Square, 42nd St and Port Authority, 34th and Penn Station, and Flushing and Main all on Thursdays as these are the stations and the day with the highest overall traffic.

## Design

This project is looking to find the highest number of points of contact while ensuring that the people encountered are more likely to provide their email and attend the WTWY gala. In order to achieve this, I focused on exploring the number of daily exits for the 5 stations with the highest overall traffic. By using exit data we can reduce the number of people who will be in a rush and more likely to pass by the survey teams, and by using the stations with the most traffic we are able increase the number of contact points and the subsequent emails gathered, gala attendance, and awareness of the issues women in technology sectors face. Another point to consider is the location of these stations to monuments or historical sites, as their proximity to these sites could increase the number of tourists who are unlikely to be receptive to the survey teams. 

## Data

The primary source of data used is the MTA turnstile transit data that is freely available covering the months of June 2021 through August 2021. Some features of this data include the system location information of each turnstile, their associated linename, as well as the day and time the data was recorded for each turnstile. An additional source of data is the use of google maps to view what is in the immediate vicinity of each station. 

## Algorithms

Data was explored initially using SQLAlchemy queries, then through pandas. The MTA data was sorted first by Control Area(CA), Unit, SCP, Station, and Date_time, with the Date_time group being created during ingestion through a function that also gathered the data into a csv. Duplicates were then dropped based on duplicate counts of entry data, and sorted again by exit data counts to ensure all duplicates were removed. There were instances where the exit and entry data both were being counted in reverse, and cleaned using a function that would also account for extreme values that are outside the norm to create a count of daily entries and exits for each day. The IQR was then found for the exits and used to discover outliers in the data and remove them. 
Data was aggregated by CA, Unit, SCP, and Station with a sum of all the daily entries and exits to be plotted onto a bar chart to determine the 10 most trafficked stations. This data was then used in tandem with the creation of a day_of_week_number column to create and plot the average number of daily exits by day for the 5 most trafficked stations. 

## Tools
   - SQLite and DB Browser for SQLite for initial data exploration and ingestion
   - SQLalchemy for querying the database through Python
   - Numpy and Pandas for exploratory data analysis
   - Matplotlib and Seaborn for plotting and data visualization

## Communication

The data is presented through the ![slides](https://github.com/ajstake/EDA-Project/blob/main/EDA_Final_Presentation.pdf) and ![figures](https://github.com/ajstake/EDA-Project/tree/main/figures) provided
