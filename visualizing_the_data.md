# Visualizing the Data

**Open data is everywhere!**

Go to [https://data.melbourne.vic.gov.au/](https://data.melbourne.vic.gov.au/) and see how many data sources they have data on all aspects of Melbourne life! (seriously - look no further if you need to know the locations of all the public toilets, or the gradient of every footpath...)

**Example: data of pedestrian numbers in the CBD**

In this example we'll look at the dataset called 'Pedestrian Counts', which contains an hourly count for the number of people that passed a particular sensor in Melbourne. That's data every hour, on the hour at 18 locations, since 2009! And MATLAB didn't even bat an eyelid when I tried to load it up. (Ok, yes it did warn me I was opening a large text file, but it still worked).

** Sensor Locations**
1. Bourke Street Mall (North)
2. Bourke Street Mall (South)
3. NA
4. Town Hall (West)
5. Princes Bridge 
6. Flinders Street Station Underpass
7. NA
8. NA
9. Southern Cross Station
10. Victoria Point
11. Waterfront City
12. New Quay
13. Flagstaff Station
14. Sandridge Bridge
15. State Library
16. Australia on Collins
17. Collins Place (South)
18. Collins Place (North)

Two tools that are used again and again when exploring data are scatter plots (`scatter`) and histograms (`hist` and `histc`). *NB both of these plots can also be achieved using the `plot` function*