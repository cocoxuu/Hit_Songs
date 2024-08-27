## Project Overview

**Introduction:** The digital age, marked by the rise of streaming platforms such as Spotify, Apple
Music and YouTube Music, has revolutionized our listening habits. These streaming platforms collect
vast amounts of data on consumer listening behaviors, facilitating personalized music experiences, and
reshaping user engagement with popular songs.

**Motivation:** My profound passion for music and curiosity about the inner workings of Spotify’s
recommendation algorithms drive this research. I hope this project not only fuels my own dedication but also contribute valuable insights to stakeholders within the music industry.


## Features

- Data Extraction: Utilizes APIs and web scraping to gather music data

- Data Cleaning and Processing: Prepares data for analysis, ensuring quality and usability

- Exploratory Data Anlysis: Employs statistical tools and visulizations to uncover trends and patterns


## Requirements

- **Programming Language:** Python

- **Environment:** Any Python 3.x Environment

- **Libraries:** 

  - pandas==2.1.1

  - numpy==1.24.3

  - requests==2.31.0

  - beautifulsoup4==4.11.1

  - python-dotenv==1.0.1

  - selenium==4.19.0

    
## Installation

To set up this project, follow these steps:

#### 1. Obtain the Project Files

- Download the zip file containing the project
- Extract the zip file to your desired location

#### 2. Install dependencies

- Ensure you have Python 3.9 or higher environment
- Open your command line interfaces, and run the following command to install the required libraries:

```bash
pip install -r requirements.txt
```


## Configuration

To enhance the security of my project and simplify configuration management, I used a ```src/.env``` file to store sensitive information such as API keys. These settings include:

- The id and secret used to access **the Spotify API**

  - ```CLIENT_ID```

  - ```CLIENT_SECRET```

- The api key and secret used to access **the Last.fm API**

  - ```API_KEY```

  - ```SECRET```

Due to frequent rate limits encountered with Spotify's API, several app credentials are stored in the ```.env``` file. Feel free to switch to a different key if the rate limit is hit!

#### How to use 

1. Install the ```python-dotenv``` library

   ```python
   pip install python-dotenv
   ```

2. Create a ```.env``` file in the ```src``` directory and fill in the necessary environment variables

   ```python
   # SPOTIFY_API_KEY
   CLIENT_ID = 'abc123'
   CLIENT_SECRET = 'def456'
   ...
   
   # LAST.FM API KEY
   API_KEY = 'ghi789'
   SECRECT = 'xyz000'
   ```

   3. In your pyton script, use the following code to load the enrvironment variables:

   ```python
   from dotenv import load_dotenv
   import os
   
   load_dotenv()  # This loads the variables from the .env file
   
   client_id = os.getenv('CLIENT_ID') # Load Spotify API's id and secrect
   client_secret = os.getenv('CLIENT_SECRET')
   
   api_key = os.getenv('LASTFM_API_KEY') # Load Last.fm's api key and secret
   secret = os.getenv('LASTFM_SECRECT')
   ```


## Usage

This section outlines how to run the different components of my project to fetch data from Spotify, Last.fm and perform web scraping of the Grammy Awards websites. Each script supports a sample mode that allows me to run the scripts in a demo environment with limited data output.

#### 1. Spotify API Usage

```bash
# Standard Mode
python src/spotify_api.py

# sample Mode
python src/spotify_api.py --sample
```

The output file path is ```./output/spotify_results.csv```. 

#### 2. Last.fm API Usage

```bash
# Standard Mode
python src/lastfm_api.py

# Sample Mode
python src/lastfm_api.py --sample 5 # return the first 5 sample results
python src/lastfm_api.py --sample 10 # return the first 10 sample results
```

The output file path is ```./output/lastfm_results.csv.```

#### 3. Grammy Awards Web Scraping

This script uses Selenium package to scrape content that relies on JavaScript from the Grammy Awards website. It is executed using Chrome.


