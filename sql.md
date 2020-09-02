SQL information
==
- standard    
    iec 9075, ansi

- range data   
    set number data to range string format
    ```sql
    select t.range as [score range], count(*) as [number of occurences]
    from (
    select case 
        when score between  0 and  9 then ' 0-9 '
        when score between 10 and 19 then '10-19'
        when score between 20 and 29 then '20-29'
        ...
        else '90-99' end as range
    from scores) t
    group by t.range
    ```
    or
    ```sql
    select (score/10)*10 || '-' || (score/10)*10+9 as scorerange, count(*)
    from scores
    group by score/10
    order by 1
    ```
    or   
    ```sql
    SELECT t.range AS ScoreRange,
        COUNT(*) AS NumberOfOccurrences
    FROM (SELECT CASE
                        WHEN score BETWEEN 0 AND 9 THEN '00-09'
                        WHEN score BETWEEN 10 AND 19 THEN '10-19'
                        ELSE '20-99'
                END AS Range
            FROM Scores) t
    GROUP BY t.Range
    ```
    
