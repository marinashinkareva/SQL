# Basic knowledge,example

**Structured Query language (SQL)** is standard language for dealing with Relational Databases.

> SQL programming can be effectively used to insert, search, update, delete database records.
> In fact it can do lot of things including, but not limited to, optimizing and maintenance of databases.
> For left join, to get results from left table and matching ones from the right table, use this command below

```sql
Select 	distinct s.AccessDateTime, 
		s.Keyword, 
		s.Search_Type, 
		d.Tab_Name, 
		s.Series_Code, 
		c.Product_code, 
		s.Link_URL, 
		s.SessionId
From search s
	Left Join detail_tab d	On s.SessionId = d.SessionId and s.Link_URL = d.Page_URL 
	Inner Join code_fix c 	On s.SessionId = c.SessionId and (s.Series_Code = c.Series_Code or d.Page_URL = c.Referer_URL)
Where s.Status = 'Link' # Limiting results to Link only for now 
	  and s.SessionId = '6e64b44adbec3cf7ad6cb820751159c0' 	

ORDER BY s.Keyword ASC;
```