```bash
# Standard Mode
python src/grammy_web_scraping.py

# Sample Mode
python src/grammy_web_scraping.py --sample
```

The output file path is ```./output/grammy_results.csv```.

**NOTE:** 

1. Due to the nature of API fetching, the sample mode is configured to retrieve data from only one URL, which might contain several dozen entries, rather than specifically the first five entries as is typically expected. 
2. Currently, the sample mode for the Grammy Awards scraping does not support a customizable number of entries. It will always return the results from the first Grammy page.



## Usage Example

#### 1. Spotify API

When you run the command `python src/spotify_api.py --sample`, you will see an output similar to the screenshot below. 

Fig.1 Spotify API Sample Output

![sample-spotify_api](./d-sample output/sample-spotify_api.png)



#### 2. Last.fm API

The following screenshot demonstrates the output from the Last.fm API when executing the command `python src/lastfm_api.py --sample 5`. 

Fig.2 Last.fm API Sample Output

![sample-lastfm_api](./d-sample output/sample-lastfm_api.png)



#### 3. Grammy Awards Web Scrapping

This screenshot is captured after running  ```python src/grammy_web_scraping.py --sample```.

Fig.3 Grammy Awards Web Scraping Output

![sample-grammy_awards](./d-sample output/sample-grammy_awards.png)



## Data Sets

This project utilizes three distinct datasets, each sourced differently to enrich the analysis:

#### 1. Spotify API Results

- **Overview:** This dataset comprises 3,440 records distributed across 21 columns, derived from Spotify's annual top songs playlists
  - Each year's top playlist URLs were manually searched and stored in ```./data/spotify_playlists.csv``` file as the foundation datasets. Occasionally, when playlists from certain years were unavailable, alternative top tracks of the year provided by the user 'Spotifyn' were used.

- **Structure:**
  - **Metadata (8 columns):** Include details such as  ```playlist_name```,   ``track_name``, ```track_id```, ```album_name```, ```released_date```, ```artist_names```, ```popularity```, ```genres```, and ```followers``` 
  - **Audio Features (13 columns):** Covers a range of acoustic attributes for each track, including ```danceability```, ```energy```, ```key```, ```loudness```, ```mode```, ```speechiness```, ```acousticness```, ```instrumentalness```, ```liveness```, ```valence```, ```tempo```, ```duration_ms```, ```time_signature``` 

#### 2. Last.fm API Results

- **Overview:** Contains 750 records across 5 columns, focusing on the top artists from the 15 largest global records music markets
- **Data Points:** Data includes geo-location details for artists prominent in global major music markets, which were chosen based on the [List of Largest Recorded Music Markets](https://en.wikipedia.org/wiki/List_of_largest_recorded_music_markets) web page
  - The countries include the United States, Japan, United Kingdom, Germany, China, France, South Korea, Canada, Brazil, Australia, Italy, Netherlands, Russia, Spain and Mexico

#### 3. Grammy Awards Web Scraping

- **Overview:** This dataset features 3,131 entries with 6 columns, recording the Grammy Awards from 1990 to 2023
- **Details:**

  - **6 Columns:** Include `year`, `award`, `category`, `winner`, `winner_artist`, and `winner_artist_counts`
  - **Award Coverage**: the `award` column encompasses all the awards categories, such as "Record of the Year", "Album of the Year", "Song of the Year", and "Best New Artist", among others
    - For analytical purposes, these have been manually categorized into **11 award types**: record, album, song, artist, producer, songwriter, performance, video, film, composition, and arrangement

## Methodology

Key steps include:

- **Data Collection**: Leveraging APIs and web scraping techniques (e.g., Selenium) to gather JSON responses from Spotify, Last.fm, and the Grammy Awards

- **Data Wrangling**: Cleaning, transforming, and storing data into a CSV format file

- **Data Analysis**: Applying statistical and machine learning techniques to extract patterns, trends, and insights from the music data
