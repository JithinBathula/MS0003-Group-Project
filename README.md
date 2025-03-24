# MS0003-Group-Project
import pandas as pd

#Problem statement: Analyse the global and country-level trends in renewable energy adoption over the past two decades and identify the key drivers
#e.g. (GDP, Population, Policy, Comsumption etc) that could influence it.

# Load the dataset
url = "https://github.com/owid/energy-data/raw/master/owid-energy-data.csv"
data = pd.read_csv(url)

# Display the first few rows
print(data.head())

# Check for missing values
print(data.isnull().sum())

# Check column names and metadata
print(data.columns)


columns_of_interest = [
    'year', 'country', 'population', 'gdp',
    'solar_consumption', 'wind_consumption', 'hydro_consumption', 
    'fossil_fuel_consumption' , 'energy_per_capita' , 'energy_per_gdp'
]
subset_data = data[columns_of_interest]

# Display the first few rows of the subset
print(subset_data.head())

# Drop rows with missing values
subset_data = subset_data.dropna()

# Alternatively, fill missing values with zeros
subset_data = subset_data.fillna(0)

print(subset_data)

# Filter for years between 2016 and 2022
subset_data = subset_data[(subset_data['year' ] >= 2016) & (subset_data['year' ] <=2022)]

print(subset_data)

# Display the subsetted data
print(subset_data.head())

#Filter for specific countries
countries_of_interest = ['Russia', 'United States', 'China']
subset_data = subset_data [subset_data['country'].isin(countries_of_interest)]

print(subset_data)

