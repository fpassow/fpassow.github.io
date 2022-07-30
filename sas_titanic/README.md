# Working with the Titanic Data Set in SAS

I downloaded the Titanic dataset from 
github at [https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv](https://raw.githubusercontent.com/pandas-dev/pandas/main/doc/data/titanic.csv)
then uploaded it to [SAS Studio online](https://welcome.oda.sas.com/home).

```
 /* Import the data from the .csv into a temporary data set. */
proc import file="/home/u61913325/titanic/titanic.csv"
    out=work.titanic_raw
    dbms=csv
    replace;
run;

/* Select columns to work with and create a computed column "women_and_children" */
data titanic replace;
set titanic_raw;
women_and_children = (Age <= 15) or (Sex = "female");
keep Survived Sex Age Fare Embarked women_and_children;
run;

/* Compare survival rates for women and children vs everyone else. */
/* Observation: Pure SAS syntax can do everything, or almost everything.
   But if you already know SQL, it's much easier to use "proc sql" and write SQL in SAS. */
proc sql;
		select women_and_children, avg(Survived)*100 as percent_survived
		from work.titanic
		group by women_and_children
		order by percent_survived desc;
quit;
```


|women_and_children|percent_survived|
| --- | --- |
|1|56.48536|
|0|17.43341|

