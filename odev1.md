# Soru 1 - 1980’den itibaren spor grubu bazında en çok madalya alan 1. 3. 5. ülkeyi bulalım.

```SQL
select * from (
select country,count(1) as medal, row_number() over(order by count(1) desc) as row 
from semih_durmaz.summer_medals 
where year >=1980  
group by country  
order by count(1) desc)
where row in (1,3,5)
```
