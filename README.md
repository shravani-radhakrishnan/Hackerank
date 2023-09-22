# Hackerank
practice examples in hackerank

The STATION table is described as follows:

|  Field | Type |
|---|---|
| ID  | NUMBER |
| CITY | VARCHAR2(21)   |
| STATE  | VARCHAR2(2)  |
| LAT_N |  NUMBER |
| LONG_W | NUMBER |

** 1. Query a list of CITY and STATE from STATION.**

**Solution**
```sql
SELECT CITY,STATE FROM STATION;       
```
** 2. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates. **

**Solution**
``` sql
SELECT distinct city 
FROM station 
WHERE city LIKE 'a%' or city LIKE 'e%' or city LIKE 'i%' or city LIKE 'o%' or city LIKE 'u%'; 
```
** 3. Query the 2 cities contained in STATION table with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
Let's say that CITY only has four entries: DEF, ABC, PQRS and WXY 
Sample Output: 
ABC 3 
PQRS 4  **

**Solution**
``` sql
SELECT CITY,LENGTH(CITY) from STATION order by Length(CITY) asc, CITY limit 1;  
SELECT CITY,LENGTH(CITY) from STATION order by Length(CITY) desc, CITY limit 1; 
```
** 4. Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates. **

**Solution**
``` sql
SELECT distinct city  
FROM station 
WHERE city LIKE '%a' OR city LIKE '%e' OR city LIKE '%i' OR city LIKE '%o' OR city LIKE '%u'; 
```
** 5. Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last  **

**Solution**
``` sql
SELECT distinct city   
FROM station  
WHERE lower(city) REGEXP '^[aeiou].*[aeiou]$' ; 
```
** 6. Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.   **

**Solution**
``` sql
SELECT distinct city   
FROM station  
WHERE upper(city) not like 'A%' and upper(city) not like 'E%' and upper(city) not like 'I%' and upper(city) not like 'O%' and upper(city) not like 'U%';
```
** 7. Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.  **

**SolutionS**
``` sql
SELECT distinct city    
FROM station   
WHERE (upper(city) not like 'A%' and upper(city) not like 'E%' and upper(city) not like 'I%' and upper(city) not like 'O%' and upper(city) not like 'U%') or (upper(city) not like '%A' and upper(city) not like '%E' and upper(city) not like '%I' and upper(city) not like '%O' and upper(city) not like '%U');
```
``` sql
SELECT DISTINCT city FROM station WHERE city RLIKE '^[^aeiouAEIOU].*|.*[^AEIOUaeiou]$'; 
```
``` sql
SELECT DISTINCT city FROM station WHERE upper(city) RLIKE '^[^AEIOU].*|.*[^AEIOU]$';   
```

** 8. Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates. **

**Solution**
``` sql
SELECT DISTINCT CITY  
FROM STATION   
WHERE upper(substr(CITY,1,1)) NOT IN ('A','E','I','O','U') and upper(substr(CITY,LENGTH(CITY),1)) NOT IN ('A','E','I','O','U'); 
```

--Problem Statement

/*
Given a table TRIANGLES that holds data for three fields namely A, B, C.
+-------------+------------+
| Column      |   Type     |
+-------------+------------+
| A           | INTEGER    |
| B           | INTEGER    |
| C           | INTEGER    |
+-------------+------------+
 
Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral   : It's a triangle with  sides of equal length.
Isosceles     : It's a triangle with  sides of equal length.
Scalene       : It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.
*/

```sql
SELECT CASE 
WHEN A + B <=C OR B + C <= A OR C + A <= B THEN 'Not A Triangle'
WHEN A = B AND B = C THEN 'Equilateral'
WHEN A = B OR B = C OR C = A THEN 'Isosceles'
ELSE 'Scalene'
END
FROM TRIANGLES;
```