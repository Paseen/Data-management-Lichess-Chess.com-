# Lichess-Chess.com-Data-management

The goal of this project is to create a dataset with data obtained by web scraping and APIs from two different sources, clean the data and store it on a DBSM. <br>
In this particular case I crawled data from Lichess and Chess.com, stored it on MongoDB and analysed it with its analytics. I also tried to find the users who played on both platforms and create a unique JSON joining the informations from both websites.    

# Data acquisition
## Web scraping
|Lichess    | N. usernames |
|--------------|----|
  | "2021 Winter Marathon" Tournament<sup>1</sup>     | 28.480            |
|Leaderboards    |2.600           |

|Chess.com     | N. usernames |
|--------------|----|
| 2022 Chess.com Daily Chess Championship<sup>2</sup>     |32.819             |
|Leaderboards    |30.000           |


31.325 Lichess' usernames were extracted from a downloaded JSON of “2021 Spring Marathon” Tournament<sup>3</sup>

$^1$ https://lichess.org/tournament/winter21   <br>
$^2$ https://www.chess.com/tournament/2022-chess-com-daily-chess-championship  <br>
<sup>3</sup> https://lichess.org/tournament/spring21

## APIs
Lichess' API provided a unique JSON containing the queried user's public information and data about his performances in the chess variants he played, alike Chess.com which provided two separated documents. 

## Ground truth for name matching

As ground truth for name matching between Lichess and Chess.com users I used a dataset containing name, title, country, rating in that country, FIDE rating, age k-factor of 191.971 FIDE players downloaded from Kaggle<sup>4</sup> <br>

To be sure that two people that shared the same name were the same person FIDE rating and the player's title, when present, were used to be sure that the match was correct. Unfortunately the majority of people didn't share or didn't have this informations in their profile, so the total number of matches was 2242.  
<br> 
FuzzyWuzzy function was used for name matching, since it was not influenced by the order and the caps of the strings; it returned a level of similarity between strings in the 0-100 interval, and the treshold value for a match was set to 90. <br>
<sup>4</sup> https://www.kaggle.com/datasets/deepcontractor/international-chess-statistics-2022

## Data cleaning and integration

Before integrating the documents from the two platforms it was necessary to perform those steps:
-	Rename the keys of the two different platform’s JSONs in order for them to match
-	Unify for each key the set of possible values that they can hold 
-	Create a unique JSON's structure: it was decided to adapt the Chess.com JSON's structure to the Lichess one 

After that it was possible to join the JSON documents.

## Data modelling

Since the data didn't have a precise schema it was decided to use MongoDB, a NoSQL DBSM, to store it and analyse the data using its analytical tools.    
<br>
- For a more in-depth analysis of this work consult the [Report](https://github.com/Paseen/Lichess-Chess.com-Data-management/blob/main/Report%20data%20management.pptx)
