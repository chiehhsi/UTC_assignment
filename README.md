# UTC_assignment

Project Data:

The given data is the scheduling information of pace suburban bus service in the suburban cook counties. The data is in the text file format which have been provided by the General Transit feed Service ‘GTFS’. There are 5 text files (Calendar, Stops, Stop_times, Routes, Trips) which you’ll use for creating a final table with requested filed in a separate column.
Below are the few steps and details about the data.
 - Unzip the file and extract all the files
 - All the text files have to be exported into database tables-(when exporting into a table, use any relevant data type for each file by looking the original text file)
 - Calendar text file has weekday fields such as Monday, Tuesday, etc and having ‘0’ and ‘1’ values which means that having ‘no service’ and ‘service’ respectively.
 - Join the tables with the common field between the two entities
 - The ‘stop_times’ table has arrival and departure times fields where some of the records are showing above 24 hr format, that is, for example a record showing 24:10:10 in Monday needs to be corrected as 00:10:10 and should be noted under the following day, Tuesday.

### 1st assignment (Hours_of_Service.ipynb)
---
We want the hours of service for each unique (stop_id, route_id) pair.  Please submit the Python code and your output in the following format:
 
- Stop_id, route_id, earliest arrival time, latest  departure time, hours of service, Monday.
- Also provide the grand total of the hours of service (for all stops and routes) at the top of the sheet.

**Output Sheet: Assignment1.xlxs

**Explaination:

Use Pandas Package to export txt file into dataframe and merge the Calendar, Stop_times, Routes and Trip text files' columns to get the modified_table with columns( service_id, monday, route_id, trip_id, arrival_time, departure_time, stop_id, stop_sequence). If you sort the table by (route_id, stop_id), you will see lots of duplicate with different service_id. Therefore, I create the unique keypair, (route_id,stop_id) and use keypair as selector, from modified_table, to get the separate table set. Then check the column Monday to make sure this route, or stop, have services on Mondays. The earliest time is the minimum value appears in column arrival_time of those who serves on Monday, and on the other hand, the maximun is the last time. If we subtract these two numbers, and we will get hours of service of this route_id and stop_id. Moreover, if there is no '1' appears in column Monday, we still get the earliest_time and last_time for corresponding column, however, set the hours_of_service = 0. In the end, sum all the value in column hours_of_service and get the grand total.

### 2nd assignment (Zone_distance.ipynb)
---
Output in the following format:
Zone_id label (not coordinates), 1st nearest neighbor zone label (not coordinates) : distance (in miles), … , 6th nearest neighbor zone label (not coordinates) : distance (in miles).

**Output Sheet: Assignment2.xlxs

**Explaination:

As above, I use Pandas Package to export txt file into dataframe, however, the raw txt file has unmatch columns. Therefore, I split the value and tear into two matching columns to make the right table with columns( zone09, lantitude, logitude). I use a k-dimensional tree to organize our points in our 3-dimensional space, which is a data structure from computer science that can help with searches over multidimensional keys, and Scipy has KDtree implemented, and for searches it uses euclidian distance by default (p=2). Hence, I defined the cartesian function to return point and appended to KDtree. And I defined find_neighbor function to implement tree query by send the point and the return number of nearest neighbor. The reason why k=7 is that the closest zone will be the same zone itself, so we cannot include that. Moreover, the return distance of tree query is in kilometer, so I multiply the ratio(0.621317) to change into miles and I store lable_id and distance as a tuple for the indice of the final table.
