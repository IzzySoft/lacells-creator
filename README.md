lacells-creator
===============

Script for generating a cell tower database for NetworkLocation from the μg Project

The μg Project at https://github.com/microg is building a number of open source components to replace Google Mobile Services on Android phones. One of the older components is called NetworkLocation and it uses a on phone sqlite database to resolve the locations of cell towers seen by the phone.

The database is fairly old now so the scripts on this page will generate a new database and place it on the phone. The database generated with this script will have an additional field not used by NetworkLocation but used on some other software I have written.

Requirements
============

1. bash - Main script is written in bash
2. wget - Used to pull CSV files from OpenCellId and Mozilla Location Services
3. OpenCellID API Key - Needed to pull CSV files from OpenCellID. Get one for free at http://wiki.opencellid.org/wiki/How_to_join
4. sqlite3 - Used to generate the actual database for the phone
5. PHP - Command line script written in PHP is used to combine tower information that is duplicated between OpenCellId and Mozilla
6. adb - Used to push database file to the phone.

Setup
=====
The gen_lacells script needs to be edited to use your the OpenCellId API key.

How To Run
==========
1. Plug phone into computer using USB cable. Phone should have development options enabled to the computer can use adb to push the final file to the phone.
2. From the bash shell prompt enter:

> cd <directory gen_lacells is located in>
> ./gen_lacells

Other Considerations
====================
The OpenCellId project limits downloads to one per day per API key. So this script will only run correctly the first time it is run per day.