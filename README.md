

# Musical Hit Trends: A Data Driven Analysis of Popular Songs (1990-2023)

Author: Ke Xu


### Project Overview

**Introduction:** The digital age, marked by the rise of streaming platforms such as Spotify, Apple
Music and YouTube Music, has revolutionized our listening habits. These streaming platforms collect
vast amounts of data on consumer listening behaviors, facilitating personalized music experiences, and
reshaping user engagement with popular songs.



**Motivation:** My profound passion for music and curiosity about the inner workings of Spotify’s
recommendation algorithms drive this research. I hope this project not only fuels my own dedication but
also contribute valuable sights to stakeholders within the music industry



#### Features

- Data Extraction: Utilizes APIs and web scraping to gather music data.

- Data Cleaning and Processing: Prepares data for analysis, ensuring quality and usability.

- Exploratory Data Anlysis: Employes statistical tools and visulizations to uncover trends and patterns.

  

#### Requirements

- Programming Language: Python
- Environment: Python 3.x Environment
- Libraries: pandas, numpy, requests, beautifulsoup, logging, re, json, time, python-dotenv, os, sys, argparse, base64, selenium



#### Installation

To set up this project:

1. files

```markdown
1. Clone the repo: (what if i don't have a repo?)
github / zip
```

2. Install dependencies

```python
pip install -r requirements.txt
```



#### Configuration

I have stored all API keys and secrets in the 'scr/.env' file. Each script will load necessary credentials from this file at runtime. Due to frequent rate limits encountered with Spotify's API, multiple app credentials are stored. Feel free to switch to a different key if the rate limit is hit!

```python
# Enviroment Setup

# SPOTIFY_API_KEY 1,2,3,4,5
# No.1
CLIENT_ID = '85c2ebdb71a54b6a8696e6efa4035d81'
CLIENT_SECRET = '027f493fef5c420d83ac673e35141daf'
...

# Last.fm API
API_KEY = 'b313434440505504bdee7d3138cc6a5f'
SECRECT = '89d39aab6123342c4f0bfe997f8e0d79'
```



#### Usage


HOW TO ACTIVATE SMAPLE MODE

1. For Spotify API - command line argument

```css
python scr/spotify_metadata.py
python scr/spotify_metadata.py --sample
```



2. For Last.fm API

```css
python scr/lastfm_api.py
python scr/lastfm_api.py --sample 5 # display the first 5 sample results
python scr/lastfm_api.py --sample 10 # display the first 10 sample results
```



3. For Grammy Awards Web Scrapping
Since I use the selemiun module for scraping javascript contents, the scraping will be down by using Chrome.


```css
python scr/grammy_web_scraping.py
python scr/grammy_web_scraping.py --sample_mode
```



As I don't know how to only create 5 samples entries in this case, it will return the result of the first grammy page, aka all the awards from 33th grammy awards.



#### Usage Example

1. Spotify API

​	when run command line of "python scr/spotify_metadata.py --sample", you would probably get the results below.

```markdown
# pic 1 
```



1. Last.fm API

```markdown
![Description][./images/last_fm_sample.png]
```



1. Grammy Awards Web Scrapping

```
# pic 3
```



#### Project Structure

```css
FINAL_PROJECT/
├── README.md               
├── data/                    
│   ├──        
│   └── spotify_playlists.csv             
├── scripts/                     # Source code for the project
│   ├── grammy_web_scraping.py     
├   ├── lastfm_api.csv     
			── .env  
│   └── spotify_api.py            
├── output/                  
│   ├── results.csv     
    ── 1_sp_full_data.csv   
    ── 2_lastfm_api_results.csv   
		── 3_grammy_results.csv   
└── requirements.txt         # Required libraries

```


INCLUDE A DIAGRAM TO ILLUSTRATE WORKFLOW





