![Screenshot 2024-09-16 171120](https://github.com/user-attachments/assets/bd5971d4-9c38-4467-8fc7-de80a524244c)


# AB-Test-Analysis-on-Vanguard-Clients-Experience
Applying EDA, KPI's, testing hypothesis & making dashboard to uncover the A/B test result and come up with a data driven decision.

## Introduction
In 2017 cusomer experience team at Vanguard launched a new digital interface (UI). Applied it on a group of clients and collect their data for 3 months. In the same time frame they also create a group of clients who is using the traditional process. With this two group of clients they conduct an A/B test. The goal is to: 

- Uncover the test result
- A data driven decision
- Effectiveness of the new UI

## Data Overview
For the project the following datasets were provided:

- Client Details: Demographics like age, gender, and account details
- Client Activity: A detailed trace of client interactions online
- Experiment Group: Control & Test.
Clients interacted with Vanguard’s traditional online process in "Control Group" and who experienced the new UI in "Test Group".

## Data Cleaning & Data Wrangling

- Null values
- Duplicates
- Renaming variable
- Mapping gender & process step column
- Defining 2 dataframe on each group to conduct separate analysis

To analyze the "Error Rate" was a difficult challenge. Whoever come back to a previous step or any previous step or jump any steps need to consider as error. The shift(-1) function helps to define this and then stored it as true or false in a new column.
The process to analyse time spent on each step was another challenge. Overcome through following step:

- First converting date_time column to data type date time
- Sorting them on visit_id and date_time
- Calculating the time spent / difference between one step to another: Groupby visit ID and date_time.diff().dt.total_seconds
- Dropping the 'NaT' for further analyse
- Finding avg time difference for each step
- Converting the timedelta to total seconds and round the values

## Choosen KPI's

- The average duration users spent on each step
- Moving back to a step as an error and that error rate
- The proportion of user who completed all the steps

## EDA & Dashboard

- Number of clients for each group (Control & Test)
- Gender diversity among the group of people
- Client tenure
- Number of clients on their age (a bar chart)
- Average duration for each step and their differences for two group
- The percentage of people for each step who started and then went through step 1, 2, 3 and completed

### Dashboard link: https://public.tableau.com/views/PeojectVanguardABTestingAnalysisDashboard/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

## Hypothesis testing: Statically proved through analysis

- Error rate among different age category has a significant impact from the test user group and control user group.
- Average duration in each step for test group != Average duration in each step for control group. (P value 0.4681, ttest)
- Significant difference between the completion rates among two group. (P-value: 2.3502234547775717e-69, ztest)

### Presentation link: https://docs.google.com/presentation/d/1hg3mwdm7Dr5VSLiVm212w5cxwfJl34DmX0aR6CwwpqE/edit?usp=sharing
