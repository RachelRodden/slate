---
title: Boomerang Platform API Reference
---

# Introduction

Welcome to the Boomerang Platform REST API! We have a list of endpoints and parameters, along with a sample json response in the dark area to the right.

# Insights

Here we have endpoints for Boomerang Insights.

## App Builds

> This command returns JSON structured like this:

```json
[
	{
		"name": "name1",
		"version": "2.0",
		"startDate": "2017-04-24 23:39:55.0",
		"duration": "146",
		"status": "SUCCEEDED",
		"versionId": "fdjskaf2-jfd9-54sw-nge3-34s2l32i89iy48",
		"count": "",
		"coverage": "",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "fdjskaf2-jfd9-54sw-nge3-34s2l32i86dac8",
		"processType": "BUILD",
		"templateMode": "iOS"
	}
]
```

This endpoint gets all UrbanCode app builds for a given time period.

### HTTP Request

`GET /insights/builds/apps`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.

## Service Builds

> This command returns JSON structured like this:

```json
[
	{
		"name": "name1",
		"version": "2.0",
		"startDate": "2017-04-24 23:39:55.0",
		"duration": "146",
		"status": "SUCCEEDED",
		"versionId": "fdjskaf2-jfd9-54sw-nge3-34s2l32i89iy48",
		"count": "",
		"coverage": "",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "fdjskaf2-jfd9-54sw-nge3-34s2l32i86dac8",
		"processType": "BUILD",
		"templateMode": "mff.adapter"
	}
]
```

This endpoint gets all UrbanCode service builds for a given time period.

### HTTP Request

`GET /insights/builds/services`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## App Deploys

> This endpoint returns JSON structured like this:

```json
[
	{
		"name": "name1",
		"version": "1.0",
		"startDate": "2017-04-25 22:38:54.0",
		"duration": "23",
		"status": "SUCCEEDED",
		"versionId": "fdjskaf2-jfd9-54sw-nge3-34s2432i874de3",
		"count": "",
		"coverage": "",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "fdjskaf2-jfd9-54sw-nge3-34s2l32i874de3",
		"processType": "DEPLOY",
		"templateMode": "iOS"
	}
]
```

This endpoint gets all UrbanCode app deploys for a given time period.

### HTTP Request

`GET /insights/deploys/apps`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## Service Deploys

> This endpoint returns JSON structured like this:

```json
[
	{
		"name": "name1",
		"version": "1.0",
		"startDate": "2017-04-25 22:38:54.0",
		"duration": "23",
		"status": "SUCCEEDED",
		"versionId": "fdjskaf2-jfd9-54sw-nge3-34s2432i874de3",
		"count": "",
		"coverage": "",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "fdjskaf2-jfd9-54sw-nge3-34s2l32i874de3",
		"processType": "DEPLOY",
		"templateMode": "iOS"
	}
]
```

This endpoint gets all UrbanCode service deploys for a given time period.

### HTTP Request

`GET /insights/deploys/services`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## All Application Components

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "component1",
		"templateMode": "iOS"
	},
	{
		"componentName": "component2",
		"templateMode": "mff.adapter"
	}
]
```

This endpoint returns a list of all components for a given UrbanCode application

### HTTP Request

`GET /insights/application/components/all`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Urbancode application name


## App Application Components

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "component1",
		"templateMode": "iOS"
	}
]
```

This endpoint returns a list of app components for a given UrbanCode application

### HTTP Request

`GET /insights/application/components/apps`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Urbancode application name


## Service Application Components

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "component1",
		"templateMode": "mff.adapter"
	}
]
```

This endpoint returns a list of service components for a given UrbanCode application

### HTTP Request

`GET /insights/application/components/services`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Urbancode application name


## App Static Issues

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "component1",
		"versionName": "1",
		"staticIssuesTotal": "7252",
		"staticCriticalIssuesTotal": "353",
		"versionCreated": "2017-03-17T15:28:20.805Z"
	}
]
```

This endpoint gets a list of static issues for app component versions of a given UrbanCode application for a given time period

### HTTP Request

