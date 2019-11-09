# Web scrape to [flashcore](flashscore.com)

## Used technologies

- [Selenium](https://selenium-python.readthedocs.io/)
- [TinyDB](https://tinydb.readthedocs.io/en/latest/)

## How to use 

### Scraping

```python
from flashscore_scraping import Scraping
from selenium import webdriver

# Scraping startup
scraping = Scraping()

# Selenium startup
driver = webdriver.Chrome('chromedriver')

# get all matches of Brazilian Championship Serie A 2019
scraping.collect(driver, 'brazil', 'serie-a', 2019)

# get all LaLiga matches from 2012 until 2019
scraping.collect(driver, 'spain', 'laliga', 2018, 2012)

driver.quit()
```

### Statistics

```python
from flashscore_scraping import Statistics

# Statistics startup
statistics = Statistics()

# get all matches where the Atletico MG win in 2018
statistics.get_win_matches('brazil', 'serie-a', 'Atletico-MG', 2018)

# get all matches where the Atletico MG lost between 2014 and 2016
statistics.get_lose_matches('brazil', 'serie-a', 'Atletico-MG', 2016, 2014)

# get all matches where the Atletico MG draw in 2015
statistics.get_draw_matches('brazil', 'serie-a', 'Atletico-MG', 2015)

# get all possession ball of Bayern Munich in 2019
statistics.get_statistic_by_team('germany', 'bundesliga', 'Bayern Munich', statistic, 2017)

# get all the names of teams that participated in the Premier League in 2019
statistics.get_teams('england', 'premier-league', 2013)
```

## Documentation

> path: by default, the path is initialized with './data', but the path can be changed to your preferred path.

> driver: Selenium driver that must be initialized before as done [here](https://selenium-python.readthedocs.io/getting-started.html)

> country: country name where the championship is held

> championship: championship name

> team: team name

> statistic: one this statistics

    ============================== STATISTICS ===============================
    "ball_possession",  "goal_attempts", "shots_on_goal", "shots_off_goal", 
    "blocked_shots",    "free_kicks",    "corner_kicks",  "offsides", 
    "total_passes",     "fouls",         "yellow_cards",  "goalkeeper_saves", 
    "completed_passes", "tackles",       "attacks",       "dangerous_attacks" 
    =========================================================================

> last_year: championship year

> first_year: required only if you need matches within a given time interval


### Scraping

```python
Scraping(path)

collect(driver, country, championship, last_year, first_year)
```

### Statistics

```python
Statistics(path)

get_teams(country, championship, last_year, first_year)

get_win_matches(country, championship, team, last_year, first_year)

get_lose_matches(country, championship, team, last_year, first_year)

get_draw_matches(country, championship, team, last_year, first_year)

get_statistic_by_team(country, championship, team, statistic, last_year, first_year)
```