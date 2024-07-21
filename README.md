# play-store-project
select b.category , prat,frat,
case 
	when prat > frat then 'paid'
    when frat > prat then 'free'
    else 'nahi pta'
    end as cato 
 from
(
select Category,round(avg(rating), 2) as 'frat' from playstore where type = 'free'
group by Category
)b
 inner join  
(
select Category, type,round(avg((rating)),2) as 'prat' from playstore where type = 'paid'
group by Category
)n
