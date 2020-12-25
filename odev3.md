# Soru 3 - Günün her bir dakikası için aktif kullanıcı sayısının hesaplanması.

``` SQL

with aktif  
as  
(select timestamp_trunc(view_ts,minute) as zaman,count(deviceid) as cihaz from semih_durmaz.pageview group by zaman order by zaman)  
select zaman,sum(cihaz) over (order by zaman rows between 4 preceding and 0 following) as aktif_toplam  
from aktif  

```
