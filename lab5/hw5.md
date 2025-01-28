---
title: "Homework 5"
author: "Type Your Name Here"
date: "2025-01-27"
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

## Data 
For this assignment, we will use data from a study on vertebrate community composition and impacts from defaunation in [Gabon, Africa](https://en.wikipedia.org/wiki/Gabon). One thing to notice is that the data include 24 separate transects. Each transect represents a path through different forest management areas.  

Reference: Koerner SE, Poulsen JR, Blanchard EJ, Okouyi J, Clark CJ. Vertebrate community composition and diversity declines along a defaunation gradient radiating from rural villages in Gabon. _Journal of Applied Ecology_. 2016. This paper, along with a description of the variables is included inside the data folder.   

**1. Load `IvindoData_DryadVersion.csv` and store it as a new object called `gabon`.**

``` r
gabon <- read.csv("data/IvindoData_DryadVersion.csv")
```

**2. Use one or more of the summary functions you have learned to get an idea of the structure of the data.**  

``` r
summary(gabon)
```

```
##    TransectID       Distance        HuntCat          NumHouseholds  
##  Min.   : 1.00   Min.   : 2.700   Length:24          Min.   :13.00  
##  1st Qu.: 5.75   1st Qu.: 5.668   Class :character   1st Qu.:24.75  
##  Median :14.50   Median : 9.720   Mode  :character   Median :29.00  
##  Mean   :13.50   Mean   :11.879                      Mean   :37.88  
##  3rd Qu.:20.25   3rd Qu.:17.683                      3rd Qu.:54.00  
##  Max.   :27.00   Max.   :26.760                      Max.   :73.00  
##    LandUse             Veg_Rich       Veg_Stems       Veg_liana     
##  Length:24          Min.   :10.88   Min.   :23.44   Min.   : 4.750  
##  Class :character   1st Qu.:13.10   1st Qu.:28.69   1st Qu.: 9.033  
##  Mode  :character   Median :14.94   Median :32.45   Median :11.940  
##                     Mean   :14.83   Mean   :32.80   Mean   :11.040  
##                     3rd Qu.:16.54   3rd Qu.:37.08   3rd Qu.:13.250  
##                     Max.   :18.75   Max.   :47.56   Max.   :16.380  
##     Veg_DBH        Veg_Canopy    Veg_Understory     RA_Apes      
##  Min.   :28.45   Min.   :2.500   Min.   :2.380   Min.   : 0.000  
##  1st Qu.:40.65   1st Qu.:3.250   1st Qu.:2.875   1st Qu.: 0.000  
##  Median :43.90   Median :3.430   Median :3.000   Median : 0.485  
##  Mean   :46.09   Mean   :3.469   Mean   :3.020   Mean   : 2.045  
##  3rd Qu.:50.58   3rd Qu.:3.750   3rd Qu.:3.167   3rd Qu.: 3.815  
##  Max.   :76.48   Max.   :4.000   Max.   :3.880   Max.   :12.930  
##     RA_Birds      RA_Elephant       RA_Monkeys      RA_Rodent    
##  Min.   :31.56   Min.   :0.0000   Min.   : 5.84   Min.   :1.060  
##  1st Qu.:52.51   1st Qu.:0.0000   1st Qu.:22.70   1st Qu.:2.047  
##  Median :57.90   Median :0.3600   Median :31.74   Median :3.230  
##  Mean   :58.64   Mean   :0.5450   Mean   :31.30   Mean   :3.278  
##  3rd Qu.:68.17   3rd Qu.:0.8925   3rd Qu.:39.88   3rd Qu.:4.093  
##  Max.   :85.03   Max.   :2.3000   Max.   :54.12   Max.   :6.310  
##   RA_Ungulate     Rich_AllSpecies Evenness_AllSpecies Diversity_AllSpecies
##  Min.   : 0.000   Min.   :15.00   Min.   :0.6680      Min.   :1.966       
##  1st Qu.: 1.232   1st Qu.:19.00   1st Qu.:0.7542      1st Qu.:2.248       
##  Median : 2.545   Median :20.00   Median :0.7760      Median :2.316       
##  Mean   : 4.166   Mean   :20.21   Mean   :0.7699      Mean   :2.310       
##  3rd Qu.: 5.157   3rd Qu.:22.00   3rd Qu.:0.8083      3rd Qu.:2.429       
##  Max.   :13.860   Max.   :24.00   Max.   :0.8330      Max.   :2.566       
##  Rich_BirdSpecies Evenness_BirdSpecies Diversity_BirdSpecies Rich_MammalSpecies
##  Min.   : 8.00    Min.   :0.5590       Min.   :1.162         Min.   : 6.000    
##  1st Qu.:10.00    1st Qu.:0.6825       1st Qu.:1.603         1st Qu.: 9.000    
##  Median :11.00    Median :0.7220       Median :1.680         Median :10.000    
##  Mean   :10.33    Mean   :0.7137       Mean   :1.661         Mean   : 9.875    
##  3rd Qu.:11.00    3rd Qu.:0.7722       3rd Qu.:1.784         3rd Qu.:11.000    
##  Max.   :13.00    Max.   :0.8240       Max.   :2.008         Max.   :12.000    
##  Evenness_MammalSpecies Diversity_MammalSpecies
##  Min.   :0.6190         Min.   :1.378          
##  1st Qu.:0.7073         1st Qu.:1.567          
##  Median :0.7390         Median :1.699          
##  Mean   :0.7477         Mean   :1.698          
##  3rd Qu.:0.7847         3rd Qu.:1.815          
##  Max.   :0.8610         Max.   :2.065
```
  

``` r
names(gabon)
```

```
##  [1] "TransectID"              "Distance"               
##  [3] "HuntCat"                 "NumHouseholds"          
##  [5] "LandUse"                 "Veg_Rich"               
##  [7] "Veg_Stems"               "Veg_liana"              
##  [9] "Veg_DBH"                 "Veg_Canopy"             
## [11] "Veg_Understory"          "RA_Apes"                
## [13] "RA_Birds"                "RA_Elephant"            
## [15] "RA_Monkeys"              "RA_Rodent"              
## [17] "RA_Ungulate"             "Rich_AllSpecies"        
## [19] "Evenness_AllSpecies"     "Diversity_AllSpecies"   
## [21] "Rich_BirdSpecies"        "Evenness_BirdSpecies"   
## [23] "Diversity_BirdSpecies"   "Rich_MammalSpecies"     
## [25] "Evenness_MammalSpecies"  "Diversity_MammalSpecies"
```
  

``` r
is.factor("HuntCat")
```

```
## [1] FALSE
```
  
**3. Use `mutate()` Change the variables `HuntCat`, `LandUse`, and `TransectID` to factors.**

``` r
gabon %>%
  mutate(HuntCat=as.factor(HuntCat), LandUse=as.factor(LandUse), TransectID=as.factor(TransectID)) %>%
  select("HuntCat", "LandUse", "TransectID")
```

```
##     HuntCat LandUse TransectID
## 1  Moderate    Park          1
## 2      None    Park          2
## 3      None    Park          2
## 4      None Logging          3
## 5      None    Park          4
## 6      None    Park          5
## 7      None    Park          6
## 8      None Logging          7
## 9      High Neither          8
## 10     High Logging          9
## 11 Moderate Logging         13
## 12 Moderate Logging         14
## 13     High Neither         15
## 14 Moderate Logging         16
## 15     High Neither         17
## 16     None Logging         18
## 17 Moderate Logging         19
## 18 Moderate Logging         20
## 19     High Neither         21
## 20     High Logging         22
## 21     None    Park         24
## 22 Moderate Logging         25
## 23 Moderate Logging         26
## 24     High Logging         27
```

**4. Use `filter` to make three new dataframes focused only on 1. national parks, 2. logging concessions, and 3. neither. Have a look at the README in the data folder so you understand the variables.**

``` r
national_parks <- filter(gabon, LandUse=="Park")
```


``` r
logging_c <- filter(gabon, LandUse=="Logging" )
```


``` r
net <- filter(gabon, LandUse=="Neither")
```

**5. How many transects are recorded for each land use type?**
13 for Logging, 4 for Neither, and 7 for Park 

``` r
table(gabon$LandUse)
```

```
## 
## Logging Neither    Park 
##      13       4       7
```

**6. For which land use type (national parks, logging, or neither) is average all species diversity the greatest?**
National Parks demonstrate the greatest average all species diversity 


``` r
mean(national_parks$Diversity_AllSpecies)
```

```
## [1] 2.425143
```


``` r
mean(net$Diversity_AllSpecies)
```

```
## [1] 2.3575
```


``` r
mean(logging_c$Diversity_AllSpecies)
```

```
## [1] 2.232538
```

**7. Use `filter` to find the transect that has the highest relative abundance of elephants. What land use type is this? Use `arrange()` to sort your results.** 

``` r
gabon%>%
  select(TransectID, RA_Elephant, LandUse)%>%
  filter(RA_Elephant == max(RA_Elephant))
```

```
##   TransectID RA_Elephant LandUse
## 1         18         2.3 Logging
```
Logging has the highest relative abundance of elephants at TransectID 18

**8. Use `filter` to find all transects that have greater than 15 tree species or a breast height diameter between 50 and 60cm.  **

``` r
filter(gabon, Veg_Rich > 15,(Veg_DBH >=50 & Veg_DBH <=60))
```

```
##   TransectID Distance  HuntCat NumHouseholds LandUse Veg_Rich Veg_Stems
## 1         14     8.23 Moderate            56 Logging    15.75     30.22
## 2         21     5.14     High            24 Neither    16.25     34.89
##   Veg_liana Veg_DBH Veg_Canopy Veg_Understory RA_Apes RA_Birds RA_Elephant
## 1     14.13   52.12       3.57           2.86    0.46    66.56        0.52
## 2     15.38   50.36       3.13           2.63    4.21    68.15        0.77
##   RA_Monkeys RA_Rodent RA_Ungulate Rich_AllSpecies Evenness_AllSpecies
## 1      26.66      4.54        1.27              22               0.699
## 2      21.46      5.41        0.00              19               0.833
##   Diversity_AllSpecies Rich_BirdSpecies Evenness_BirdSpecies
## 1                2.161               11                0.701
## 2                2.452                9                0.824
##   Diversity_BirdSpecies Rich_MammalSpecies Evenness_MammalSpecies
## 1                 1.681                 11                  0.861
## 2                 1.810                 10                  0.742
##   Diversity_MammalSpecies
## 1                   2.065
## 2                   1.708
```

**9.Which transects and land use types have more than 10 tree species and 10 mammal species? Use `arrange()` to sort by the number of tree species.**

``` r
gabon%>% 
  select(TransectID, LandUse, Veg_Rich, Rich_MammalSpecies)%>%
  filter(Veg_Rich > 10 & Rich_MammalSpecies > 10)%>%
  arrange(Veg_Rich)
```

```
##   TransectID LandUse Veg_Rich Rich_MammalSpecies
## 1          3 Logging    12.44                 11
## 2          6    Park    14.75                 12
## 3         14 Logging    15.75                 11
## 4          5    Park    16.50                 12
## 5          1    Park    16.67                 11
## 6         24    Park    16.75                 12
## 7          2    Park    16.88                 11
## 8          4    Park    17.13                 12
## 9         22 Logging    17.13                 12
```
Land Use types Park and Logging, belonging to Transects 1-6, 14, 22, and 24 have more than 10 tree and mammal species.  

**10. Explore the data! Develop one question on your own that includes at least two lines of code. **
**Which LandUse types have a relative abundance of birds greater than 50% and a relative abundance of monkeys less than 30% ? Arrange by relative abundance of birds. 

``` r
gabon%>%
  select (LandUse, RA_Monkeys, RA_Birds)%>% 
  filter(RA_Monkeys < 30 & RA_Birds > 50 )%>%
  arrange(RA_Birds)
```

```
##    LandUse RA_Monkeys RA_Birds
## 1     Park      28.53    52.17
## 2  Logging      19.85    59.29
## 3  Logging      23.94    62.04
## 4  Logging      26.66    66.56
## 5  Logging      27.71    67.25
## 6  Neither      21.46    68.15
## 7  Logging      25.58    68.25
## 8  Logging      23.12    72.99
## 9  Neither      20.02    73.06
## 10 Logging      18.69    74.40
## 11 Logging       5.84    85.01
## 12 Neither       9.09    85.03
```
All three land types fit this criteria 

## Knit and Upload
Please knit your work as a .pdf or .html file and upload to Canvas. Homework is due before the start of the next lab. No late work is accepted. Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  
