<h2 align="center">Channel 8, the local community TV station</h1>

# Teleprompt Script for the Continuity Announcer <img align="right" width="200" height="300" src="https://github.com/kariycha/TVPrompt/blob/main/TelePrompter2.png">

### Author: CK 2021-Jul-2021  
## Objective
To write out the teleprompt script that the continuity announcer reads during the credits of each program (yezz, good ol' days!). The script should tell the viewer which program is finishing and what time it is finishing, which show is about to be played and which show is on after that.

## Background
This program is written in Python 3.7 environment. File name: test.py. Python libraries used: datetime, numpy, pandas, and sys

## What you should pass to the program (inputs)
1.   CSV (**C**omma **S**eparated **V**alues) file containing the TV guide. This is a mandatory input. If the data in the file is not valid then teleprompt script will not be generated. Mandatory fields in the file are:
  * title - Text format
  * utc_start_date - Date format dd/mm/yyyy e.g. 07/07/2021
  * utc_start_time - Time format HH:MM e.g. 03:24
  * running_time   - Integer format, duration in seconds e.g. 3600
  
     Note: "rating" column can be empty, however in the teleprompt it will say "rating is not available" 
Snippet of a sample file is shown below...
<p align="center">
  <img width="600" height="500" src="https://github.com/kariycha/TVPrompt/blob/main/CVSFile.PNG">
</p>

2.   Date and Time in ISO 8601 format e.g. 2021-06-20T05:37:22+10:00. This is optional. However, if not provided machine's local datetime will be used

## What to expect as output from the program
The program will scan the CSV file and extract the TV program that's running at the date time specified as input or machine local time(if date time not provided). Then determine the next the programs to follow. Details output are:
* Title and Ending time of the TV program running at the date and time specified
* Title and Rating of the next program to follow
* Title of the program to follow the next program
