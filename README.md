# Testing Framework for Zebra

This guide provides a framework for setting up a testing environment for Zebra using Newman, Robot Framework, and Python. Follow the steps below to export Postman collections, push files to Git, write Robot Framework scripts, generate reports, and publish them.

## Pre-requisites

Ensure that the CI/CD pipeline has the following pre-installed:
- Newman (a CLI runner for Postman)
- Robot Framework
- Python

## Steps

### 1. Export Postman Collection and Environment

1. Open Postman.
2. Select the desired collection.
3. Click on the "..." icon.
4. Choose "Export".
5. Select "Collection v2" format.
6. Repeat the process for the environment.

### 2. Push Files to Git and Merge with Main

1. Navigate to your local Git repository.
2. Add the exported files.
   ```sh
   git add <collection_file> <environment_file>
   ```
3. Commit changes.
   ```sh
   git commit -m "Add Postman collection and environment files"
   ```
4. Push to Git repository.
   ```sh
   git push origin main
   ```
5. Merge with the main branch if necessary.

### 3. Write Robot Framework Script for Newman Execution

1. Install Newman if not already installed.
   ```sh
   npm install -g newman
   ```
2. Create a `.robot` file for the Robot Framework script.
3. Write test cases using Robot Framework's syntax.
4. Use the `Run Process` keyword to execute Newman.
5. Specify options like collection file, environment file, etc.

### 4. Generate HTML and JSON Report for Execution

After executing Newman with Robot Framework, HTML and JSON reports are generated automatically. These reports contain test execution results, including pass/fail status, response times, etc.

### 5. Publish HTML and JSON Reports

1. Identify the location of generated HTML and JSON reports.
2. Copy or move these files to a location accessible to others (e.g., a web server, shared folder).
3. Share the URL or path to the HTML report for others to view.
4. Optionally, compress the JSON report for distribution.

## Example Robot Framework Script

```robot
*** Settings ***
Library           Process

*** Variables ***
${COLLECTION}     path/to/your/postman_collection.json
${ENVIRONMENT}    path/to/your/postman_environment.json
${REPORT}         newman_report.html
${REPORT_JSON}    newman_report.json

*** Test Cases ***
Run Newman Tests
    Run Process    newman run ${COLLECTION} -e ${ENVIRONMENT} -r html,cli,json --reporter-html-export ${REPORT} --reporter-json-export ${REPORT_JSON}
```

This script runs Newman with the specified collection and environment files and generates HTML and JSON reports.

## Notes

- Ensure that the path to the Postman collection and environment files is correct.
- Customize the `Run Process` command options as needed for your specific requirements.
- After execution, share the generated reports with your team for analysis.

By following these steps, you can effectively set up and utilize a testing framework for Zebra using Newman, Robot Framework, and Python.