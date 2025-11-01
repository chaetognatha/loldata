The objective is to prepare a dataset for games in 2025 on EUW

Will use pixi for environment

## Method

encrypted player ids are retrieved by querying latest game sessions by
server instance

we retrieve data from the euw endpoint and prepare a large set of ids in
raw_league.csv

the rate limits make it unfeasible to query all entries in the dataset
so we first make a unique set of encrypted player uuids and then select
a random sample of n eg 3000 players

these uuids are used to fetch a list of n (3) games, a set of 3
should be sufficient replication in the dataset, there is a parameter
filter that prohibits games from before the start of 2025 from being returned

finally, for each players 3 games, we query the game objects that are
written to games.json

games.json can then be flattened and parsed into a dataframe for further
analysis

EDA reveals there are large differences in popularity of champions so I 
decided to scale values by the relative number of games played on champions
and then average

## Data availability

you can download the data from:
https://drive.google.com/drive/folders/1-21tjIiBd_8ecTudYdSk0WczH2XkH1Cg?usp=sharing