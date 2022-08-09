# World_Weather_Analysis

The aim of this project is to use the Open Weather and Google API along jupyter notebook to create a travel itinerary from 4 chosen locations that meet the desired temperature criteria.

The first dataset consists of 2000 randomly generated latitude and longitude coordinates which are then used to locate the city  closest to them. Then, the current weather for each city is extracted from the OpenWeather API.

Using a user input for the maximum and minimum desired temperatures, the dataset is reduced to only the cities with a temperature within that range. Then using the dataset's latitude and longitude for each city entry, we find the nearest hotel.

The Google maps API is used to create a map with a marker layer that shows the hotel name, city, country and its current weather for each of the filtered dataset's entries.

Finally, 4 locations within the same country from this dataset are used to generate a travel itinerary using the Google Directions API.

## Overview of Project

!["Vacation_Spots"](/Vacation_Search/WeatherPy_vacation_map.png)

The image from the gmaps API shows all the hotels at the cities that have a temperature within the chosen range of 70 to 80 °F.

Each of the markers in this image contains the Hotel Name, City, Country and the description and temperature of the current weather.

!["Vacation_Itinerary"](/Vacation_Itinerary/WeatherPy_travel_map_markers.png)

For this project, China was chosen as the destination country; after picking 4 cities in China we obtained this travel route.

### Purpose

The purpose of this project is to use the available APIs to create a tailored travel itinerary for a customer according to the weather they'd prefer when travelling.

## Analysis

!["City_DataFrame"](/Images/City_Data_DF.png)

This is the first dataframe which consists of the City that's closes to the random generated coordinates, the country code, the latitude and longitude from the city which were obtained from the OpenWeather API response as well as weather parameters such as humidity, cloudiness, wind speed and a brief description.

By choosing a desired temperature range, this dataset was reduced into the following:

!["Preferred_Cities_DataFrame"](/Images/Preferred_Cities_DF.png)

This dataframe contains the same information as the Citiy_DataFrame for the cities that have a max temperature between 70 and 80°F. With this information we could then use the Places Google API to obtain the closest hotel to the registered latitude and longitude, and append this information to the Preffered_Cities_DataFrame. After iterating through all the entries, the resulting dataset is the following:

!["Hotel_DataFrame"](/Images/Hotel_DF.png)

This dataframe contains the additional column of the chosen Hotel for each city.

## Results

!["Itinerary_DF"](/Images/Itinerary_DF.png)

The Hotel_DataFrame was filtered according to the country codes that had 4 or more cities in them, this is done because we need a starting/ending location and 3 places to visit. China was chosen as the destination country. Listed in order, the cities in the itinerary are the following:
1. Start : chaozhou
2. First stop : rucheng
3. Second stop : jiancheng
4. Third stop : huicheng
5. End : chaozhou

Using the Directions Google API we received the following route:

!["Travel_route"](/Vacation_Itinerary/WeatherPy_travel_map.png)

### Further implementations

This project could use more criterias such as humidity and cloudiness to narrow down the preferred cities dataframe since we also have that information. Another idea is to let the user choose how many stops they'd like to make and filter the DataSet to show only the countries with an equal or greater amount of stops.

When choosing the travel destination, we could also add a method that uses either the Google Directions API response that has the total distance, or the haversine formula, to determine which cities are the furthest and nearest to the starting one, and from them to let the program create a route automatically.