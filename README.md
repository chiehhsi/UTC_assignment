# UTC_assignment

Project Data:

The given data is the scheduling information of pace suburban bus service in the suburban cook counties. The data is in the text file format which have been provided by the General Transit feed Service ‘GTFS’. There are 5 text files (Calendar, Stops, Stop_times, Routes, Trips) which you’ll use for creating a final table with requested filed in a separate column.
Below are the few steps and details about the data.
 - Unzip the file and extract all the files
 - All the text files have to be exported into database tables-(when exporting into a table, use any relevant data type for each file by looking the original text file)
 - Calendar text file has weekday fields such as Monday, Tuesday, etc and having ‘0’ and ‘1’ values which means that having ‘no service’ and ‘service’ respectively.
 - Join the tables with the common field between the two entities
 - The ‘stop_times’ table has arrival and departure times fields where some of the records are showing above 24 hr format, that is, for example a record showing 24:10:10 in Monday needs to be corrected as 00:10:10 and should be noted under the following day, Tuesday.

Deliverables:
 - Calculate the hours of service, that is, the number of hours for Monday for each bus stop that has service which should be depicted with a separate column in the table
 - The final new table should have fields: stop_id, Monday, route_id, hours of service
 - You can come up with your own method and own choice of your comfortable software program
 - Please provide us the final table with a brief write-up of explaining the methods that you followed in the process

### 1st assignment (Hours_of_Service.ipynb)
---
We want the hours of service for each unique (stop_id, route_id) pair.  Please submit the Python code and your output in the following format:
 
- Stop_id, route_id, earliest arrival time, latest  departure time, hours of service, Monday.
- Please also provide the grand total of the hours of service (for all stops and routes) at the top of the sheet.

Output Sheet: Assignment1.xlxs
 
### 2nd assignment (Zone_distance.ipynb)
---
Please submit your Python code and output in the following format:
Zone_id label (not coordinates), 1st nearest neighbor zone label (not coordinates) : distance (in miles), … , 6th nearest neighbor zone label (not coordinates) : distance (in miles).

Output Sheet: Assignment2.xlxs