`GET /insights/issues/static/apps`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## Service Static Issues

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "component1",
		"versionName": "1",
		"staticIssuesTotal": "7252",
		"staticCriticalIssuesTotal": "353",
		"versionCreated": "2017-03-17T15:28:20.805Z"
	}
]
```

This endpoint gets a list of static issues for service component versions of a given UrbanCode application for a given time period

### HTTP Request

`GET /insights/issues/static/services`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## App Compilation Issues

> This endpoint returns JSON structured like this:

```json
{
		"componentName": "name1",
		"versionName": "1",
		"versionCreated": "2017-04-25T16:30:13.685Z",
		"compileErrors": "0",
		"compileWarnings": "873",
		"templateMode": "iOS"
	}
]
```

This endpoint gets a list of compilation issues for app component versions of a given UrbanCode application within a given time period.

### HTTP Request

`GET /insights/issues/compilation/apps`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Urbancode application name
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## App Test Summaries

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "component",
		"versionName": "1",
		"testCoverageResult": "0.10575830936431885",
		"unitTestTotal": "3",
		"unitTestFailures": "3",
		"uiTestTotal": "0",
		"uiTestFailures": "0",
		"versionCreated": "2017-03-16T03:47:25.609Z"
	}
]
```

This endpoint gets a list of test summaries for app component versions of a given UrbanCode application within a given time period.

### HTTP Request

`GET /insights/tests/summary/apps`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Urbancode application name
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.


## Service Test Summaries

> This endpoint returns JSON structured like this:

```json
[
	{
		"componentName": "Component1",
		"versionName": "1",
		"testCoverageResult": "0.3",
		"unitTestTotal": "2",
		"unitTestFailures": "0",
		"uiTestTotal": "",
		"uiTestFailures": "",
		"versionCreated": "2017-04-19T15:32:23.685Z"
	}
]
```

This endpoint gets a list of test summaries for service component versions of a given UrbanCode application within a given time period.

### HTTP Request

`GET /insights/tests/summary/services`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Urbancode application name
days | false | Number of days to retrieve builds for. If not specified, defaults to 7.

# Scorecard

Here we have endpoints for Boomerang Scorecard.

## Component Versions

> This command returns JSON structured like this:

```json
[
	{
		"templateMode": null,
		"id": "8b32994c-e758-4a11-9s16-0f30fswb984b",
		"name": "version1",
		"previousVersionName": null,
		"versionArtifactList": null,
		"versionArtifactListPrevious": null
	}
]
```

This endpoint gets all versions for a given UrbanCode component.

### HTTP Request

`GET /scorecard/urbancode/component/version`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name or ID of UrbanCode component

## Application Components

> This command returns JSON structured like this:

```json
[
	{
		"name": "component1",
		"id": "86113ad5-9l3c-4ctr-88ca-aeaa1ab71d0a",
		"mode": "iOS"
	}
]
```

This endpoint gets components for a given UrbanCode application.

### HTTP Request

`GET /scorecard/urbancode/application/components`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
application | true | Name of UrbanCode application

## All applications

> This command returns a list of all UrbanCode applications:

```json
[
	{
		"name": "Mobile@Scale - app1",
		"id": "0f032e85-5fc8-4580-bf19-6c9f04f854da",
		"shortName": "app1"
	}
]
```

This endpoint gets all UrbanCode applications that start with the urbancode.application.type that is set within application.properties in the Scorecard Service.

### HTTP Request

`GET /scorecard/urbancode/applications`

### Query Parameters

none

## Version Statuses

> This command returns JSON structured like this:

```json
[
	{
		"id": "f1aa4219-a29f-4f49-83a1-24d190754f3d",
		"type": "VERSION",
		"name": "statusName",
		"description": "",
		"deleted": false,
		"color": "#17AF4B",
		"unique": false,
		"created": 1487354119456,
		"user": "user1"
	}
]
```

This endpoint gets all statuses for a given UrbanCode version.

### HTTP Request

`GET /scorecard/urbancode/component/version/status`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version

## Download Artifact

This endpoint downloads a given artifact from artifactory for a given component version.

### HTTP Request

`GET /scorecard/urbancode/artifact/download`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 
artifact | true | Name of artifact on artifactory 

