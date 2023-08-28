# Project Title: streaming-02-multiple-processes

> Multiple processes accessing a shared resource concurrently

## Overview

This example starts a shared database and multiple processes.

The processes represent multiple users, or locations, or programs 
hitting a shared database at the same time. 

## Prerequisites

1. Git
1. Python 3.7+ (3.11+ preferred)
1. VS Code Editor
1. VS Code Extension: Python (by Microsoft)

The following modules are required:


| Module          | Version  |
|-----------------|----------|
| logging         | 0.5.1.2  |
| multiprocessing | 3.11.4   |
| datetime        | 3.11.4   |
| sqlite3         | 2.6.0    |
| os              | 3.11.4   |
| platform        | 1.0.8    |
| sys             | 3.11.4   |
| time            | 3.11.4   |

## Task 1. Fork 

Fork this repository ("repo") into **your** GitHub account. 

## Task 2. Clone

Clone **your** new GitHub repo down to the Documents folder on your local machine. 

## Task 3. Explore

Explore your new project repo in VS Code on your local machine.

## Task 4. Execute Check Script

Execute 00_check_core.py to generate useful information.
<i>This ran without issues</i>

## Task 5. Execute Multiple Processes Project Script

Execute multiple_processes.py.

Read the output. Read the code. 
Try to figure out what's going on. 

1. What libraries did we import?
- datetime
- logging
- multiprocessing
- os
- platform
- sqlite3
- sys
- time
1. Where do we set the TASK_DURATION_SECONDS? 
<i> Where we declare the program constants </i>
1. How many functions are defined? 7
1. What are the function names? recreate_database(), create_table(),drop_table(),insert_pet(process, name, breed),process_one(), process_two(), process_three()
1. In general, what does each function do? drop and recreate a database, create a table in the database, drop the table if it exists, insert a pet into pets table, logs the start of the process and then calls the `insert_pet` function twice to insert pet data for a specific category.
    
1. Where does the execution begin? if __name__ == "__main__": block is where the execution of a script begins when the script is run as the main program
1. How many processes do we start? 3
1. How many records does each process insert? 2

In this first run, we start 3 processes, 
each inserting 2 records into a shared database 
(for a total of 6 records inserted.)

In each case, the process gets a connection to the database, 
and a cursor to execute SQL statements.
It inserts a record, and exits the database quickly.

In general, we're successful and six new records get inserted. 

## Task 6. Execute Multiple Processes Script with Longer Tasks

For the second run, modify the task duration to make each task take 3 seconds. 
Hint: Look for the TODO.
Run the script again. 
With the longer tasks, we now get into trouble - 
one process will have the database open and be working on it - 
then when another process tries to do the same, it can't and 
we end up with errors. 

## Task 7. Document Results After Each Run

To clear the terminal, in the terminal window, type clear and hit enter or return. 

`clear`

To document results, clear the terminal, run the script, and paste all of the terminal contents into the output file.

Use out0.txt to document the first run. 

Use out3.txt to document the second run.


-----

## Helpful Information

To get more help on the early tasks, see [streaming-01-getting-started](https://github.com/denisecase/streaming-01-getting-started).


### Reading Error Messages

Python has pretty helpful error messages. 
When you get an error, read them carefully. 

- What error do you get? I received a datbase is locked error

### Database Is Locked Error

Do a web search on the sqlite3 'database is locked' error.

- What do you learn? <i>This occurs when multiple processes or threads are trying to access an SQLite database concurrently, and one process holds an exclusive lock on the database that prevents other processes from performing certain operations.</i>
- Once a process fails, it crashes the main process and everything stops. 

### Deadlock

Deadlock is a special kind of locking issue where a process 
is waiting on a resource or process, that is waiting also. 

Rather than crashing, a system in deadlock may wait indefinitely, 
with no process able to move forward and make progress.

### Learn More

Check out Wikipedia's article on deadlock and other sources to learn how to prevent and avoid locking issues in concurrent processes. 

## Additional Resources

1. For more information about Git in VS Code, see [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview).
1. For more information about editing Markdown in VS Code, see [Markdown and Visual Studio Code](https://code.visualstudio.com/docs/languages/markdown).

## Acknowledgments

I would like to acknoledge both Stackoverflow and ChatGPT as an instrumental aid in the development of this project.