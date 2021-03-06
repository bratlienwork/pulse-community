## Framework and Tool Parsers

- The name of the parser indicates the framework or tool as well as the expected results output data format.  HTML is not supported nor encouraged as a standardized data format.
- All framework and tool parsers listed here leverage the delivery scripts and UpdateQTestWithResults.js submission method found in this repository, except as noted in the next point.  See the 'delivery' and 'qtest' subdirectories for more information.
- Users leveraging the qTest Scenario Plugin for Jira will use UpdateQTestAndLinkScenarioRequirements.js instead to deliver results to qTest and the 
- These actions are NOT compatible with the stock Pulse 9.1 BDD workflow rules as these rules incorporate standards and conventions not used in the stock rules.
- These actions are NOT compatible with the parsers included in Launch due to a difference between leveraged qTest backend API endpoints, however Pulse actions may be used in lieu of a Launch parser by skipping parser selection in the Universal Agent and shipping the results to the Pulse webhook endpoint instead.

### AllureXML.js
This parser will consume XML results from the Allure framework.  All items marked as test cases in the results files will be marked as test cases in qTest.

### AllureCustomXML.js
This parser will consume XML results from the Allure framework, but at a higher level.  All items marked as test cases in the results file will be marked as test STEPS in qTest.  Use this if your framework outputs test steps as individual test cases.

### CucumberJSON.js
This is a parser for Cucumber for Java 4.0+ JSON result files.  Earlier versions of Cucumber need to use the Legacy parser.  Required for the qTest Scenario workflow.

### CucumberLegacyJSON.js
This is a parser for Cucumber for Java versions prior to 4.0 JSON result files.  This is not compatible with Cucumber 4.0+.  You should probably upgrade.

### CypressMochawesome.js
This parser consumes JSON results from the Cypress.io Mochawesome frameworks.  Ship the consolidated 'report.json' file to this parser.

### JUnitXML.js
This is a parser for JUnit XML result files.  It may also support XUnit result files.

### NUnitXML.js
This parser is for NUnit XML result files.  It reports tests at the method level, so there are no test steps.  Failures are annotated and attached to the test runs in qTest.

### PostmanJSON.js
This is a parser for Postman API endpoint test results output in JSON.  This is a more detailed parser than the one included with Launch, and thus not compatible with results already consumed by Launch.

### QuerySurgeXML.js
This is a parser for the XML output provided by the QuerySurge testing tool.

### ReadyAPIXML.js
This is a parser for the XML output provided by the ReadyAPI testing tool.  Expected results will be in a test suite and not individual tests.

### SerenityJSON.js
This is a parser for the Serenity BDD XML format, a Cucumber derivative.  This parser has been submitted for public use by our friends at Specsavers UK.

### SonarQubeJSON.js
This is a parser for the SonarQube JSON format for code quality and assurance.  Leverage the webhook calls in SonarQube, please see this article to configure and review the expected format: https://docs.sonarqube.org/latest/project-administration/webhooks/

### SpecFlowXML.js
This is a parser for Tricents SpecFlow product TRX XML result files.  It does not support HTML report output.

### TestNGXML.js
This is a parser for TestNG XML results files.  It does not support Extent HTML reports.

### ToscaXML.js
This is a parser for Tricentis Tosca JUnit XML results files.  It parses the test steps from the non-standard plaintext tags inside the file.  It is not compatible with results already consumed by Launch and the built-in integration and is meant for CI Pipeline usage only via ToscaCI.  It is a work in progress and may require customization for your environment.