## Display Artifact Contents

> This command returns a String containing the contents of the specified artifactory file:

This endpoint displays the contents of a given artifact from artifactory for a given component version.

### HTTP Request

`GET /scorecard/urbancode/artifact/display`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 
artifact | true | Name of artifact on artifactory 

## Build Logs

> This command returns JSON structured like this:

```json
[
	{
	"buildLog":null,
	"buildLogName":"buildLog.log"
	}
]
```

This endpoint gets a list of all build logs for a given component version.

### HTTP Request

`GET /scorecard/logs/list`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version

## Static Test Data

> This command returns JSON structured like this:

```json
{
	"staticIssuesTotal": 6,
	"staticCriticalIssuesTotal": 55,
	"staticFilesTotal": 3,
	"sonarQubeUrl": "http://www.example.com",
	"component": "componentName"
}
```

This endpoint gets info from TestStaticReport.json on artifactory for a given component version.

### HTTP Request

`GET /scorecard/report/static/test`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version

## Coverage Report Data

> This command returns JSON structured like this:

```json
[
	{
		"name": "CoverageReport1.json",
		"report": "contents of CoverageReport1.json"
	}
]
```

This endpoint returns a list of all coverage reports on artifactory for a given component version.

### HTTP Request

`GET /scorecard/report/coverage`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version

## Test Execution Report

> This command returns a String containing the contents of TestExecutionReport.json on artifactory:

This endpoint displays the contents of a TestExecutionReport.json from artifactory for a given component version.

### HTTP Request

`GET /scorecard/report/test/execution`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 

## New Relic Crash Count

> This command returns JSON structured like this:

```json
{
"count":1
}
```

This endpoint returns a the number of crashes from New Relic for a given app version.

### HTTP Request

`GET /scorecard/newrelic/crashes`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
appName | true | Name of app on New Relic
versionName | true | Name of version on New Relic

## Compilation Report

> This command returns JSON structured like this:

```json
{
	"compile_warnings": [
		{
			"file_name": "File.swift",
			"file_path": "/Users/workeradmin/Documents/Workspace/",
			"reason": "initialization of immutable value 'words' was never used; consider replacing with assignment to '_' or removing it",
			"line": "                let words = self.breakupWords(newTranscription: message)",
			"cursor": "                ~~~~^~~~~"
		}
		
	],
	"compile_errors": [
		{
			"file_name": "File2.swift",
			"file_path": "/Users/admin/Documents/Workspace/Pods",
			"reason": "variable 'i' was never mutated; consider changing to 'let' constant",
			"line": "                        for var i in (0..<self.lines.count)",
			"cursor": "                            ~~~ ^"
		}
	]
}
```

This endpoint returns information extracted from CompilationReport.json on artifactory.

### HTTP Request

`GET /scorecard/report/compilation`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 

## Compilation Summary Report

> This command returns JSON structured like this:

```json
{
	"compilationSummaryReport": {
		"compile_warnings": 60,
		"warnings": 0,
		"ld_warnings": 0,
		"errors": 0,
		"compile_errors": 0,
		"file_missing_errors": 0,
		"undefined_symbols_errors": 0,
		"duplicate_symbols_errors": 0,
		"tests_summary_messages": 0
	},
	"reportExists": true
}
```

This endpoint returns information extracted from CompilationSummaryReport.json on artifactory.

### HTTP Request

`GET /scorecard/report/compilation/summary`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 

## Analyzed Summary Reports

> This command returns JSON structured like this:

