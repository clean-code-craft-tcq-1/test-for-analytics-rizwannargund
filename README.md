# Test for Analytics

Design tests for Analytics functionality on a Battery Monitoring System.

Fill the parts marked '_enter' in the **Tasks** section below.

## Analysis-functionality to be tested

This section lists the Analysis for which _tests_ must be written.

Battery Telemetrics are collected and stored on a server.
Data for a month is stored in a [csv file](https://en.wikipedia.org/wiki/Comma-separated_values).

Analysis must be done on this csv file to find the following:
- minimum
- maximum
- count of breaches (how many times did it cross the threshold in a month?)
- record trends (date & time when the reading was continuously increasing for 30 minutes)

A PDF report of the analysis must be stored every week.
Notification must be sent when a new report is available.

## Tasks

### List Dependencies

List the dependencies of the Analysis-functionality.

1. Access to the Server containing the telemetrics in a csv file
2. Access to the csv file
3. Has data in csv
4. PDF generator component
5. Place to store the PDF report
6. Email account if notification is via email service



### Mark the System Boundary

What is included in the software unit-test? What is not? Fill this table.

| Item                      | Included?     | Reasoning / Assumption
|---------------------------|---------------|---
Battery Data-accuracy       | No            | We do not test the accuracy of data
Computation of maximum      | Yes           | This is part of the software being developed
Off-the-shelf PDF converter | Yes			| Need for pdf report generator
Counting the breaches       | Yes			| This is part of the software being developed
Detecting trends            | Yes			| This is part of the software being developed
Notification utility        | Yes			| This is part of the software being developed

### List the Test Cases

Write tests in the form of `<expected output or action>` from `<input>` / when `<event>`

Add to these tests:

1. Write minimum and maximum to the PDF from a csv containing positive and negative readings
2. Write "Invalid input" to the PDF when the csv doesn't contain expected data
3. Write number of times the breach crossed in a month from csv by counting to the PDF
4. Write date & time when the reading was continuously increasing for 30 minutes from csv to PDF
5. Write to PDF and save works
6. Write to confirm mock job runs on every week
7. Write to confirm mock notification works

(add more)

### Recognize Fakes and Reality

Consider the tests for each functionality below.
In those tests, identify inputs and outputs.
Enter one part that's real and another part that's faked/mocked.

| Functionality            | Input        | Output                      | Faked/mocked part
|--------------------------|--------------|-----------------------------|---
Read input from server     | csv file     | internal data-structure     | Fake the server store
Validate input             | csv data     | valid / invalid             | None - it's a pure function
Notify report availability | emailid 	  | boolean flag                | Mock email sending
Report inaccessible server | IP addr 	  | connection state		    | None - it's state verification
Find minimum and maximum   | csv data 	  | get minimum and maximum     | Fake csv data
Detect trend               | csv data 	  | get trend datetime          | Fake csv data
Write to PDF               | csv data/string | PDF file with content   	| Mock PDF provider
