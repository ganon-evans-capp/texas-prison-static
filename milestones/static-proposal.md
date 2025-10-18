# Ganon Evans

## Description

Texas has one of the largest prison systems in the country. It's incarceration rate of 751 per 100,000 people is higher than the US's already-high average compared to the rest of the world. Texas prisons have experienced several problems in recent years, including overcrowding, deaths during heat waves, and increased misconduct by staff.

Using the state's robust data by inmate, I wanted to do an overview of the demographics of the Texas prison system and some comparisons among things like gender, charge, sentence time, and opportunity for parole. 

I wanted to bring in facility data like deaths and staff counts to see if any interesting relationships arose among outcomes.

## Data Sources

### Data Source 1: August 2025 Inmate Data, State of Texas

URL: [{URL}](https://data.texas.gov/dataset/High-Value-Dataset-August-2025/9b32-yeu6/about_data)

Size: 139,211 rows, 20 columns

The file includes every single inmate in the Texas prison system, including their charge and sentence as well as details about their parole and timeline (i.e, when they were arrested and how long has been served, etc.). I want to start with some basic visualizations representing who is in the system, then see if there's other oddities that arise and explore those. 

### Data Source 2: UCLA Law Behind Bars Data Project

URL: [{URL}](https://github.com/uclalawcovid19behindbars/data/tree/master/latest-data)

Size: 2,768 rows, 31 columns

This data includes facility-wide details like death counts as well as staff and admin numbers. I can match the prison data by name to the Texas file I have. This file also includes geographic coordinates for the prison, which makes a potential map across Texas a bit easier. 

## Questions

{Numbered list of questions for course staff, if any.}

1. I'm approaching the data from a naive angle to just see what's there at first. Do you think I should have a more concrete goal from the start, or is that something I can focus on depending on what I find when exploring the data?