# Lichess-Chess.com-Data-management

The goal of this project is to create a dataset with data obtained by web scraping and APIs from two different sources, clean the data and store it on a DBSM. <br>
In this particular case I crawled data from Lichess and Chess.com, stored it on MongoDB and analysed it with its analytics. 

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
Lichess' API provided a unique JSON containing the queried user's public information and data about his chess variants performances, alike Chess.com which provided two separated documents. 


The readme is work in progress, I'll complete it soon! :)
