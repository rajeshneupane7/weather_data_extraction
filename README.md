HistoricalLocationWeather Class
Overview
The HistoricalLocationWeather class is a custom-built Python solution to retrieve historical weather data for a specified city and date range using the World Weather Online API. This class was developed to work around issues with the worldweatherpy package, which was not functioning as expected.

Features
City-based Historical Weather Retrieval: Fetches historical weather data by city name or postal code.
Date Range Specification: Allows you to specify a start and end date for data collection.
Frequency of Data Points: Supports frequencies of 1, 3, 6, or 12 hours.
Structured Data Output: Returns data in a clean pandas.DataFrame format with key weather metrics.
CSV Export: Optionally saves the data to a CSV file.
Requirements
Python Libraries: This class relies on the following Python packages:
requests
pandas
datetime
json
urllib
os
To install the dependencies, run:

bash
Copy code
pip install requests pandas
API Key
To use this class, you must have an API key from World Weather Online. You can register and obtain a key at World Weather Online.

Class Usage
Arguments
api_key (str): Your API key for World Weather Online.
city (str): The city or postal code for which you want to retrieve weather data.
start_date (str): Start date for data retrieval in 'YYYY-MM-DD' format.
end_date (str): End date for data retrieval in 'YYYY-MM-DD' format.
frequency (int): Frequency of weather data (1, 3, 6, or 12 hours).
verbose (bool, optional): If True, prints status messages. Default is True.
csv_directory (str, optional): Directory path to save the data as a CSV file.
Methods
retrieve_hist_data(): Retrieves historical weather data for the specified city and date range. If csv_directory is provided, it saves the data as a CSV file in the specified location. Returns the data as a pandas.DataFrame.
Example
Here’s an example of how to use this class:

python
Copy code
# Import and instantiate the class
from HistoricalLocationWeather import HistoricalLocationWeather

# Instantiate the weather data retriever
weather_data = HistoricalLocationWeather(
    api_key='your_api_key_here',
    city='76446',
    start_date='2020-01-01',
    end_date='2024-05-31',
    frequency=12,
    verbose=True,
    csv_directory='/path/to/save/csv'
)

# Retrieve the dataset
dataset = weather_data.retrieve_hist_data()
print(dataset.head())
Data Output
The retrieve_hist_data method outputs a pandas.DataFrame containing weather metrics for the specified city and date range, with columns like:

date_time: Combined date and time of the record.
maxtempC, mintempC: Maximum and minimum temperatures.
totalSnow_cm: Total snowfall in cm.
sunHour: Hours of sunlight.
uvIndex: UV index rating.
moon_illumination, moonrise, moonset, sunrise, sunset: Astronomy data.
Various weather metrics like tempC, humidity, precipMM, windspeedKmph, etc.
If csv_directory is specified, a CSV file named <city>.csv will be saved with this data.

Error Handling
The class handles various error scenarios, including:

Mismatched row lengths in dataframes.
Missing columns like date or time.
Invalid API keys or missing values.
Notes
This class was created to provide reliable access to historical weather data from the World Weather Online API, bypassing issues encountered with the worldweatherpy package.

