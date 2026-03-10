# Rating research

## Elo
* Not a great option because of a long calibration time and a larger sample size of matches to accurately assess skill
* No assessment of rating uncertainty or rating decay
* Implementation is really simple, two formulas

## Glicko-2
* Good for 1v1 format games
* Incorporates rating uncertanty, which is good for new players and returning players
* Uncertainty increases based on last play time, which is a good thing
* Harder to implement manually but there are good Python libraries for it (https://pypi.org/project/glicko2)

## Trueskill
* Good for 1v1 format games and team format games
* Incorporates rating uncertainty well, and is quite accurate
* Great for new players because the model is designed to get an accurate rating in as few games as possible
* Likely will have to implement hidden MMR
* A good library for this is https://trueskill.org

## Best option
Trueskill. It is most ideal for the number of people in the community and scales well for larger groups. Also, it's built for many game formats (1v1, NvN, NvNvN, etc.) and takes far fewer games to compute an accurate rating for players. Implementation will be done via a python library.

### Updates
* Users will have to store TrueSkill constants (mu -> rating, sigma -> confidence, last time played)
* We will need to use established default constants for these values
* Displaying regular MMR based on confidence (iirc it was something like mu - 2 sigma because rating is mu +- 2 sigma)
* On the end of a game, values need to be updated of course.
* (Maybe) check if a game is fair using the Trueskill "match quality" valuation

## References
https://en.wikipedia.org/wiki/TrueSkill
https://en.wikipedia.org/wiki/Glicko_rating_system
https://pypi.org/project/glicko2
https://trueskill.org