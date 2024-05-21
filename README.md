# BLS Dashboard

The goal of this project is to analyze and visualize employment and economic data from the U.S. Bureau of Labor Statistics (BLS). This analysis involves fetching data from the BLS API, transforming it into a usable format, and creating visual representations to identify trends and correlations. Specifically, the project aims to:

Fetch various time series data from the BLS API.
Transform and clean the data for analysis.
Create visualizations to explore correlations between National Employment data and other economic indicators.
Develop an interactive dashboard for users to visualize and explore the data dynamically.


# Code Functionality
The provided code performs the following tasks:

# Data Fetching:

fetch_bls_data(): This function sends a POST request to the BLS API to fetch time series data for specific economic indicators. It uses a predefined set of series IDs and requests data from 2022 to 2024.
The response from the API is parsed to extract relevant data points and stored in a pandas DataFrame.

![Data api code](https://github.com/samipdk/BLS_Dashboard/assets/137905918/29d222ad-6491-4998-ab1c-77b95fd73eac)

# Analyzing the data for visualization:

get_custom_name(series_id): This function maps series IDs to human-readable names for easier interpretation of the data.
The data is pivoted to create a table where each row corresponds to a time period, and each column corresponds to a specific economic indicator.



# Data Visualization:

The correlation matrix of the economic indicators is computed and visualized using a heatmap, helping to identify relationships between different variables.
The correlation between National Employment and other statistics is specifically analyzed.
![Correlation heat map](https://github.com/samipdk/BLS_Dashboard/assets/137905918/298ab9e3-5a81-45cd-a4b4-94b20e2f2e5c)

# Design the App using Dash, Plotly:

A Dash web application is created to provide an interactive interface for exploring the data.
The dashboard allows users to select a year and view line charts of the Consumer Price Index (CPI) and National Employment data for that year.
The layout and callbacks in Dash ensure that the visualizations update dynamically based on user input.
Code Breakdown
![App code](https://github.com/samipdk/BLS_Dashboard/assets/137905918/67675357-30ba-4c43-9183-a76708fdfb3d)

# Launch the App :
Run the code which will launch the app:


