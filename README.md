# Puzzles

## The Fake Coin
Twelve coins, one fake. Real coins have unknown but uniform weights; fake coin weighs different. One scale, what is the best stragety using the scale minimum number of times?

Source: https://www.folj.com/puzzles/very-difficult-analytical-puzzles.htm


## Blue Eyes
100 blue-eyed and 100 brown-eyed logicians on an island without reflection and commuincation is forbidden. Anyone who figures out their own eye color is allowed to leave on on a ferry that comes once a day. Everyone can see everyone else's eyes colors, and they can see who leaves on the ferry.  On day 1, oracle arrives and announce that they see (at least one pair of) blue eyes, and the game commences.

Who leaves and on which day?

**Bonus question:** This is probably much harder than the question itself. What is the relevance of the orcale? i.e., "Everyone can already see that the are blue eyes".

Source: https://xkcd.com/blue_eyes.html


# Prinsoner guesses own number 

Source missing.

There are 100 prinsoners, and they will go in a room and each will put on a hat randomly numbered 1 to 100 (with duplicates). They will be able to see other prisoners' hats, but cannot communicate. If any prisoner guesses their own hat's number, everyone goes free; everyone is executed if no one guesses correctly. They can convene and come up with a strategy prior to the game. What is the best strategy to survive?

<details>
  <summary>Solution and explaination</summary>

  Everyone is assigned a different number `x` to memorize, from 1 to 100. The prisoner will guess `1 + (x - (sum(rest)) mod 100)` when it's their turn, where `sum(rest)` is the sum of all numbers they see. Exactly one prisoner will guess right.

  In more layperson terms, subtract sum of all numbers observed plus `x` from 10,000. The last two digits plus one is their guess.

  That is a concise way to describe a solution. More intutively, each prinsoer will assume a different modulo-100 remainder `r` of the total sum of numbers (including thier own) - 100. Subtract 100 because we want the numbers to be 0 to 99 to work with modular arithmatics (i.e. subtract 1 from each number). Exactly one prisoner will have the correct assumption (since there are 100 different remainders). Given the correct remainder, they can compute their own number via solving the modular arithmatic equation `(sum(rest) + t - 100) mod 100 = r`, where `t` is their acutal number on their hat. Note that `-100` can be omitted because that's 0 mod 100. But that is equivalent to computing the first formula given above where `x = 100 - r`, and hence the concise solution.
</details>
