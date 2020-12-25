# Soru 2 - 1980’den itibaren herhangi bir spor grubunda üst üste 3 veya daha fazla madalya almış atletleri bulalım.

```SQL
select * from (
select athlete,sport,
first_value(year) over(partition by athlete,sport order by athlete,year) as year1,
lead (year,1) over(partition by athlete,sport order by athlete,year) as year2,
lead (year,2) over(partition by athlete,sport order by athlete,year) as year3,
from semih_durmaz.summer_medals
order by athlete,sport)
where year3-year2=4 and year2-year1=4
```
