---
title: "Homework 6"
author: "Type Your Name Here"
date: "2025-01-29"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---

## Instructions
Answer the following questions and/or complete the exercises in RMarkdown. Please embed all of your code and push the final work to your repository. Your report should be organized, clean, and run free from errors. Remember, you must remove the `#` for any included code chunks to run.  

## Load the tidyverse

``` r
library("tidyverse")
library("janitor")
```

## Load the superhero data
Let's have a little fun with this one! We are going to explore data on superheroes. These are data taken from comic books and assembled by devoted fans. The include a good mix of categorical and continuous data.  Data taken from: https://www.kaggle.com/claudiodavi/superhero-set  

Load the `heroes_information.csv` and `super_hero_powers.csv` data. Make sure the columns are cleanly named.

``` r
superhero_info <- read_csv("data/heroes_information.csv", na = c("", "-99", "-")) %>% clean_names()
```

```
## Rows: 734 Columns: 10
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (8): name, Gender, Eye color, Race, Hair color, Publisher, Skin color, A...
## dbl (2): Height, Weight
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

``` r
superhero_powers <- read_csv("data/super_hero_powers.csv", na = c("", "-99", "-")) %>% clean_names()
```

```
## Rows: 667 Columns: 168
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr   (1): hero_names
## lgl (167): Agility, Accelerated Healing, Lantern Power Ring, Dimensional Awa...
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

1. For the superhero_info data, how many bad, good, and neutral superheros are there? Try using count() and/ or tabyl().

``` r
superhero_info %>% 
  count(alignment)
```

```
## # A tibble: 4 × 2
##   alignment     n
##   <chr>     <int>
## 1 bad         207
## 2 good        496
## 3 neutral      24
## 4 <NA>          7
```
There are 207 bad, 496 good, and 24 neutral.

``` r
superhero_info %>% 
  tabyl(alignment)
```

```
##  alignment   n     percent valid_percent
##        bad 207 0.282016349    0.28473177
##       good 496 0.675749319    0.68225585
##    neutral  24 0.032697548    0.03301238
##       <NA>   7 0.009536785            NA
```

2. Notice that we have some bad superheros! Who are they? List their names below.  

``` r
superhero_info %>% 
  filter(alignment=="bad") %>% 
  pull(name)
```

