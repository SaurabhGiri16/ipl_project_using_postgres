        
        
# :dart: IPL_Project_Using_Postgres 

 ###  Find number of matches played per Year.

    select distinct season ,**count(season) as Count_season from 
    matches group by season order by  season;

### Output :

```
'2008', '58'
'2009', '57'
'2010', '60'
'2011', '73'
'2012', '74'
'2013', '76'
'2014', '60'
'2015', '59'
'2016', '60'
'2017', '59'
```


### Find Number of matches won of all teams over all the years of IPL.


    select distinct winner ,count(winner) as Won from 
    matches where winner != "" group by winner order by winner;

### Output :

```
'Chennai Super Kings', '79'
'Deccan Chargers', '29'
'Delhi Daredevils', '62'
'Gujarat Lions', '13'
'Kings XI Punjab', '70'
'Kochi Tuskers Kerala', '6'
'Kolkata Knight Riders', '77'
'Mumbai Indians', '92'
'Pune Warriors', '12'
'Rajasthan Royals', '63'
'Rising Pune Supergiant', '10'
'Rising Pune Supergiants', '5'
'Royal Challengers Bangalore', '73'
'Sunrisers Hyderabad', '42'
```


 ### Find the year 2016 get the extra runs conceded per team .

    select distinct batting_team , SUM(extra_runs) as Extra_Run from deliveries 
    inner join matches on matches.id= deliveries.match_id and season = 2016 
    group by batting_team order by batting_team;
 
 ### Output :
```
'Delhi Daredevils', '109'
'Gujarat Lions', '132'
'Kings XI Punjab', '83'
'Kolkata Knight Riders', '130'
'Mumbai Indians', '102'
'Rising Pune Supergiants', '101'
'Royal Challengers Bangalore', '118'
'Sunrisers Hyderabad', '124'
```

### Find the year 2015 get the top economical bowlers.



    select bowler ,(sum(total_runs)*6.0)/(count(bowler)) as Most_Economical_Bowler from deliveries , matches
    where matches.id= deliveries.match_id and matches.season=2015 group by bowler 
    order by Most_Economical_Bowler limit 1;
 
 ### Output :
 `'RN ten Doeschate', '3.42857'`
