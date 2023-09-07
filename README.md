# Hackerank
Practise examples in hackerank
###**[Weather Observation Station 1](https://www.hackerrank.com/challenges/weather-observation-station-1)**

Query a list of CITY and STATE from STATION.

Input Format

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

**Solution**
```sql
SELECT CITY,STATE FROM STATION;       
```

``` sql
select distinct city 
from station 
where city like 'a%' or city like 'e%' or city like 'i%' or city like 'o%' or city like 'u%'; 

```
