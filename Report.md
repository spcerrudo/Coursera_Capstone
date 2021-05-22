# Capstone Project - The Battle of the Neighborhoods (Week 2)
### Applied Data Science Capstone by IBM/Coursera

## Introduction: Business Problem <a name="introduction"></a>

The COVID pandemic has raged the whole world from its outbreak in January 2020 until today. Due to its nature of transmission and its deadly symptoms, data has been heavily utilized to trace contacts and confirmed cases of people that had contracted the virus in order to reduce its transmission.

From the previous activities, we have utilized Foursquare venue data to get common venues from neighborhoods and cluster these neighborhoods according to their similarity of frequency of specific venues. For this project, we want to look at how common venues in neighborhoods may have affected COVID cases in these neighborhoods through clustering and correlation of population and confirmed covid cases. 

I have taken information in datasets found in the capital region of the Philippines - the National Capital Region or Metro Manila as locals call the region. As a Filipino, I may be able to insert context into the data and further expound correlations in the data analysis.

The results should be able to inform governing bodies in implementing informed quarantine measures and contact tracing to more vulnerable regions.

## Data <a name="data"></a>

To start, neighborhoods in the Philippines are called Barangays and comprise a smaller unit inside a local government unit (LGU) like a city. We'll be grabbing data on the list of barangays in Metro Manila, the population of each barangay (when data is present) and the current confirmed COVID cases as posted by each LGU in Facebook. We'll also be using data on venues closest to these barangays.

1. List of barangays in Metro Manila - https://en.wikipedia.org/wiki/List_of_barangays_of_Metro_Manila

2. List of confirmed COVID cases found in:
	* Public Information Office of the government unit in charge of City (via Facebook)
	* Facebook pages of the current mayor of the government unit
    
    
3. Venues near each barangay via Foursquare API

We scrape the data off the Wikipedia page via pandas. I have personally compiled all of the data on the numbers of covid cases in each barangay. The data is stored in an excel file via Google Drive.

## Methodology <a name="methodology"></a>

From the previous processing, we have gathered the required data: **location of every venue near barangays** within Metro Manila and the **Number of COVID cases** for each barangay. The wikipedia page also provides values on population of each barangay. This will also be used for analysis. However, it is important to note that the data was gathered in 2015 so the **actual percentage ratios of confirmed cases to yet-to-be affected persons will be far** from the results here. For the sake of discussion, we assume that the rate of difference in populations between barangays should be the same for today. The next step would be to process the data to get the frequency of venues in a barangay via one-hot encoding.

After one-hot encoding, we will be utilizing K-means clustering to find commonalities between common venues in barangays and give context towards the covid cases in each barangay. After clustering and encoding, we will be plotting the clusters (via color) and COVID cases/Population (via size) of each barangay and try to correlate the clustering of barangays (based on common venues) and the number of covid cases in that barangay.

After the analysis, we will conclude on how the common venues may have affected the rate of infection in each barangay based on the potential movement of people through these venues.
