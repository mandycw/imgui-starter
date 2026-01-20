# imgui-starter

Using the provided code provided here you have a base Dear IMGUI project for Windows and macOS. There is a basic CMakefile in this project that includes the necessary files to create an application that brings up just a basic screen.

You must add a logging system to this code that you will be using THROUGHOUT the quarter. This logging system should do two things.

It should be able to log to a Dear IMGUI debug console
It should also log its output to a file.

For the submission, make a branch of this repo and submit a new GitHub URL

I worked on Windows.

Since Dear IMGui is a new to me, I decdied to start with something simple such as creating the test buttons which will eventually create a warning/error log, etc. 

It was advised in the Discord to use singletons and a header file for all of the logging so I implemented that. Next was to add functionality to these buttons, I first created functions for each type of log that I wanted. Each function would have an AddLog function which was declared privately. The AddLog function uses the LogEntry struct which contains the timestamp, log type, message and color. AddLog creates an entry with this information, then, push_back() is used to add the information to logEntries. The function deletes old logs if the max limit is reached, logs to terminal and if the log file is open, writes the logs to a file called log.txt. 
 
To create the logging levels, I created a static bool that checked whether each type of log was off or on. Then a for loop that iterates through the log entries to check the type and static bool. If the bool is disabled then those log entry types are skipped and do not show on the log window. To make this accessible to the user, I created a list of checkboxes in the options menu using ImGui that allows the user to check which type of log they want to see. 

For user input, I created a function for text input that includes a char buffer, strncpy, and InputText from ImGui. This allows the user to modify the text and updated accordingly. Space was reserved for the text input box so the input box would be at the bottom of the window. 

To log to file, logFile is declared privately in Logger() to open log.txt in append mode. Writing to the file happens in addLog(). 

To make the window actually show up, I added one line of code to Application.cpp which rendered the log window. 

I personally did not ask any questions. Other classmates had asked questions previously which had answered my questions as well. 