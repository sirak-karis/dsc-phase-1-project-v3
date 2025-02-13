# Aviation Accident Analysis


## Table of Contents

* Overview
* Business Understanding
* Data Understanding and Analsis
* Conclusion

## Overview

Goal: To determine which aircrafts are the lowest risk for purchase for the new business endeavor


## Business Understanding

* Determine which aircrafts based on make and model have had the least number of accidents
   * This will enable the stakeholders make a data driven decsions on the low risk aircrfts to purchase
* Determine which phase of flight experinces the most accidents
* Determine the number of accident all through the years



## Data Understanding and Analysis

 # Read CSV file to Pandas DataFrame

the csv file is uploaded ito Panda DataFrame using path

 ### Checking the tail of the data

confirming that all the data or rows of the CSV have been captured in the DataFrame

 ### Brief description of the data

Information the count of data in each column is seen here.
This assists in knowing the extent of missing vaues in our data

### List of data column names
Easiest way to see the column names; here we can identify the columns that will contribute gratly to our end goal like Make, Madel, Injuries

### Numeric columns description
Gives a brief description of the data

# Data Cleaning

### Checking if there are any duplicate rows
Identify duplite rows with the intent of droppng them - this makes oue dat mre accurate

### Number of duplicated rows
Sum of all the duplicated rows will assist in knowing the expcred number of rows after we drop te duplicates

### Drop the duplicates


### Proof there are no more duplicates
Proof checking that the duplicates have indeed been dropped

## Check for missing values
Identify the columns with missing values

### Count of missing values
Sum of the missing values and arranged in ascending order

missing.sort_values(ascending=False)

### The percentage of the missing data
Assistsin identifying the columns that have the biggest percentage of missing data

### Store the series data in a dataframe
miss_aviation_data = pd.DataFrame({
    "Count": missing.values,
    "%": percentage_missing.values
} , index = missing.index)

# drop values where count is 0


# sort values in descending order


### Drop the columns with more than 31% of missing data
It is difficult to use replace the data or draw conclusons rom columns that have a huge percentage of missin data hece we drop them


### Identify the most important columns
* Make
* Model
* Event.Date
* Purpose.of.flight
* Weather.Conditions
* Broad.face.of.flight
* Total.Fatal.Injuries
* Total.Minor.Injuries
* Total.Serious.Injuries
* Total.Uninjured

### Replace the missing values in column 'Total.Fatal.Injuries'with mean


### Replace the missing values in column 'Total.Minor.Injuries'with mean


### Replace the missing values in column 'Total.Serious.Injuries' with mean


### Replace the missing values in column 'Total.Uninjured' with mean


### Replace the missing values in column 'Make' with mode


### Replace the missing values in column 'Model' with mode


### Replace the missing values in column 'Purpose.of.flight' with mode


### Replace the missing values in column 'Broad.phase.of.flight' with mode


### Replace the missing values in column 'Weather.Condition' with mode


### Unify the date format of 'Event.Date'
Ensuring that the date entries in column Event.Date have the same format

### Replace missing dates
ffill is used becaause the Event..Date has a pattern

### Separate the years from the date/month and create its own column
i order to do a visualisation that showcases the number of accidents over the years, the year is separated from month and date

### confirming the columns to be used for visualization have no missing values


# Outliers
As per my numerical data description the max value for passangers(injurd or uninjured) is 699, while the highest capacity in an aiplane is 853 passangers; hence an outlier analysis won't be necessary.

## Save to CSV
Saving our cleaned DataFrame as csv




## Check for duplicates in unique entry 'Event.Id'
duplicates = Aviation_data_clean[Aviation_data_clean.duplicated(subset=['Event.Id'], keep=False)]

duplicates
### Count of the duplicated data

Aviation_data_clean.duplicated(subset='Event.Id').sum()

### % of duplicates in the column

# % of duplicates in the column
np.round(Aviation_data_clean.duplicated(subset='Event.Id').sum() / len(Aviation_data_clean), 3)

### Get the index of rows with duplicate Event.Id

duplicated_indices = Aviation_data_clean[Aviation_data_clean['Event.Id'].duplicated(keep=False)].index

duplicated_indices

### filter the data

filtered_Aviation_data = Aviation_data_clean.loc[duplicated_indices]
filtered_Aviation_data.shape

filtered_Aviation_data

### Flag duplicates for Manual Review





# Data Visualization

### Plot data of Total.Uninjured by make an Model
### Plot data of proportion of fatalites by phase f flight
### Plot data of number f people involed in an accident through the years



# Recommendations and Conclusion
The model 737 is highly recommended as it has had the highest number of uninjured passengers