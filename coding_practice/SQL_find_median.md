Location: https://www.hackerrank.com/challenges/weather-observation-station-20/problem
# Question
A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to  decimal places.


# My solution (follows instructions)
```sql
with ranks as (
select LAT_N,
row_number() over (order by LAT_N) as rk,
count(*) over () as cnt from STATION)
select round(avg(LAT_N),4) from ranks where rk in ((cnt+1)/2, (cnt+2)/2)
```
