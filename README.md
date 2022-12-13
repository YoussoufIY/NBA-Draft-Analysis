<img width="1180" alt="Screen Shot 2022-12-12 at 2 00 50 AM" src="https://user-images.githubusercontent.com/113209883/206981244-33551d00-95ce-4a9c-a33d-69f9d7e2ee9c.png">


## Table of Contents
- [Project Overview](#project-overview)
- [Repository Structure and Organization](#repository-structure-and-organization)
- [Methodology Overview](#methodology-overview)
    - [Datasets Used](#datasets-used)
    - [Data Cleaning and Organization](#data-cleaning-and-organization)
- [Results and Analysis](#results-and-analysis)
    - [Addressing the First Question](#addressing-the-first-question)
    - [Addressing the Second Question](#addressing-the-second-question)
    - [Addressing the Third Question](#addressing-the-third-question)
- [Conclusions and Project Limitations](#conclusions-and-project-limitations)

## Project Overview
Arguably, one the most important decisions NBA managers and coaches need to make each year, especially those who rank high in the NBA lottery, is related to which talent they select on draft night as this player could potentially turn-around a weak franchise's losing record. Due to the high stakes associated with this decision, in this project we explore the following:
- Whether or not the draft position of an NBA player in any given year from 1990-2021 is correlated with future success; and 
- Whether or not general managers and coaches of NBA teams have historically done a good job of increasing their teams' chances of succes by analyzing the top 10 draft pick data from 1990-2021.

### **Research Question:** Is the position at which a player is drafted commensurate with the value they bring to their team?

To answer the research question and the points of exploration listed above, the research question was broken down into a smaller subset of questions. In this project we measure the succcess and value a player brings to an organization by looking at their offensive output, defensive output, and their overall impact they have on their respective teams' winning record. Moreover, the questions explored were:
- **Do top draft picks bring offensive value?** To measure this, we looked at historical regular season player data highlighting the following:
    - Points scored per game (PPG)
    - Assists made per game (APG)
- **Do top draft picks bring defensive value?** To measure this, we looked at historical regular season player data highlighting the following:
    - Steals made per game (STPG)
    - Blocks made per game (BLKPG)
- **Are top draft picks significant contributors to their respective teams' winning record?** To measure this, we looked at historical regular season player data highlighting the following:
    - Box plus minus per season (BPM)
    - Win shares per season (WS)

## Repository Structure and Organization
This repository contains the following folders and files:
> A **folder** titled ```Resources``` that contains:
> - Visualization output that plots **assists per game** as a function of draft position titled ```APG.png```;
> - Visualization output that plots **blocks per game** as a function of draft position titled ```BLKPG.png```;
> - Visualization output that plots **box plus-minus** as a function of draft position titled ```BPM.png```;
> - Visualization output that plots **points per game** as a function of draft position titled ```PPG.png```;
> - Visualization output that plots **steals per game** as a function of draft position titled ```STPG.png```;
> - Visualization output that plots **win-shares** as a function of draft position titled ```WS.png```;
> - A CSV file containing the data used in the analysis titled ```draft-data-20-years.csv```;
> - A CSV file containing the data used in the analysis titled ```player_data.csv```; and
> - A CSV file containing the data used in the analysis titled ```player_stats.csv```;

- A ```.gitignore``` file to ensure that the file that contains the API keys is kept from being shared with the public;
- The final PPT presentation slides titled ```Basketball Presentation v3.0.pptx```;
- The final ```Jupyter Notebook``` containing the Python script that extracted, cleaned, and organized all the data used in this project titled ```Data_Extraction.ipynb```; and
- The final ```Jupyter Notebook``` containing the Python script that created the visualizations used in this project titled ```Visualizations_Final.ipynb```.

## Methodology Overview
### Datasets Used
To answer the subquestions listed above, we first extracted data from an NBA API called ```Balldontlie.io```. We used this API to gather defensive player statistics per regular season, including **Steals** and **Blocks**. The API was not cooperative for a high number of requests; therefore the Python sleep function was implemented to delay every request. While this process took several hours to complete, it enabled 10,000+ requests to be made to gather data on 300+ players over 32 seasons. In addition to the API mentioned above, we used ```Kaggle``` to directly download NBA player datasets directly through their public API. Using this resource, we collected offensive regular season player stats, including **Points Per Game** and **Assists Per Game**, as well as other statistics pertaining to a player's contribution to their respective organization, including **Box Plus Minus** and **Win Share** stats. 

### Data Cleaning and Organization
To clean and organize the data collected, ```Python``` and more specifically, the ```pandas``` Python library was used. Given the large sets of data related to the players drafted from 1990-2021 and their associated statistics, players were grouped by the position they were selected in during their draft year. Since we only considered high lottery picks (i.e., those selected in the Top 10), using the grouping method outlined above produced 10 groups to compare:
- Group containing all of the **No. 1** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 2** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 3** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 4** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 5** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 6** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 7** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 8** picks in the drafts that occured between 1990-2021;
- Group containing all of the **No. 9** picks in the drafts that occured between 1990-2021; and
- Group containing all of the **No. 10** picks in the drafts that occured between 1990-2021.

In addition, we narrowed down over 20 player statistics for each group to the following 6:
- Points Per Game (PPG);
- Assists Per Game (APG);
- Steals Per Game (STPG);
- Blocks Per Game (BLKPG);
- Win-Shares (WS); and 
- Box Plus-Minus (BPM).

**Figure 1** below summarizes this grouping system. 

![fig1](https://user-images.githubusercontent.com/113209883/206972642-2e7ef42d-9e13-4f04-9f6b-eb339aa53e63.jpg)

## Results and Analysis
### Addressing the First Question
To address the first question related to the **offensive value** brought by top NBA draft picks, **average PPG** made by each group was plotted as a function of draft position using the ```pandas``` and ```Matplotlib``` Python libraries. In addition, using the ```NumPy``` and ```scipy``` Python libraries, the r and p correlation values were computed, and a linear regression analysis was performed. The above steps produced the following plot:

![PPG](https://user-images.githubusercontent.com/113209883/206975720-346ad4af-648a-49f0-ad4d-e2b89f0bfbab.png)

Referring to the scatter plot for average career points per game as a function of draft position above, we see a negative correlation with points per game and draft position. Moreover, we see that in general, as we move down the picks of the draft, the lower their average PPG they produce. The correlation between draft position and PPG was computed to be: -0.87. The p-value was computed to be: 0.001. These values suggest that the strength of association of these variables is high and statistically significant.

Addressing the same question as above, **average APG** made by each group was also plotted as a function of draft position using the ```pandas``` and ```Matplotlib``` Python libraries. In addition, using the ```NumPy``` and ```scipy``` Python libraries, the r and p correlation values were computed, and a linear regression analysis was performed. The above steps produced the following plot:

![APG](https://user-images.githubusercontent.com/113209883/206976884-8090de2a-5b7c-4998-825b-cd0509906e35.png)

Referring to the scatter plot for average assists per game as a function of draft position above, we see a negative correlation with the assists made per game and draft position. Moreover, we see that in general, as we move down the picks of the draft, the lower their average APG these picks tend to produce. The correlation between draft position and APG was computed to be: -0.83. The p-value was computed to be: 0.003. These values suggest that the strength of association of these variables is high and statistically significant.

### Addressing the Second Question
To address the second question related to the **defensive value** brought by top NBA draft picks, **average STPG** made by each group was plotted as a function of draft position using the ```pandas``` and ```Matplotlib``` Python libraries. In addition, using the ```NumPy``` and ```scipy``` Python libraries, the r and p correlation values were computed, and a linear regression analysis was performed. The above steps produced the following plot:

![STPG](https://user-images.githubusercontent.com/113209883/206977329-3aa0e49a-81fe-4705-8ed8-0a532228fe8f.png)

Referring to the scatter plot for average steals made per game as a function of draft position above, we see a negative correlation with the steals made per game and draft position. Moreover, we see that in general, as we move down the picks of the draft, a lower the number of steals are made amongst these picks. The correlation between draft position and STPG was computed to be: -0.54. The p-value was computed to be: 0.107. These values suggest that there is not a strong relationship between draft position and the ability to produce steals within a game.

Addressing the same question as above, **average BLKPG** made by each group was also plotted as a function of draft position using the ```pandas``` and ```Matplotlib``` Python libraries. In addition, using the ```NumPy``` and ```scipy``` Python libraries, the r and p correlation values were computed, and a linear regression analysis was performed. The above steps produced the following plot:

![BLKPG](https://user-images.githubusercontent.com/113209883/206977763-b53ac2c5-3977-4888-87b4-6e6befc05318.png)

Referring to the scatter plot for average blocks made per game as a function of draft position above, we see a negative correlation with the blocks made per game and draft position. Moreover, we see that in general, as we move down the picks of the draft, a lower the number of blocks are made amongst these picks. The correlation between draft position and BLKPG was computed to be: -0.77. The p-value was computed to be: 0.009. These values suggest that there is a strong correlation between draft position and the ability to produce blocks within a games. This makes sense in the context of the Modern NBA as Forwards tend to be more desired than Guards given their dominant physical attributes. 

### Addressing the Third Question
Lastly, to address the third question related to the **team impact** draft picks have **average WS** of each group was plotted as a function of draft position using the ```pandas``` and ```Matplotlib``` Python libraries. In addition, using the ```NumPy``` and ```scipy``` Python libraries, the r and p correlation values were computed, and a linear regression analysis was performed. The above steps produced the following plot:

![WS](https://user-images.githubusercontent.com/113209883/206978396-975fe0e6-1cfb-41d7-975c-80ed09af81d0.png)

Referring to the scatter plot for average WS as a function of draft position above, we see a negative correlation with WS and draft position. Moreover, we see that in general, as we move down the picks of the draft, a lower the number the WS values are amongst these picks. The correlation between draft position and WS was computed to be: -0.73. The p-value was computed to be: 0.017. These values suggest that there is a strong correlation between draft position and a pick's WS.

Addressing the same question as above, **average BPM** of each group was also plotted as a function of draft position using the ```pandas``` and ```Matplotlib``` Python libraries. In addition, using the ```NumPy``` and ```scipy``` Python libraries, the r and p correlation values were computed, and a linear regression analysis was performed. The above steps produced the following plot:

![BPM](https://user-images.githubusercontent.com/113209883/206978791-96ee3372-7918-436a-ab7c-e62f4e0d327a.png)

Referring to the scatter plot for average BPM as a function of draft position above, we see a negative correlation with BPM and draft position. Moreover, we see that in general, as we move down the picks of the draft, a lower the number the BPM scores are amongst these picks. The correlation between draft position and WS was computed to be: -0.79. The p-value was computed to be: 0.006. These values suggest that the strength of association of these variables is high and statistically significant.

## Conclusions and Project Limitations
Based on our analysis, we see that on average, players selected higher in the NBA draft tend to outperform others drafted below them in terms of offensive output, defensive output, and overall team impact. This suggests that NBA general managers and coaches that have had the opportunity to draft the first few picks in each NBA draft have been successful in doing so, especially in regards to players that offensively excel.

While this in general is true, there were outliers as can be observed in each of the plots above. These outliers are most likely related to the limitations with the scope of our study. Moreover, our analysis does not take into account the nature of the draft and several other limitations, which we believe affects these stats (e.g., positions of players drafted, physcial attributes of players selected, rank of team selecting players high in the draft, lack of implementation of more advanced stats that take into account more of the basic statistics we used in this analysis, etc...). In addition to that, this study does not take into account the "intanglibles" inherent in any sport (e.g., player psychology). 
