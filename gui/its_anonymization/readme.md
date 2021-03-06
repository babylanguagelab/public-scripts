## Introduction:
This program takes all the .its files from a folder and removes information that might be used to identify the child, based on the user's selections.  It will generate a new folder that ends with "processed" at the place where the original folder is. It will also creates a report file that lists the old and new information for any fields that have been deleted or altered. Deletion of some information may prevent ADEX from functioning properly. 

## Requirement:
* [python 2.7](https://www.python.org/downloads/release/python-2710/)
* [gtk-3](https://wiki.gnome.org/action/show/Projects/PyGObject?action=show&redirect=PyGObject)

## How To Run:
```shell
python main.py
```
* Step 1: Select the folder that contains its files.
* Step 2(optional): Configure the options for sensitive information in its files. Depending on your participant labelling system, you may or may not want to change these information.
* Step 3: Run.

## Sensitive Information:
### Identify Info:
1. Serial Number: keep, fuzz[default->0]
2. Gender: keep[default], delete
3. Algorithm Age: keep[default], delete 
4. Child ID: keep, fuzzy[default->0]
5. child Key: keep, fuzzy[default->0] 

## Time Info:
1. Enroll Data: keep, delete[default]
2. DOB & Clock Time: keep, fuzzy[default->DOB will be set as 2000-01-01 and clock time will recalculate after that.]
3. Time Zone: keep, delete[default]
4. UTC Time: keep, delete[default]

## xpath for ITS file:
./ProcessingUnit/UPL_Header/TransferredUPL/RecordingInformation/TransferTime/LocalTime
./ProcessingUnit/UPL_Header/TransferredUPL/RecordingInformation/TransferTime/TimeZone 
./ProcessingUnit/UPL_Header/TransferredUPL/RecordingInformation/TransferTime/UTCTime 
./ProcessingUnit/UPL_Header/TransferredUPL/RecorderInformation/SRDInfo/SerialNumber 
./ProcessingUnit/UPL_Header/TransferredUPL/ApplicationData/PrimaryChild/ChildKey 
./ProcessingUnit/UPL_Header/TransferredUPL/ApplicationData/PrimaryChild/DOB
./ProcessingUnit/UPL_Header/TransferredUPL/ApplicationData/PrimaryChild/Gender 
./ChildInfo/algorithmAge
./ChildInfo/gender
./Recording/startClockTime
./Recording/endClockTime
./Bar/startClockTime
./Bar/Recording/startClockTime
./Bar/Recording/endClockTime
./Bar/Recording/FiveMinuteSection/startClockTime
./Bar/Recording/FiveMinuteSection/endClockTime
./ExportData/Child/id
./ExportData/Child/EnrollDate
./ExportData/Child/ChildKey
./ExportData/Child/DOB
./ExportData/Child/Gender
