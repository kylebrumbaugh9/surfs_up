# surfs_up

## Overview of Statistical Analysis

### Purpose
The main purpose for this analysis was to determine if the temperature in Oahu, Hawaii would support keeping a surf and ice cream shop business alive year-round. 

### Sources and technology used

Database: a SQLite database was provided that showed temperature data in Oahu, Hawaii from 2010-2017

Technology: Jupyter Notebook, Python, pandas, numpy, SQLAlchemy, and VS Code. I downloaded the SQLite and SQLite Viewer extensions into VS code so that I could visually see the data and the structure of the data from the SQLite database (see image below)

![SQLite_In_VSCode](https://user-images.githubusercontent.com/114685724/209010641-208980a1-087d-4ecb-bfca-10a7f1508d7c.png)

## Results

There are 3 main differences in the temperatures of Oahu, Hawaii in June and December

- The first difference is the mean temperature. It's nearly 4 degrees cooler in June than December: 71.0 degrees vs 74.9 degrees
- The second main difference is the minimum temperature, or the "floor". It's 8 degrees cooler in June than December: 56 degrees vs 64 degrees
- The last difference I noticed was the max temperature, or the "ceiling". It's only 2 degrees cooler in June than December: 83 degrees vs 85 degrees

### Supporting images

June Stats

![JuneTempSummaryStats](https://user-images.githubusercontent.com/114685724/209011338-094446e1-952d-4acc-aaa8-9df69fe11a75.png)

December Stats

![DecemberTempSummaryStats](https://user-images.githubusercontent.com/114685724/209011381-91690046-81c6-44b1-bf81-4472ec463adf.png)

## Summary

Overall, December is warmer on average than June, but only by about 4 degrees Fahrenheit. This is a pretty negligible change of temperature over the course of 6 months, so I believe it is safe to say that the temperature in Oahu, Hawaii is consistenly warm. If temperature was the only factor, a surf and ice cream shop would certainly be appropriate to open in Oahu, Hawaii.

### Future queries to run

I think we could use a little more research on the precipitation levels between these two seasons. I would want to see how rainy it is on average between June and December. While the temperature is appropriate for eating ice cream and surfing, if it's raining, I wouldn't say that that's a great combination. I would write a query like this to compare June to December, where "xx = 06" for June and "xx = 12" for December:

session.query(Measurement.date, Measurement.prcp).filter(Measurement.date.like('%-xx-%')).all()

I think we should also look at each year specifically to see if the "cold years" were an anomaly. The majority of the temperatures are in the mid/low 70s but those min values are troubling me. I would want to look temperatures over time and see if there was a specific year where both June and December were cold so that I could chalk those minimum values up to chance or not. I would use a query like this:

results = session.query(Measurement.date, Measurement.tobs).group_by(Measurement.date).all()