```
##   [1] "Abomination"       "Abraxas"           "Absorbing Man"    
##   [4] "Air-Walker"        "Ajax"              "Alex Mercer"      
##   [7] "Alien"             "Amazo"             "Ammo"             
##  [10] "Angela"            "Annihilus"         "Anti-Monitor"     
##  [13] "Anti-Spawn"        "Apocalypse"        "Arclight"         
##  [16] "Atlas"             "Azazel"            "Bane"             
##  [19] "Beetle"            "Big Barda"         "Big Man"          
##  [22] "Billy Kincaid"     "Bird-Man"          "Bird-Man II"      
##  [25] "Black Abbott"      "Black Adam"        "Black Mamba"      
##  [28] "Black Manta"       "Blackout"          "Blackwing"        
##  [31] "Blizzard"          "Blizzard"          "Blizzard II"      
##  [34] "Blob"              "Bloodaxe"          "Bloodwraith"      
##  [37] "Boba Fett"         "Bomb Queen"        "Brainiac"         
##  [40] "Bullseye"          "Callisto"          "Carnage"          
##  [43] "Chameleon"         "Changeling"        "Cheetah"          
##  [46] "Cheetah II"        "Cheetah III"       "Chromos"          
##  [49] "Clock King"        "Cogliostro"        "Cottonmouth"      
##  [52] "Curse"             "Cy-Gor"            "Cyborg Superman"  
##  [55] "Darkseid"          "Darkside"          "Darth Maul"       
##  [58] "Darth Vader"       "Deadshot"          "Demogoblin"       
##  [61] "Destroyer"         "Diamondback"       "Doctor Doom"      
##  [64] "Doctor Doom II"    "Doctor Octopus"    "Doomsday"         
##  [67] "Doppelganger"      "Dormammu"          "Ego"              
##  [70] "Electro"           "Elle Bishop"       "Evil Deadpool"    
##  [73] "Evilhawk"          "Exodus"            "Fabian Cortez"    
##  [76] "Fallen One II"     "Faora"             "Fixer"            
##  [79] "Frenzy"            "General Zod"       "Giganta"          
##  [82] "Goblin Queen"      "Godzilla"          "Gog"              
##  [85] "Gorilla Grodd"     "Granny Goodness"   "Greedo"           
##  [88] "Green Goblin"      "Green Goblin II"   "Harley Quinn"     
##  [91] "Heat Wave"         "Hela"              "Hobgoblin"        
##  [94] "Hydro-Man"         "Iron Monger"       "Jigsaw"           
##  [97] "Joker"             "Junkpile"          "Kang"             
## [100] "Killer Croc"       "Killer Frost"      "King Shark"       
## [103] "Kingpin"           "Klaw"              "Kraven II"        
## [106] "Kraven the Hunter" "Kylo Ren"          "Lady Bullseye"    
## [109] "Lady Deathstrike"  "Leader"            "Lex Luthor"       
## [112] "Lightning Lord"    "Living Brain"      "Lizard"           
## [115] "Loki"              "Luke Campbell"     "Mach-IV"          
## [118] "Magneto"           "Magus"             "Mandarin"         
## [121] "Match"             "Maxima"            "Mephisto"         
## [124] "Metallo"           "Mister Freeze"     "Mister Knife"     
## [127] "Mister Mxyzptlk"   "Mister Sinister"   "Mister Zsasz"     
## [130] "MODOK"             "Moloch"            "Molten Man"       
## [133] "Moonstone"         "Morlun"            "Moses Magnum"     
## [136] "Mysterio"          "Mystique"          "Nebula"           
## [139] "Omega Red"         "Onslaught"         "Overtkill"        
## [142] "Ozymandias"        "Parademon"         "Penguin"          
## [145] "Plantman"          "Plastique"         "Poison Ivy"       
## [148] "Predator"          "Professor Zoom"    "Proto-Goblin"     
## [151] "Purple Man"        "Pyro"              "Ra's Al Ghul"     
## [154] "Razor-Fist II"     "Red Mist"          "Red Skull"        
## [157] "Redeemer II"       "Redeemer III"      "Rhino"            
## [160] "Rick Flag"         "Riddler"           "Sabretooth"       
## [163] "Sauron"            "Scarecrow"         "Scarlet Witch"    
## [166] "Scorpia"           "Scorpion"          "Sebastian Shaw"   
## [169] "Shocker"           "Siren"             "Siren II"         
## [172] "Siryn"             "Snake-Eyes"        "Solomon Grundy"   
## [175] "Spider-Carnage"    "Spider-Woman IV"   "Steppenwolf"      
## [178] "Stormtrooper"      "Superboy-Prime"    "Swamp Thing"      
## [181] "Swarm"             "Sylar"             "T-1000"           
## [184] "T-800"             "T-850"             "T-X"              
## [187] "Taskmaster"        "Thanos"            "Tiger Shark"      
## [190] "Tinkerer"          "Trigon"            "Two-Face"         
## [193] "Ultron"            "Utgard-Loki"       "Vanisher"         
## [196] "Vegeta"            "Venom"             "Venom II"         
## [199] "Venom III"         "Violator"          "Vulture"          
## [202] "Walrus"            "Warp"              "Weapon XI"        
## [205] "White Canary"      "Yellow Claw"       "Zoom"
```


3. How many distinct "races" are represented in `superhero_info`?

``` r
superhero_info%>%
  summarize(superhero_race=n_distinct(race, na.rm=T))
```

```
## # A tibble: 1 × 1
##   superhero_race
##            <int>
## 1             61
```
There are 61 distinct races 

## Good and Bad
4. Let's make two different data frames, one focused on the "good guys" and another focused on the "bad guys".

``` r
good_guys <- filter(superhero_info, alignment=="good")
```


``` r
bad_guys <- filter(superhero_info, alignment=="bad")
```

5. Who are the good Vampires?

``` r
superhero_info%>%
  filter(alignment=="good", race == "Vampire")%>%
  select(name)
```

```
## # A tibble: 2 × 1
##   name 
##   <chr>
## 1 Angel
## 2 Blade
```
Angel and Blade  

6. Who has the height advantage- bad guys or good guys? Convert their height to meters and sort from tallest to shortest.  

``` r
bad_guys%>%
  mutate(bad_guy_height=height/100)%>%
  select(bad_guy_height, name)%>%
  arrange(-bad_guy_height)
```

