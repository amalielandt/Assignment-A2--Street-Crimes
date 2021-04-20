# Assignment A2 - Street Crimes

### Download a data set in a csv format and use (some of) the data in it to create a graph database.

- Gem [csv filen](https://github.com/amalielandt/Assignment-A2--Street-Crimes/blob/main/2021-02-dorset-street.csv) med det anvendte data i import folderen som vist på billedet

<img width="901" alt="Skærmbillede 2021-04-20 kl  13 03 57" src="https://user-images.githubusercontent.com/44894156/115385949-12c7ef00-a1d9-11eb-8fce-267cef7c49e0.png">

- Kør følgende script i Neo4j Browser

```
LOAD CSV WITH HEADERS FROM 'file:///2021-02-dorset-street.csv' AS crimes

WITH crimes WHERE NOT crimes.Location IS null AND NOT crimes.`Crime ID` IS null AND NOT crimes.`Crime type` IS null

MERGE (c:crimes {id: crimes.`Crime ID`, location:crimes.Location, crime:crimes.`Crime type` })

return c
```
##### Use Cypher and the Neo4j browser tools. 

### Based on your data sample, show

#### Which is the location with highest number of crimes?
```
match (c:crimes) 

return c.location, count(*) as occurences ORDER BY occurences DESC LIMIT 1
```

#### Which is the most common crime?
```
match (c:crimes)

return c.crime, count(*) as occurences ORDER BY occurences DESC LIMIT 1
```
