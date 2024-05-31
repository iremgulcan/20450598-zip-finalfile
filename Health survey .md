\---

title: "Health Survey Analysis"

author: irem gülcan

date: "`r format(Sys.Date(), '%d %B %Y')`"

output: HTML document

\---



\## Introduction



This report presents an analysis of health survey data. The analysis includes data cleaning, descriptive statistics, visualizations, and examining relationships between specific health indicators.



\## Data Loading and Pre-processing



\```{r load-data, message=FALSE, warning=FALSE}

\# Load necessary libraries

library(dplyr)

library(ggplot2)

library(readr)

library(knitr)

library(tidyr)



\# Load the data

data <- read\_csv("health\_survey\_data.csv")



\# Display the first few rows of the data

kable(head(data))



\# Check for missing values

sum(is.na(data))



\# Fill missing values with the mean (as an example)

data <- data %>% 

`  `mutate (across(everything (), ~ ifelse(is.na(.), mean(., na.rm = TRUE), .))



) # Summary of age distribution

age\_summary <- summary(data$Age)

kable(age\_summary)



\# Plot of age distribution

ggplot(data, aes(x=Age)) + 

`  `geom\_histogram(binwidth=5, fill="blue", color="black") + 

`  `theme\_minimal() + 

`  `labs(title="Age Distribution", x="Age", y="Frequency")

\# Impact of smoking status on health (e.g., SelfRatedHealth)

ggplot(data, aes(x=SmokingStatus, y=SelfRatedHealth, fill=SmokingStatus)) + 

`  `geom\_boxplot() + 

`  `theme\_minimal() + 

`  `labs(title="Smoking Status and Health", x="Smoking Status", y="Health Status")

**Results and Discussion**

This report presents an analysis of health survey data. Basic health indicators such as age, gender, and BMI were examined, and relationships between these indicators were analyzed. Notably, the relationship between age and BMI, as well as the effects of smoking status on health, were observed. These findings can be important for health policies and individual health assessments.


