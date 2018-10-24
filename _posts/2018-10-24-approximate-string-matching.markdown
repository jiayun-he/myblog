---
layout: "post"
title: "Approximate String Matching"
date: "2018-10-24 18:38"
author: Jiayun
---
{% include mathjax.html %}

### Approximate String Matching
For convenience, we use (m,i,d,r) to infer (matching, insertion, deletion, replacement)

#### Neighborhood Search
In neighborhood, there are operations: i,d,r. Linux's [agrep](https://github.com/Wikinaut/agrep) is one of the most famous fast neighborhood search tool. A simple example is given below:
```
agrep -2 -w word dictionary.txt
```
"-2" indicates a 2-neighborhood, which means at most 2 operations (i,d,r) can be performed. "-w" indicates the matching string must be a word. All 2-neighborhood words of "word" from the dictionary.txt file will be returned.

#### Edit Distance
A "score" or "distance" will be returned by the according algorithms.

![ed](/myblog/assets/ed.png)

When determine a new value in the grid, the edit distance algorithms will compare the neighboring 3 pre-calculated values with the corresponding operation score/penalty.
The three choices are:<br>

$$(i,j-1) + deletion$$

$$(i-1,j) + insertion$$

$$(i-1,j-1) + match/replacement$$

##### Global Edit Distance
let us assume the first word is "led" and second word is "deed", and (m,i,d,r) = (-3,1,4,2)

**Since m < i,d,r the algorithm will select the minimum among the three choices. In other words, if (m,i,d,r) = (1,-1,-1,-1), the maximum will be selected.**

![ed](/myblog/assets/ged.png)

Let us calculate the question marked grid:


$$(i,j-1) + deletion = 1 + 4 = 5$$

$$(i-1,j) + insertion = 4 + 1 = 5$$

Since "l" != "d",

$$(i-1,j-1) + match/replacement = 0 + 2 = 2$$

Among which the minimum is 2, we fill the grid with 2, mark the operation and source:

![ed](/myblog/assets/ged_2.png)

P.S.

Needleman–Wunsch algorithm (m,i,d,r) = (1,-1,-1,-1) -> max()

Levenshtein distance (m,i,d,r) = (0,1,1,1) -> min()

##### Local Edit distance
For local edit distance, one more choice - 0 is created. LED algorithms are used to search for best substring matches. Like GEDs, **max() when m > i,d,r or min() otherwise**.

#### N-Grams
Let: A = "led", B = "deed". <br><br>
N_Gram_distance = $$ |A|+|B|-2|A\cap B| $$

Let us do a 2-gram distance.

2-GRAMS of A:

#l, le, ed, d#

and B:

#d, de, ee, ed, d#

There are 2 matches: ed and #d

2_Gram_distance = 4 + 5 - 2 * 2 = 5


#### Soundex
The steps for converting a word to soundex representation:
1. Except for initial character, translate string characters according to soundex table.
2. Remove duplicates (e.g. 4444 → 4)
3. Remove 0s
4. Truncate to four symbols

Consider a simple soundex table:

| symbols | soundex number|
|:---:|:---:|
| aeiouwy  | 0  |
|  bdgjlmnrvz | 1  |
| cfhkpqstx  |  2 |

and a word "carter":

1. c01201
2. c01201
3. c121
4. c121

So, the soundex representation of word "carter" is **c121**.
