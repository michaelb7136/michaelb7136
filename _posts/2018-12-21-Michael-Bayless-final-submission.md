---
layout: post
title: "Flag Project - Final Submission"
date: 2018-12-21
---

## Unit 4 of the data science curriculum by Michael Bayless

## Describe your program

This program's purpose is to manipulate a data set that I chose. 

## Current output

* * *
![Chart](/images/chart.png)
* * *

## Describe your process.

-   What questions, strategies, help from peers or teacher, or thinking got you to this point? _then delete this instruction_

<!--- Delete this comment and add your writing -->


## Explain your code.

-   Choose a significant part of your program (15 lines max) and paste it below. Do not insert your entire program here. _then delete this instruction_
-   Explain each argument in the code section. _then delete this instruction_
-   Tell us how it functions independently and within the whole program _then delete this instruction_

* * *

```
fun is-mega(row):
  if string-length(row["name"]) < 5:
    false
  else if not(string-substring(row["name"],4,5) == " "):
    false
  else:
  "Mega" == string-substring(row["name"],0,4)
  end
end
```

* * *

-   Explain the code you posted by telling us about each argument.
-   Then tell us how your code section fits into the whole.
 
 


## Program code

```
# include Libraries we want
include shared-gdrive("Bootstrap-DataScience-v1.2.arr", "1jum6V7z8nqaCSnS3rv3uintE2lkktyNq")
include gdrive-sheets
include tables
include image

# Define your spreadsheet
pokemon-sheet = load-spreadsheet("1F5Q2HwyhrhzMBivKNA2qpgUroqGWpDTUKcF3p82pVDA")

p-table = load-table: number, name, type1, type2, total, hp,	attack,	defense,	special-attack,	special-defense,	speed,	generation,	legendary
  source: pokemon-sheet.sheet-by-name("Pokemon", true)
end
  
# https://mrallatta.github.io/sy18-19-lacs/
# Extracting some rows
charizard = p-table.row-n(6)
mew = p-table.row-n(165)
mega-charizard = p-table.row-n(7)
fun is-legendary(row):
  row["legendary"]
end

fun not-legendary(row):
  not(is-legendary(row))
end

fun stat-avg(row):
  row["total"] / 6
end

fun has-one-type(row):
  row["type2"] == "None"
end

fun two-type(row):
  not(has-one-type(row))
end

fun is-mega(row):
  if string-length(row["name"]) < 5:
    false
  else if not(string-substring(row["name"],4,5) == " "):
    false
  else:
  "Mega" == string-substring(row["name"],0,4)
  end
end

fun not-mega(row):
  not(is-mega(row))
end

p-table2 = p-table.build-column("stat average",stat-avg)
p-table3 = p-table2.build-column("mega?",is-mega)
no-mega-table = p-table3.filter(not-mega)
normal-p-table = no-mega-table.filter(not-legendary).order-by("stat average",true)
legendary-table = p-table3.filter(is-legendary).order-by("stat average",true)
mega-table = p-table3.filter(is-mega).order-by("stat average",true)

#bar-chart(mega-table,"name","stat average")
#pie-chart(mega-table,"name","stat average")
#pie-chart(legendary-table,"name","stat average")
#bar-chart(legendary-table,"name","stat average")



```
