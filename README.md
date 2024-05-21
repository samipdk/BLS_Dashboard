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

# Data Transformation:

get_custom_name(series_id): This function maps series IDs to human-readable names for easier interpretation of the data.
The data is pivoted to create a table where each row corresponds to a time period, and each column corresponds to a specific economic indicator.
Data Visualization:

The correlation matrix of the economic indicators is computed and visualized using a heatmap, helping to identify relationships between different variables.
The correlation between National Employment and other statistics is specifically analyzed.

# Developing and launching an Interactive Dashboard:

A Dash web application is created to provide an interactive interface for exploring the data.
The dashboard allows users to select a year and view line charts of the Consumer Price Index (CPI) and National Employment data for that year.
The layout and callbacks in Dash ensure that the visualizations update dynamically based on user input.
Code Breakdown
Imports and Setup:

pandas, seaborn, and matplotlib are used for data manipulation and visualization.
requests is used to make API calls.
dash, dcc, and html are used to build the interactive web application.
Fetching Data:

python
Copy code
def fetch_bls_data():
    ...
Custom Series Names:

python
Copy code
def get_custom_name(series_id):
    ...
Correlation Heatmap:

python
Copy code
df = fetch_bls_data()
df['value'] = pd.to_numeric(df['value'], errors='coerce')
pivot_df = df.pivot_table(index=['year', 'period'], columns='series_title', values='value')
correlation_matrix = pivot_df.corr()
plt.figure(figsize=(12, 10))
heatmap = sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', linewidths=0.5)
heatmap.set_title('Correlation Heatmap', fontdict={'fontsize': 18}, pad=16)
plt.show()
Dash Application:

python
Copy code
import pandas as pd
import dash
from dash import dcc, html, Input, Output
import plotly.express as px

app = dash.Dash(__name__)
app.layout = html.Div([
    html.H1("U.S. Bureau of Labour Statistics", style={'textAlign':'center'}),
    html.Div([
        html.Div([
            html.Label("Year"),
            dcc.Dropdown(
                id='year-dropdown',
                options=[{'label': title, 'value': title} for title in df['year'].unique()],
                value=df['year'].unique()[0],
                style={'width': '300px'}
            )
        ], style={'display': 'inline-block', 'verticalAlign': 'top', 'marginRight': '10px'}),
    ]),
    html.Div(id='graphs', style={'display': 'flex', 'justify-content': 'space-around', 'flexWrap': 'wrap'})
])
@app.callback(
    Output('graphs', 'children'),
    [Input('year-dropdown', 'value')]
)
def update_graphs(selected_year):
    ...
if __name__ == '__main__':
    app.run_server(host='localhost', port=8050, debug=True, use_reloader=False, jupyter_mode='external')
This code provides a comprehensive approach to fetching, analyzing, and visualizing BLS data, making it accessible and interpretable for users through an interactive dashboard.
