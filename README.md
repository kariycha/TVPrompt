<h2 align="center">Channel 8, the local community TV station</h1>

# Teleprompt Script for the Continuity Announcer <img align="right" width="200" height="300" src="https://github.com/kariycha/TVPrompt/blob/main/TelePrompter2.png">
### Author: CK    
2021-Jul-12  
## Objective
To write the teleprompt script that the continuity announcer reads during the credits of each program (just like good ol' days!). The script should tell the viewer which program is finishing and what time it is finishing, which show is about to be played and which show is on after that.
## Background
This program is written in Python 3.7 environment. File name: run.py. Standard Python libraries used: datetime and sys
## What you should pass to the program (inputs)
1.   CSV (**C**omma **S**eparated **V**alues) file containing the TV guide. This is a mandatory input. If the data in the file is not valid then the teleprompt script will not be generated. Required fields in the file are:
  * title - Text format
  * utc_start_date - Date format dd/mm/yyyy e.g. 07/07/2021
  * utc_start_time - Time format HH:MM e.g. 03:24
  * running_time   - Integer format, duration in seconds e.g. 3600  
     Notes: 
     * "rating" column can be empty, however in the teleprompt it will say "rating is not available" 
     * If the CSV file is in a different location, full path to the file must be provided e.g. *D:\Data\Python\TVPrompt\example.csv* 

Snippet of a sample file is shown below...
<p align="center">
  <img width="500" height="400" src="https://github.com/kariycha/TVPrompt/blob/main/CVSFile.PNG">
</p>

2.   Date and Time, in ISO 8601 format e.g. 2021-06-20T05:37:22+10:00. This is optional. However, if not provided machine's local datetime will be used
## What to expect as output
The program will scan the CSV file and extract the TV program that's running at the date time specified as input or machine local time(if date time not provided). Then determine the next the programs to follow. Output details are:
* Title and Ending time of the TV program running at the date and time specified
* Title and Rating of the next program to follow
* Title of the program to follow the next program

e.g. *That was Game of Thrones ending at 20/06/2021 06:20, up next is Westworld which is rated MA15+ and coming up later is Succession.*\
when no program details are available:    e.g. *No program details available for 2021-06-19T15:27:30+10:00.*
## How to use the program
Run the program *run.py* as shown below:
````python 
>>>python run.py test.csv 2021-06-20T05:37:22+10:00
That was Game of Thrones ending at 20/06/2021 06:20, up next is Westworld which is 
rated MA15+ and coming up later is Succession.
````
## Common Pitfalls
Here are some errors that might occur
1. CSV file is not in the specified location or fullpath is not provided
2. Data formats in the CSV file are incorrect espcially start date and time
3. Date and time provided are outside of the TV guide (CSV file) 
4. Date and time provided not in the ISO 8601 format
## Future improvements
More data validations for CSV file can be implemented: 
   * Checking date and time are in correct format
   * How to handle if there are multiple entries for the same timeslot