```
## # A tibble: 207 × 2
##    bad_guy_height name          
##             <dbl> <chr>         
##  1           3.66 MODOK         
##  2           3.05 Onslaught     
##  3           2.79 Sauron        
##  4           2.79 Solomon Grundy
##  5           2.67 Darkseid      
##  6           2.57 Amazo         
##  7           2.44 Alien         
##  8           2.44 Doomsday      
##  9           2.44 Killer Croc   
## 10           2.29 Venom III     
## # ℹ 197 more rows
```


``` r
good_guys%>%
  mutate(good_guy_height=height/100)%>%
  select(good_guy_height, name)%>%
  arrange(-good_guy_height)
```

```
## # A tibble: 496 × 2
##    good_guy_height name         
##              <dbl> <chr>        
##  1            9.75 Fin Fang Foom
##  2            7.01 Groot        
##  3            3.66 Wolfsbane    
##  4            3.05 Sasquatch    
##  5            3.05 Ymir         
##  6            2.97 Rey          
##  7            2.59 Hellboy      
##  8            2.44 Hulk         
##  9            2.34 Kilowog      
## 10            2.26 Cloak        
## # ℹ 486 more rows
```
good guys have the height advantage

## `superhero_powers`
Have a quick look at the `superhero_powers` data frame.  

7. How many superheros have a combination of agility, stealth, super_strength, and stamina?

``` r
superhero_powers%>% 
  filter(agility == TRUE, stealth == TRUE, super_strength == TRUE, stamina == TRUE)%>%
  count()
```

```
## # A tibble: 1 × 1
##       n
##   <int>
## 1    40
```
40 superheros have a combination of those abilities 

8. Who is the most powerful superhero? Have a look at the code chunk below. Use the internet to annotate each line of code so you know how it works. It's OK to use AI to help you with this task.

``` r
superhero_powers %>%
  #calls superhero_powers dataframe 
  mutate(across(-1, ~ ifelse(. == TRUE, 1, 0))) %>% 
  #applies to all columns except the first, converts all TRUE inputs to 1 and if not TRUE then 0 
  mutate(total_powers = rowSums(across(-1))) %>% 
  #sums up all the 1 and 0 from all the columns except the first one 
  select(hero_names, total_powers) %>% 
  #selects hero names and the new total powers column 
  arrange(-total_powers)
```

```
## # A tibble: 667 × 2
##    hero_names        total_powers
##    <chr>                    <dbl>
##  1 Spectre                     49
##  2 Amazo                       44
##  3 Living Tribunal             35
##  4 Martian Manhunter           35
##  5 Man of Miracles             34
##  6 Captain Marvel              33
##  7 T-X                         33
##  8 Galactus                    32
##  9 T-1000                      32
## 10 Mister Mxyzptlk             31
## # ℹ 657 more rows
```

``` r
  #arranges them in descending order 
```

## Your Favorite
9. Pick your favorite superhero and let's see their powers!  

``` r
superhero_powers%>% 
  filter(hero_names == "Deadpool")%>%
  select(hero_names, where(~. == TRUE))
```

```
## # A tibble: 1 × 17
##   hero_names agility accelerated_healing dimensional_awareness stealth
##   <chr>      <lgl>   <lgl>               <lgl>                 <lgl>  
## 1 Deadpool   TRUE    TRUE                TRUE                  TRUE   
## # ℹ 12 more variables: marksmanship <lgl>, weapons_master <lgl>,
## #   longevity <lgl>, stamina <lgl>, weapon_based_powers <lgl>,
## #   teleportation <lgl>, immortality <lgl>, reflexes <lgl>, regeneration <lgl>,
## #   toxin_and_disease_resistance <lgl>, telepathy_resistance <lgl>,
## #   mind_control_resistance <lgl>
```

10. Can you find your hero in the superhero_info data? Show their info!  

``` r
superhero_info%>%
  filter(name == "Deadpool")
```

```
## # A tibble: 1 × 10
##   name   gender eye_color race  hair_color height publisher skin_color alignment
##   <chr>  <chr>  <chr>     <chr> <chr>       <dbl> <chr>     <chr>      <chr>    
## 1 Deadp… Male   brown     Muta… No Hair       188 Marvel C… <NA>       neutral  
## # ℹ 1 more variable: weight <dbl>
```

## Knit and Upload
Please knit your work as a .pdf or .html file and upload to Canvas. Homework is due before the start of the next lab. No late work is accepted. Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  
