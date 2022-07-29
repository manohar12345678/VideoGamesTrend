# Data set:
Here we have a dataset called vgsales-2016. This data set is basically the sales of the various video games on different platforms over the years.

Agenda is to find two things:
1. Idenfying the average globale sales before 2005 and after 2005.
2. Create a new column that labels records before 2005 as 'pre-2005' and after 2005 as 'post-2005'

# Imoprting the Dataset:

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


