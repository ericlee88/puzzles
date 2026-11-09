# Puzzles

## The Fake Coin
Twelve coins, one fake. Real coins have unknown but uniform weights; fake coin weighs different. One scale, what is the best stragety using the scale minimum number of times?

Source: https://www.folj.com/puzzles/very-difficult-analytical-puzzles.htm


## Blue Eyes
100 blue-eyed and 100 brown-eyed logicians on an island without reflection and commuincation is forbidden. Anyone who figures out their own eye color is allowed to leave on on a ferry that comes once a day. Everyone can see everyone else's eyes colors, and they can see who leaves on the ferry.  On day 1, oracle arrives and announce that they see (at least one pair of) blue eyes, and the game commences.

Who leaves and on which day?

**Bonus question:** This is probably much harder than the question itself. What is the relevance of the orcale? i.e., "But everyone can already see that there are blue eyes".

Source: https://xkcd.com/blue_eyes.html


# Prinsoner guesses own number 

Source missing.

There are 100 prisoners, and they will go in a room and each will put on a hat randomly numbered 1 to 100 (with duplicates). They will be able to see other prisoners' hats, but cannot communicate. If any prisoner guesses their own hat's number, everyone goes free; everyone is executed if no one guesses correctly. They can convene and come up with a strategy prior to the game. What is the best strategy to survive?

<details>
  <summary>Solution and explaination</summary>

  Everyone is assigned a different number `x` to memorize, from 1 to 100. The prisoner will guess `1 + (x - (sum(rest)) mod 100)` when it's their turn, where `sum(rest)` is the sum of all numbers they see. Exactly one prisoner will guess right.

  In more layperson terms, subtract sum of all numbers observed plus `x` from 10,000. The last two digits plus one is their guess.

  That is a concise way to describe a solution. More intutively, each prinsoer will assume a different modulo-100 remainder `r` of the total sum of numbers (including thier own) - 100. Subtract 100 because we want the numbers to be 0 to 99 to work with modular arithmatics (i.e. subtract 1 from each number). Exactly one prisoner will have the correct assumption (since there are 100 different remainders). Given the correct remainder, they can compute their own number via solving the modular arithmatic equation `(sum(rest) + t - 100) mod 100 = r`, where `t` is their acutal number on their hat. Note that `-100` can be omitted because that's 0 mod 100. But that is equivalent to computing the first formula given above where `x = 100 - r`, and hence the concise solution.
</details>


## 100 Prisoners and 100 Boxes

There are 100 prisoners and 100 boxes. Each box contains one prisoner's unique number from 1 to 100, shuffled randomly. Each prisoner enters the room alone and may open up to 50 boxes to find their own number. After each search, the boxes are closed again without changing their contents. The prisoners cannot communicate once the search begins, but they may agree on a strategy beforehand.

If every prisoner finds their number, everyone goes free. Otherwise, everyone is executed. What is the best strategy?

<details>
  <summary>Solution and explanation</summary>

  Each prisoner starts by opening the box with their own number on it. If it contains a different number, they open the box with that number on it, and continue this way, following the numbers from box to box. They stop if they find their own number or have opened 50 boxes.

  The shuffled contents form a permutation, which can be split into cycles. Following the boxes takes each prisoner around the cycle containing their number, so they find their number exactly when that cycle has length at most 50. Everyone succeeds if and only if the permutation has no cycle longer than 50.

  The probability of this is

  `1 - (1/51 + 1/52 + ... + 1/100)`,

  which is about 31.18%. This is the optimal strategy: choosing 50 boxes independently would give the group only a `1/2^100` chance of success.
</details>

Source: https://en.wikipedia.org/wiki/100_prisoners_problem


## 1000 Bottles and 10 Prisoners

There are 1000 bottles, exactly one of which is poisoned, and 10 prisoners available to test them. The poison takes effect within a known time, and all tests must be done in one round. How can they identify the poisoned bottle?

<details>
  <summary>Solution and explanation</summary>

  Number the bottles from 1 to 1000 and write each number in binary using 10 digits. Assign one prisoner to each binary digit, from the 1s digit through the 512s digit. Each prisoner drinks a small sample from every bottle whose number has a 1 in that prisoner's digit.

  After the poison takes effect, record a 1 for each prisoner who dies and a 0 for each prisoner who survives. Read those ten results as a binary number: it gives the number of the poisoned bottle. For example, if the bottle numbered 13 is poisoned, the prisoners assigned to the 1s, 4s, and 8s digits die, since 13 is `0000001101` in binary.

  Ten prisoners can produce `2^10 = 1024` distinct outcome patterns, enough to distinguish 1000 bottles. This is also the minimum number of prisoners needed for a one-round test, since nine prisoners produce only `2^9 = 512` patterns.
</details>
