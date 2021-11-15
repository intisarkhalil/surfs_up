# surfs_up
## Overview of the Project
The purpose of this analysis is to analyze weather data that has been stored in SQLite database [Database](). The client wants more information about temperature trends before opening the surf shop. Specifically, he wants temperature data for the months of June and December in Oahu, in order to determine if the surf and ice cream shop business is sustainable year-round.  In order to extract the data in the SQLite database, we used **SQLAlchemy** to connect and generate queries to get the necessary information needed for our analysis. We use **Jupyter Notebook** and **SQLite** and **AQLAlchemy**.

### The Analysis and challenges
1. Determine the summary statistics for June:
2. Determine the summary statistics for December:
### Methodology:
1. Import dependencies.
    - ```import pandas as pd```
    - ```import numpy as np```
    - ```import sqlalchemy```
    - ```from sqlalchemy.ext.automap import automap_base```
    - ```from sqlalchemy.orm import Session```
    - ```from sqlalchemy import create_engine, func```

2. Create the engine search. ```engine = create_engine("sqlite:///hawaii.sqlite")```
3. Reflect an existing database into a new model ```Base = automap_base()```
4. Reflect the tables. ```Base.prepare(engine, reflect=True)```
5. Save references to each table. 
    - ```Measurement = Base.classes.measurement``` 
    - ```Station = Base.classes.station```
7. Create our session (link) from Python to the DB. ``` session = Session(engine)```
8. Import the SQLAlchemy extract function.  ```from sqlalchemy import extract```
9. Write a query that filters the Measurement table to retrieve the temperatures for each month. 

    - ```results = session.query(Measurement.date, Measurement.tobs).\```
    - ```filter(extract('month', Measurement.date) == 6).all()```

9. Convert the June temperatures to a list. ``` temps_june=list(results) ```

10. Create a DataFrame from the list of temperatures. 

    - ``` df=pd.DataFrame(temps, columns=['date', ' Temperatures']) ```
    - ``` df.set_index(df['date'], inplace=True)```
    
11. Calculate and print out the summary statistics for the June temperature DataFrame. ``` df.describe()```
## Results:

After extracting weather data for June and December, and making  statistical summary. The statistical summary shows the differences over these two months.

![1](https://user-images.githubusercontent.com/62036983/141722892-afe08c4c-0c1c-4b50-9169-2e44b93d392c.png)

1. ```The mean temperature for the months of June and December is (75) and (71) (in each data set, the mean and median are equal indicating that the distribution is symmetric).```
2. ```The June and December showed a similar standard deviation for the temperature data.```
3. ```There are no significant fluctuations in temperature throughout the year.```

![3](https://user-images.githubusercontent.com/62036983/141722841-537a306f-affd-43f0-a8e9-c01801b4052d.png)

## Summary
The temperature in Oahu, Hawaii is relatively the same throughout the year. In addition to extracting rainfall data during the months of June and December, as the results of precipitation in those months showed the following:

     • The average precipitation for the month of June was 13.6% with a standard deviation of 0.33.
     • The average rainfall for the month of December was 21.6%, with a standard division of 0.54.
    
These results indicate that Oahu, Hawaii is a good location for investing in the Surfs business.

![4](https://user-images.githubusercontent.com/62036983/141722792-8acc8982-6e08-460a-a5dc-e4d647430b7e.png)


