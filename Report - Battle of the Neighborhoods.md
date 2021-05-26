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

## Results and Discussion<a name="analysis"></a>

![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/111pop.png?raw=true)

From the plot, we can see three major clusters (Blue, Orange and Red). Red (Cluster 0.0) is the cluster that contained the most barangays. Blue (Cluster 2.0) comes second and Orange (Cluster 4.0) comes third. From the summary of mean values (below), we can see that the blue cluster gets a higher average population. Red cluster receives the second highest mean population and orange cluster receives the third highest mean population.

Further analysis will be described by looking at the common venues for the clusters

![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/01st.jpg?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/02nd.jpg?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/03rd.jpg?raw=true)

The red cluster (cluster 0.0) shows a variety of restaurants as its common venues. We also have bars, bakeries and coffee shops. This cluster happen to contain barangays that are comprised of residential areas. Due to the nature of roadbuilding in Metro Manila, most of these barangays will not be travelled by a person unless he/she lives and/or visits someone in that area.

![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/21st.jpg?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/22nd.jpg?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/23rd.jpg?raw=true)

The blue cluster (cluster 2.0) shows a spread of common venues. We can see fast food restaurants, electronics stores, gyms, pharmacies, and some niche areas like zoo exhibits. The barangays in the blue cluster happens to be areas that are frequented or commonly visited by people outside that barangay. Most of the venues there have the cheapest rates in some commodities or the area happens to house multiple commercial establishments in a common area inside the barangay.

![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/41st.jpg?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/42nd.jpg?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/43rd.jpg?raw=true)

The orange cluster (cluster 4.0) shows a larger spread of common venues compared to the blue cluster. However, one thing in common in these barangays is the frequency of convenience stores in these areas. Most of the barangays in these clusters happen to be very far to the city center to frequent the nearest mall or happen to contain transportation routes that are commonly frequented by people that wish to travel to another place.

![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/111.png?raw=true)
![alt text](https://github.com/spcerrudo/Coursera_Capstone/blob/main/ff.png?raw=true)
From the plot, we can see that the barangays with higher covid cases are situated near the city center. It also happens that these barangays are also densely populated areas as well. We observe a large distribution of total covid cases in the orange cluster. There is a disparity in total covid cases in the blue cluster. For the red cluster, most of the barangays have a sharp distribution (or small deviation) in covid cases.

We now look at summary of averages below. Looking at the top three clusters (0.0/Red, 2.0/Blue, 4.0/Orange), we can see the respective covid cases and percentage affected. We can see that the red cluster has the highest percentage of infected, with orange having the second highest and blue having the third highest. Looking at the data regarding common venues in the red cluster, we can correlate how these common venues (restaurants) may have been agents of transmission for locals.

Taking into account the quarantine measures applied during the pandemic, we should expect that transportation routes should be less frequented compared to pre-pandemic times. As the red cluster contains residential areas, we should expect high covid cases in those barangays.

Comparing the small number of covid cases in the orange and red clusters, we can see that barangays in the orange clusters has a higher tally of cases. While transporation routes are less frequented, the transportation issue of Metro Manila may have affected transmission in these areas.

While blue areas are commonly frequented by people from other barangays, the controlled movement of population may have contributed to the smaller covid cases of barangays in the blue cluster compared to barangays in red cluster. However, it is still important to note that the common venues in blue clusters are fast food restaurants and shopping malls. These areas may have been agents of transmission and should be recommended to be avoided as much as possible.

## Conclusion <a name="conclusion"></a>

The objective of this study is to determine a correlation between common venues in a neighborhood and the total covid cases in the neighborhood. From context and data averages, we observe a correlation in the two data. While stakeholders may now have an informed decision in further restrictions, more data may be utilized such as the rate of change of cases and travel routes of workers to complement the analysis and further fortify these claims. Nevertheless, we were able to find clusters and/or neighborhoods that may be high-risk such as barangays in Red and Blue clusters.
