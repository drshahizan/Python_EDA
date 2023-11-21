## Exploratory Data Analysis of Spotify's Musical Landscape: August-September 2023
### Team Composition
| Name                             | Matric Number |
|----------------------------------|---------------|
| BAKUNGA BRONSON                  | MCS232006     |
| LWANGA AKSAM                     | MCS231016     |
| Ismail Maeen Fateh Allah Yaqot Alawami | MCS221028     |

### Introduction
The project dives into Spotify's extensive song dataset to understand music preferences and characteristics. The goal was to identify patterns, trends, and insights within the musical offerings on Spotify, offering a glimpse into the digital interaction between listeners and music. The analysis aims to answer questions about key and mode prevalence, track valence and energy trends, release patterns, and attributes contributing to a track's 'vibe score'.

### Big Data Tools Selection
Apache Spark, paired with Python's Pandas, Matplotlib, and Seaborn, is the primary tool for managing and visualizing the large volume of data. Dask is also employed for tasks beyond Pandas' capacity but not requiring Spark's full capabilities.

### Data Loading
Essential libraries are installed, and data is sourced from provided Google Drive links for both the Spotify Track and Audio Feature datasets.

### Data Cleaning and Preprocessing
This section describes the preliminary steps taken to prepare the data for analysis, including an acknowledgment of the limitations when considering big data.

### Exploratory Data Analysis
#### Statistical Summary
A statistical overview of the audio features, revealing average scores of danceability, energy, and acousticness.

#### Uncover Patterns and Anomalies
The team discusses correlations found within the dataset, like the inverse relationship between acousticness and energy and the positive correlation between loudness and energy.

#### Focused Anomaly Detection
Insights are shared regarding outliers in the data, specifically in loudness, tempo, and duration, which shed light on the diversity of Spotify's music catalog.
### Analysis Questions
The report has several analysis questions related to Spotify tracks, such as release patterns, trends in valence and energy, prevalence of certain keys or modes, and attributes of tracks in terms of 'vibe score'.

### Conclusion
The dataset suggests that Spotify's recommendation system may prioritize a balance of musical features to cater to a broad audience. It might also consider release timing to maximize engagement, demonstrating the platform's approach to content creation and recommendation.

