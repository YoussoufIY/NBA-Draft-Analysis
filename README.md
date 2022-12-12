# Project 1: Team-14

## Table of Contents
- [Project Overview](#project-overview)
- [Methodology Overview](#methodology-overview)
- [Data Cleaning and Organization](#data-cleaning-and-organization)

## Project Overview
Arguably, one the most important decisions NBA managers and coaches need to make each year, especially those who rank high in the NBA lottery, is related to which talent they select on draft night as this player could potentially turn-around a weak franchise's losing record. Due to the high stakes associated with this decision, in this project we explore the following:
- Whether or not the draft position of an NBA player in any given year from 1990-2021 is correlated with future success; and 
- Whether or not general managers and coaches of NBA teams have historically done a good job of increasing their teams' chances of succes by analyzing the top 10 draft pick data from 1990-2021.

### **Research Question:** Is the position at which a player is drafted commensurate with the value they bring to their team?

To answer the research question and the points of exploration listed above, the research question was broken down into a smaller subset of questions. In this project we measure the succcess and value a player brings to an organization by looking at their offensive output, defensive output, and their overall impact they have on their respective teams' winning record. Moreover, the questions explored were:
- **Do top draft picks bring offensive value?** To measure this, we looked at historical regular season player data highlighting the following:
    - **Points scored per game (PPG)**
    - **Assists made per game (APG)**
- **Do top draft picks bring defensive value?** To measure this, we looked at historical regular season player data highlighting the following:
    - **Steals made per game (STPG)**
    - **Blocks made per game (BLKPG)**
- **Are top draft picks significant contributors to their respective teams' winning record?** To measure this, we looked at historical regular season player data highlighting the following:
    - **Box plus minus per season (BPM)**
    - **Win shares per season (WS)**
 
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

