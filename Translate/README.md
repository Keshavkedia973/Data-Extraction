# Working
Scrapper was last tested on 10th April 2020, Any changes to the site will hamper its working

# Disclaimer
This scraper is provided as a public service because Glasdoor doesn't have an API for reviews. Glassdoor TOS prohibit scraping and I make no representation that your account won't be banned if you use this program. Furthermore, should I be contacted by Glassdoor with a request to remove this repo, I will do so immediately.

It takes about 1.5 seconds per review to scrape. So it will take about 25 minutes to scrape 1,000 reviews, or a little over 4 hours to scrape 10,000 reviews. This script requires patience. 😁

# Installation
First, make sure that you're using Python 3.

1. Clone or download this repository.
2. Run `pip install -r requirements.txt` inside this repo. Consider doing this inside of a Python virtual environment.
3. Install [Chromedriver](http://chromedriver.chromium.org/) in the working directory.
4. Create a `secret.json` file containing the keys `username` and `password` with your Glassdoor login information, or pass those arguments at the command line. Note that the second method is less secure, but in any case you should consider creating a dummy Glassdoor account.

# Usage
```
usage: main.py [-h] [-u URL] [-f FILE] [--headless] [--username USERNAME]
               [-p PASSWORD] [-c CREDENTIALS] [-l LIMIT] [--start_from_url] 
               [--max_date MAX_DATE] [--min_date MIN_DATE]

optional arguments:
  -h, --help                                  show this help message and exit
  -u URL, --url URL                           URL of the company's Glassdoor landing page.
  -f FILE, --file FILE                        Output file.
  --headless                                  Run Chrome in headless mode.
  --username USERNAME                         Email address used to sign in to GD.
  -p PASSWORD, --password PASSWORD            Password to sign in to GD.
  -c CREDENTIALS, --credentials CREDENTIALS   Credentials file
  -l LIMIT, --limit LIMIT                     Max reviews to scrape
  --start_from_url                            Start scraping from the passed URL.
  
  --max_date MAX_DATE                         Latest review date to scrape. Only use this option
                                              with --start_from_url. You also must have sorted
                                              Glassdoor reviews ASCENDING by date.
                                              
  --min_date MIN_DATE                         Earliest review date to scrape. Only use this option
                                              with --start_from_url. You also must have sorted
                                              Glassdoor reviews DESCENDING by date.
```

Run the script as follows, taking Wells Fargo as an example. You can pass `--headless` to prevent the Chrome window from being visible, and the `--limit` option will limit how many reviews get scraped. The`-f` option specifies the output file, which defaults to `glassdoor_reviews.csv`.  


### Run Commands

```
# For getting review of the company "Capgemini Invent"
python main.py -u https://www.glassdoor.co.in/Reviews/Capgemini-Invent-Reviews-E589990.htm -f "output-invent.csv" -l 25 --headless
```