```json
{
	"analyzedAppReportSummaryList": [
		{
			"versionCreatedDate": "2017-04-17T21:48:03.235Z",
			"versionStatuses": [
				"status1"
			],
			"app": "Mobile@Scale - Component",
			"shortAppName": "Component",
			"testCoverage": "0.10640713572502136",
			"failureCount": "0",
			"unitCoverage": "0.0",
			"uiCoverage": "",
			"version": "release-50",
			"retrievalTime": "11:13:47",
			"codeViolations": "2503",
			"criticalCodeViolations": "137",
			"testCoverageTrend": "",
			"failureCountTrend": "equal",
			"unitCoverageTrend": "",
			"uiCoverageTrend": "",
			"codeViolationsTrend": "up",
			"criticalCodeViolationsTrend": "equal",
			"compileWarnings": "70",
			"compileWarningsTrend": "equal",
			"compileErrors": "0",
			"compileErrorsTrend": "equal",
			"templateMode": "iOS"
		}
	],
	"analyzedServiceReportSummaryList": [
		{
			"versionCreatedDate": "2017-04-24T21:37:07.513Z",
			"unitCoverage": "1.0",
			"unitCoverageTrend": "",
			"templateMode": "mff.adapter",
			"testCoverageResult": "0.002",
			"testCoverageResultTrend": "up",
			"staticViolations": "89",
			"staticViolationsTrend": "up",
			"staticCriticalViolations": "5",
			"staticCriticalViolationsTrend": "up",
			"versionStatuses": [
				"status1"
			],
			"service": "Mobile@Scale - Component",
			"shortServiceName": "Component",
			"version": "1"
		}
	]
}
```

This endpoint returns analyzed summary reports for both services and apps.

### HTTP Request

`GET /scorecard/report/summary/analyzed/list`

### Query Parameters

none

## App Summary Report

> This command returns JSON structured like this:

```json
{
	"testSummaryReport": {
		"testCoverageResult": "0.10575830936431885",
		"unitTestTotal": "3",
		"unitTestFailures": "3",
		"uiTestTotal": "0",
		"uiTestFailures": "0"
	},
	"testStaticReport": {
		"staticIssuesTotal": "2505",
		"staticCriticalIssuesTotal": "137",
		"staticFilesTotal": "79",
		"sonarQubeUrl": "https://www.example.com/sonarqube",
		"component": null
	},
	"compilationSummaryReportPacket": {
		"compilationSummaryReport": {
			"compile_warnings": 60,
			"warnings": 0,
			"ld_warnings": 0,
			"errors": 0,
			"compile_errors": 0,
			"file_missing_errors": 0,
			"undefined_symbols_errors": 0,
			"duplicate_symbols_errors": 0,
			"tests_summary_messages": 0
		},
		"reportExists": true
	}
}
```

This endpoint returns a summary report for an app.

### HTTP Request

`GET /scorecard/app/report/summary`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 

## Service Summary Report

> This command returns JSON structured like this:

```json
{
	"testSummaryReport": {
		"testCoverageResult": "0.488",
		"unitTestTotal": "2",
		"unitTestFailures": "0",
		"uiTestTotal": null,
		"uiTestFailures": null
	},
	"testStaticReport": {
		"staticIssuesTotal": "2",
		"staticCriticalIssuesTotal": "1",
		"staticFilesTotal": "13",
		"sonarQubeUrl": "https://www.example.com/sonarqube",
		"component": {
			"id": "AVt09-V6tIjLmFDrWYR-",
			"key": "67095439-fafs-4e43-96ac-14f6ae6d2aed",
			"name": "Component",
			"qualifier": "TRK",
			"measures": [
				{
					"metric": "staticCriticalIssuesTotal",
					"value": "2"
				}
			]
		}
	},
	"compilationSummaryReportPacket": {
		"compilationSummaryReport": {
			"compile_warnings": 0,
			"warnings": 0,
			"ld_warnings": 0,
			"errors": 0,
			"compile_errors": 0,
			"file_missing_errors": 0,
			"undefined_symbols_errors": 0,
			"duplicate_symbols_errors": 0,
			"tests_summary_messages": 0
		},
		"reportExists": false
	}
}
```

This endpoint returns a summary report for a service.

### HTTP Request

`GET /scorecard/service/report/summary`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 

## Test Summary Report

> This command returns JSON structured like this:

```json
{
	"testCoverageResult": "0.07069088518619537",
	"unitTestTotal": "3",
	"unitTestFailures": "0",
	"uiTestTotal": "1",
	"uiTestFailures": "0"
}
```

This endpoint returns a Test Summary Report for a given component version.

### HTTP Request

`GET /scorecard/report/test/summary`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Name of UrbanCode component
version | true | Name of component version 
