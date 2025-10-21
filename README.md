# Formative AT4


---
title: "70569"
format: html
---


Question 1 Exploring VCP Data



```{r}
library(dplyr)    
library(readr)    
library(tidyr) 
```




```{r}
# Count unique countries per year
data <- read_csv("~/Downloads/VCI_data_2018-24_by_demographic.csv")
countries_per_year <- data%>%
  group_by(year) %>%   # Group the data by year
  summarise(unique_countries = n_distinct(country)) %>% # Count the number of unique countries in each year
  arrange(desc(unique_countries)) # Arrange in descending order to see the year with most countries first


print(countries_per_year) # Display the results
```

```{r}
# Find the year with the most countries

year_with_most <- countries_per_year %>%
  slice(1)   # Slice(1) takes the first row (which has the highest count due to arrange)


# Print the answer
cat("\nYear with the most countries:", year_with_most$year, 
    "\nNumber of unique countries:", year_with_most$unique_countries, "\n")

# Answer of question 1: 2018 has the most countries, and there are 144 uique countries in that year.
```



Question 2 Aggregate VCP Indicators

```{r}
WB <- read_csv("~/Downloads/WorldBank_socio-economic_indicators_with_metadata.csv")

UNICEF <- read_csv("~/Downloads/who_measles_first_dose_coverage.csv")

Pop_data <- read_csv("~/Downloads/IDB_10-20-2025.csv")
```


```{r}
Pop_data %>%
select(
    country = 1,          # First column: Country/Area Name
    age_group = 3,        # Third column: GROUP
    pop_pct = 5,          # Fifth column: % of Population
    male_pct = 7,         # Seventh column: % of Males
    female_pct = 9        # Ninth column: % of Females
  )
```




```{r}
# According to question1, year 2018 has the most sufficient country coverage with 144 unique countries. We hence selected 2018 as the year to do agggregation for question 2. 


selected_year <- 2018 # Rename 2018 for better understanding

vcp_selected <- data %>%
  filter(year == selected_year) # Filter to selected year only
```



