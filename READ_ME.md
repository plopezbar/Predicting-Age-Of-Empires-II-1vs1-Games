# IRONHACK FINAL PROJECT - DATA ANALYTICS - DEC19 - PAU LÓPEZ - "Predicting Age Of Empires II 1vs1 Games" 
## Summary:

In this binary classification project we are going to predict the winner of 1v1 matches of the famous game Age of Empires II. We will try to predict which player will win the game through different approaches and models, we will also study how models evolve as games progress. This is a specific `machine learning` problem, in wich we'll deal with `classification` issues applied to `time series`.

**Age of Empires II (Contextualization):**

Age of Empires II is a real-time strategy video game developed by Ensemble Studios and published by Microsoft. Released in 1999, it is the second game in the Age of Empires series. The game won multiple awards and is today considered a classic of its type and one of the greatest games ever made, having had a significant impact on future games in its genre. 

In April 2013, Age of Empires II: HD Edition was released on the Steam digital distribution platform for Microsoft Windows. The HD Edition includes the original game and the expansion The Conquerors, as well as updated graphics for high-resolution displays. Age of Empires II: Definitive Edition, a definitive remaster, was released in November 2019. <ins>The data in our study comes from the 2013 version.</ins>

The game focuses on building towns, gathering resources, and creating armies to defeat opponents. Players conquer rival towns and empires as they advance through four "Ages": the Dark Age, the Feudal Age, the Castle Age and the Imperial Age. Advancing to a new Age unlocks new units, structures, and technologies, but players must first build certain buildings from their current age and then pay a sum of resources.

Resources can be used to train units, construct buildings, and research technologies, among other things, for example, players can research better armour for infantry units.

- Wikipedia game page: https://en.wikipedia.org/wiki/Age_of_Empires_II
- Official game page: https://www.ageofempires.com/games/aoeiide/
- Youtube channel about the maths in the game: https://www.youtube.com/channel/UChzLZJo-SxuPHz-oYKAIC_g

**Dataset Description:**

Our dataset, having 1.808.535 rows and 67 columns, is a time series collection of more than 2,200 'one-versus-one' games whose instances collect atribute values for each timestamp in the game. Each row represents a time point for a concret game, these timestamps were recorded at 3 second intervals, which means that if we have 3 rows we have data for a 9 second time interval.

*Data Source:* https://github.com/Macuyiko/aoe2predict

**Features Description:**

Most features are set as a difference between both players, for example instead of having two columns, one saying that player 1 has three castles and player 2 has one castle, we have one column saying that the difference of castles between both players is 2, being positive if it's a favorable difference for player 1 and negative otherwise. The list of features is as follows:


- `match_id`: Match (game) identifier. 

- `current_time`: Time elapsed since the start of the game (milliseconds).

- columns with `diff_units` prefix: Difference of units between both players at a specific time in the game. Units can be military, like infantry and cavalry units (soldiers) or civilian, like farmers and gold miners units (workers).

- columns with `diff_current_resources` prefix: Difference of available resources between both players at a specific time in the game. There are 4 types of resources in the game: food, wood, gold and stone.

- columns with `diff_total_resources` prefix: Cumulative difference in resources between both players at a certain time in the game.

- columns with `diff_population` prefix: Difference of population between both players at a specific time in the game. There are 4 types of population: military, civilian, total (military+civilian) and headroom (maximum population capacity - total).

- `diff_percent_explored`: Difference of map exploration between both players at a specific time in the game.

- `diff_units_queued`: Difference of civilian units queued to be produced between both players at a specific time in the game.

- `diff_diff_units_training`: Difference of military units queued to be produced between both players at a specific time in the game.

- `diff_castles`: Difference of castles between both players at a specific time in the game.

- `diff_relics`: Difference of captured relics between both players at a specific time in the game.

- columns with `diff_worth` prefix: Difference of worth spent, worth destroyed and worth lost between both players at a specific time in the game.

- columns with `diff_score` prefix: Difference of scores between both players at a specific time in the game. There are 4 types of scoring: economy, technology, society and total.
 
- `diff_kills`: Cumulative difference of military units killed between both players at a specific time in the game.

- `diff_razes`: Cumulative difference of buldings razed between both players at a specific time in the game.

- `diff_rating`:Elo difference between both players. Elo rating system: https://en.wikipedia.org/wiki/Elo_rating_system

- **`player_1_wins`**: 1 if player 1 won the game, 0 otherwise.
