## Data set:
Here we have a dataset called vgsales-2016. This data set is basically the sales of the various video games on different platforms over the years.

Agenda is to find two things:
1. Idenfying the average globale sales before 2005 and after 2005.
2. Create a new column that labels records before 2005 as 'pre-2005' and after 2005 as 'post-2005'

## Imoprting the Dataset:

pip install pymysql

## import required libraries
import pandas as pd
from sqlalchemy import create_engine
import pymysql
## creating engine
engine = create_engine('mysql+pymysql://root:@localhost:51211')
## connection string
conn = engine.connect()
### Create a new column that labels records before 2005 as 'pre-2005' and after 2005 as 'post-2005'
complex_df = pd.read_sql('''SELECT *, case
WHEN Year > 2005 THEN "post 2005"
WHEN Year < 2005 THEN "pre 2005"
ELSE null
END AS Released
from data1202.videogamesales''', conn)

complex_df.head(20)

## Output

0	1	Wii Sports	Wii	2006	Sports	Nintendo	41.49	29.02	3.77	8.46	82.74	post 2005
1	2	Super Mario Bros.	NES	1985	Platform	Nintendo	29.08	3.58	6.81	0.77	40.24	pre 2005
2	3	Mario Kart Wii	Wii	2008	Racing	Nintendo	15.85	12.88	3.79	3.31	35.82	post 2005
3	4	Wii Sports Resort	Wii	2009	Sports	Nintendo	15.75	11.01	3.28	2.96	33.00	po

