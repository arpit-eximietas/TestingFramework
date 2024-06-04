# TestingFramework

Testing Framework for Zebra

Pre-requisites:
CI/CD pipeline with newman, python and robot framework pre installed.
Newman a CLI runner for postman
Robot framework 
Python

Steps:

Export Postman Collection and Environment:
Open Postman.
Select the desired collection.
Click on the "..." icon.
Choose "Export".
Select "Collection v2" format.
Repeat the process for the environment.

Push Files to Git and Merge with Main:
Navigate to your local Git repository.
 Add the exported files.
git add <collection_file> <environment_file>
 Commit changes.
 git commit -m "Add Postman collection and environment files"
Push to Git repository
git push origin main
 Merge with the main branch if necessary.

Write Robot Framework Script for Newman Execution:
Install Newman if not already installed.
 npm install -g newman
Create a `.robot` file for Robot Framework script.
Write test cases using Robot Framework's syntax
Use the `Run Process` keyword to execute Newman.
Specify options like collection file, environment file, etc.

Generate HTML and JSON Report for Execution:
After executing Newman with Robot Framework, it generates HTML and JSON reports automatically.
These reports contain test execution results, including pass/fail status, response times, etc.

Publish HTML and JSON Reports:
Identify the location of generated HTML and JSON reports.
Copy or move these files to a location accessible to others (e.g., a web server, shared folder)
Share the URL or path to the HTML report for others to view.
Optionally, compress the JSON report for distribution.
