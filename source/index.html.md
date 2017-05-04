---
title: Boomerang Platform API Reference
---

# Introduction

Welcome to the Boomerang Platform REST API! We have a list of endpoints and parameters, along with a sample json response in the dark area to the right.

-------------
# CI

Here we have endpoints for Boomerang CI.

### HTTP Request

`POST /ci/auth`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
code | true | Code obtained from Github Enterprise to authorize

> This endpoint returns JSON structured like this:

```json
[
	{
		"access_token": "e72e16c7e42f292c6912e7710c838347ae178b4a",
		"scope": "user%2Cgist",
		"token_type": "bearer"
	}
]
```
This endpoint calls Github Enterprise which returns an authorization token to the BoomerangCi app.

### HTTP Request

`GET /ci/repo`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
token | true | Github auth token
owner | false | Name of owning github organization. If not specified, defaults to "".
repo | true | Name of Github repository.

> This endpoint returns JSON structured like this:

```json
[
	{
		"repoFullName": "GBS-AIC-MobileScale/mff_adapter_test",
		"buildNumber": "27",
		"componentStartDate": "2017-04-26 19:56:47.0",
		"componentDuration": "111",
		"componentStatus": "SUCCEEDED",
		"admin": true,
		"componentId": "bf8ee96e-e7da-4f8f-9254-692a7d54804c",
		"componentProcessType": "BUILD",
		"mode": "mff.adapter"
	}
]
```

This endpoint get associated information for a specific repository.

### HTTP Request

`GET /ci/repos`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
token | true | Github auth token
page | false | Page number of repositories returned (sets of 15). If not specified, defaults to 1.

> This endpoint returns JSON structured like this:

```json
[
	{
		"repoFullName": "GBS-AIC-MobileScale/WatsonTelephoneGame",
		"buildNumber": "50",
		"componentStartDate": "2017-04-21 21:11:13.0",
		"componentDuration": "111",
		"componentStatus": "SUCCEEDED",
		"admin": true,
		"componentId": "86113ad5-92dc-4cd8-88ca-aedd1ab71d0a",
		"componentProcessType": "BUILD",
		"mode": "iOS"
	}, {
		"repoFullName": "GBS-AIC-MobileScale/unitedairlines-onboardfoodsales",
		"buildNumber": "35",
		"componentStartDate": "2017-05-04 12:32:19.0",
		"componentDuration": "107",
		"componentStatus": "SUCCEEDED",
		"admin": true,
		"componentId": "11aaa303-623b-4635-8a68-a194a04c91ff",
		"componentProcessType": "BUILD",
		"mode": "iOS"
	}
]
```

This endpoint get associated information for all repository a Github auth token has access.

### HTTP Request

`GET /ci/webhook/find`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
token | true | Github auth token
owner | false | Name of owning github organization. If not specified, defaults to "".
repo | true | Name of Github repository.

> This endpoint returns JSON structured like this:

```json
[
	{
		"id": 1,
		"url": "https://api.github.com/repos/octocat/Hello-World/hooks/1",
		"test_url": "https://api.github.com/repos/octocat/Hello-World/hooks/1/test",
		"ping_url": "https://api.github.com/repos/octocat/Hello-World/hooks/1/pings",
		"name": "web",
		"events": [
		"push",
		"pull_request"
		],
		"active": true,
		"config": {
		"url": "http://example.com/webhook",
		"content_type": "json"
		},
		"updated_at": "2011-09-06T20:39:23Z",
		"created_at": "2011-09-06T17:26:27Z"
	}
]
```

This endpoint returns information about a webhook that matches https://services.boomerangplatform.net/webhook/payload.

### HTTP Request

`GET /ci/webhook/create`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
token | true | Github auth token
owner | false | Name of owning github organization. If not specified, defaults to "".
repo | true | Name of Github repository.

> This endpoint returns JSON structured like this:

```json
[
	{
		"id": 1,
		"url": "https://api.github.com/repos/octocat/Hello-World/hooks/1",
		"test_url": "https://api.github.com/repos/octocat/Hello-World/hooks/1/test",
		"ping_url": "https://api.github.com/repos/octocat/Hello-World/hooks/1/pings",
		"name": "web",
		"events": [
		"push",
		"pull_request"
		],
		"active": true,
		"config": {
		"url": "http://example.com/webhook",
		"content_type": "json"
		},
		"updated_at": "2011-09-06T20:39:23Z",
		"created_at": "2011-09-06T17:26:27Z"
	}
]
```

This endpoint returns a list of app components for a given UrbanCode application

### HTTP Request

`GET /ci/component/activities/latest`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
componentId | true | Urbancode Component id of the component to find activity

> This endpoint returns JSON structured like this:

```json
[
	{
		"name": "Mobile@Scale - IBM - WatsonTelephoneGame",
		"version": "release-38",
		"startDate": "2017-03-29 18:10:22.0",
		"duration": "130",
		"status": "SUCCEEDED",
		"versionId": "cf8c5f69-9dae-464d-a926-09fd17901a8a",
		"count": "",
		"coverage": "",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "d1bf09cf-3662-4142-9d33-a2e9a0b5c96c",
		"processType": "BUILD",
		"gitCommitId": "329372687fe5954c0cb6fda95ae81058cb2b9173",
		"gitCommitMessage": "Updated+to+reflect+latest+Boomerang+property+reqs",
		"gitAuthorName": "TYSON W. LAWRIE"
	}
]
```

This endpoint returns the latest activity for the given component.

### HTTP Request

`GET /ci/component/activities`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
componentId | true | Urbancode Component id of the component to find activity
activityType | false | Type of activity to retrieve (all,build,test,deploy). If not specified, defaults to "".

> This endpoint returns JSON structured like this:

```json
[
	{
		"name": "Mobile@Scale - IBM - WatsonTelephoneGame",
		"version": "release-38",
		"startDate": "2017-04-03 20:01:12.0",
		"duration": "121",
		"status": "SUCCEEDED",
		"versionId": "cf8c5f69-9dae-464d-a926-09fd17901a8a",
		"count": "",
		"coverage": "",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "bb61214a-c308-42fc-b80e-4e1c679cab72",
		"processType": "BUILD",
		"gitCommitId": "329372687fe5954c0cb6fda95ae81058cb2b9173",
		"gitCommitMessage": "Updated+to+reflect+latest+Boomerang+property+reqs",
		"gitAuthorName": "TYSON W. LAWRIE"
		
	}
]
```

This endpoint returns the all specified activity of a given type (all,build,test,deploy) for the given component.

### HTTP Request

`GET /ci/component/application`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Urbancode component id

> This endpoint returns JSON structured like this:

```json
[
	{
		"applications": [{
		"templateId": "9e7be725-6ec6-4f67-b84a-8d85996138a9",
		"tags": [],
		"id": "0f048385-5fc8-42d0-bf19-6c9f04f854da",
		"templateVersion": "-1",
		"securityResourceId": "b03460c2-873f-451d-8c3a-3555473aeef5",
		"created": "1488896772201",
		"description": "",
		"name": "Mobile@Scale - IBM",
		"active": "true",
		"user": "Application Innovation Admin (aiadmin)",
		"deleted": "false",
		"enforceCompleteSnapshots": "false"
		}]
	}
]
```

This endpoint gets the application associated with a given component.

### HTTP Request

`GET /ci/application/environment`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
applicationName | true | Urbancode application name

> This endpoint returns JSON structured like this:

```json
{
		"noSelfApprovals": "false",
		"calendarId": "7cec31bc-0b54-4f4c-9edf-d75589a83a90",
		"securityResourceId": "cc9bb957-109b-435d-ad4d-5ef58e7095c8",
		"requireApprovals": "false",
		"cleanupCountToKeep": "0",
		"deleted": "false",
		"useSystemDefaultDays": "true",
		"conditions": [],
		"id": "7164e419-3369-4d5c-b72a-cfd22f934066",
		"lockSnapshots": "false",
		"color": "#00B2EF",
		"description": "",
		"name": "DEVELOPMENT",
		"cleanupDaysToKeep": "0",
		"active": "true",
		"historyCleanupDaysToKeep": "365",
		"enableProcessHistoryCleanup": "false"
	}
]
```

This endpoint gets the latest environment stored in an array of the associated application.

### HTTP Request

`GET /ci/component/deploys/latest`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
componentId | true | Urbancode component id

> This endpoint returns JSON structured like this:

```json
{
		"name": "Mobile@Scale - IBM - WatsonTelephoneGame",
		"version": "release-38",
		"startDate": "2017-03-28 14:19:53.0",
		"duration": "38",
		"status": "SUCCEEDED",
		"versionId": "cf8c5f69-9dae-464d-a926-09fd17901a8a",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "4722e777-7756-4113-b7d4-6401180169e6"
	}
]
```

This endpoint gets the latest deploy for the specified component.

### HTTP Request

`GET /ci/component/deploys`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
componentId | true | Urbancode component id

> This endpoint returns JSON structured like this:

```json
[
	{
		"name": "Mobile@Scale - IBM - WatsonTelephoneGame",
		"version": "release-38",
		"startDate": "2017-03-28 14:19:53.0",
		"duration": "38",
		"status": "SUCCEEDED",
		"versionId": "cf8c5f69-9dae-464d-a926-09fd17901a8a",
		"environment": "DEVELOPMENT",
		"applicationProcessId": "4722e777-7756-4113-b7d4-6401180169e6"
	}
]
```

This endpoint gets all deploy for the specified component.

### HTTP Request

`PUT /ci/process/create`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
componentId | true | Urbancode component id
versionId | true | Urbancode version id of the component

> This endpoint returns JSON structured like this:

```json
[
	{
		"requestId": "f7e7b00d-8ea6-4a95-ad74-0ff853125232"
	}
]
```

This endpoint runs an application process for the given component id and version id in UrbanCode Deploy.

### HTTP Request

`GET /ci/find/application/name`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Urbancode component id
------------------------

> This endpoint returns JSON structured like this:

```List of Strings
[
	"Mobile@Scale - IBM"
]
```
This endpoint gets a list application names for a given component.

### HTTP Request

`GET /ci/find/application/id`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
component | true | Urbancode component id
------------------------

> This endpoint returns JSON structured like this:

```List of Strings
[
	"0f048385-5fc8-42d0-bf19-6c9f04f854da"
]
```
This endpoint gets a list application ids for a given component.

### HTTP Request

`GET /ci/version/artifact/download`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
componentName | true | Urbancode component name
versionName | true | Urbancode version name
artifactName | true | Urbancode artifact name (ie. build log)
------------------------

> This endpoint returns a txt document.
This endpoint downloads the specified artifact of the given component and version.

# Webhook

Here we have one endpoint for Boomerang Webhook.

### HTTP Request

`POST /webhook/payload`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
payload | true | Payload delivery from Github triggered from a push to a repository

> This endpoint returns JSON structured like this:

```json
[
	{
	  "ref": "refs/heads/release",
	  "before": "2d44998d9b0e2fb77a5021d17a3139df3756e1df",
	  "after": "af5b42dc5f7333e9d644707068deb7a60d3fa288",
	  "created": false,
	  "deleted": false,
	  "forced": false,
	  "base_ref": null,
	  "compare": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame/compare/2d44998d9b0e...af5b42dc5f73",
	  "commits": [
	    {
	      "id": "af5b42dc5f7333e9d644707068deb7a60d3fa288",
	      "tree_id": "0c3abe70eca38d1ce1e2e3976c33523890f2f478",
	      "distinct": true,
	      "message": "Update .boomerang.properties",
	      "timestamp": "2017-04-04T15:48:01-05:00",
	      "url": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame/commit/af5b42dc5f7333e9d644707068deb7a60d3fa288",
	      "author": {
		"name": "RACHEL L. RODDEN",
		"email": "rlrodden@us.ibm.com",
		"username": "rlrodden"
	      },
	      "committer": {
		"name": "GitHub Enterprise",
		"email": "noreply@github.ibm.com"
	      },
	      "added": [

	      ],
	      "removed": [

	      ],
	      "modified": [
		"_boomerang/.boomerang.properties"
	      ]
	    }
	  ],
	  "head_commit": {
	    "id": "af5b42dc5f7333e9d644707068deb7a60d3fa288",
	    "tree_id": "0c3abe70eca38d1ce1e2e3976c33523890f2f478",
	    "distinct": true,
	    "message": "Update .boomerang.properties",
	    "timestamp": "2017-04-04T15:48:01-05:00",
	    "url": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame/commit/af5b42dc5f7333e9d644707068deb7a60d3fa288",
	    "author": {
	      "name": "RACHEL L. RODDEN",
	      "email": "rlrodden@us.ibm.com",
	      "username": "rlrodden"
	    },
	    "committer": {
	      "name": "GitHub Enterprise",
	      "email": "noreply@github.ibm.com"
	    },
	    "added": [

	    ],
	    "removed": [

	    ],
	    "modified": [
	      "_boomerang/.boomerang.properties"
	    ]
	  },
	  "repository": {
	    "id": 105093,
	    "name": "WatsonTelephoneGame",
	    "full_name": "GBS-AIC-MobileScale/WatsonTelephoneGame",
	    "owner": {
	      "name": "GBS-AIC-MobileScale",
	      "email": null
	    },
	    "private": true,
	    "html_url": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame",
	    "description": null,
	    "fork": false,
	    "url": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame",
	    "forks_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/forks",
	    "keys_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/keys{/key_id}",
	    "collaborators_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/collaborators{/collaborator}",
	    "teams_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/teams",
	    "hooks_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/hooks",
	    "issue_events_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/issues/events{/number}",
	    "events_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/events",
	    "assignees_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/assignees{/user}",
	    "branches_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/branches{/branch}",
	    "tags_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/tags",
	    "blobs_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/git/blobs{/sha}",
	    "git_tags_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/git/tags{/sha}",
	    "git_refs_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/git/refs{/sha}",
	    "trees_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/git/trees{/sha}",
	    "statuses_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/statuses/{sha}",
	    "languages_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/languages",
	    "stargazers_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/stargazers",
	    "contributors_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/contributors",
	    "subscribers_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/subscribers",
	    "subscription_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/subscription",
	    "commits_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/commits{/sha}",
	    "git_commits_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/git/commits{/sha}",
	    "comments_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/comments{/number}",
	    "issue_comment_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/issues/comments{/number}",
	    "contents_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/contents/{+path}",
	    "compare_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/compare/{base}...{head}",
	    "merges_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/merges",
	    "archive_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/{archive_format}{/ref}",
	    "downloads_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/downloads",
	    "issues_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/issues{/number}",
	    "pulls_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/pulls{/number}",
	    "milestones_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/milestones{/number}",
	    "notifications_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/notifications{?since,all,participating}",
	    "labels_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/labels{/name}",
	    "releases_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/releases{/id}",
	    "deployments_url": "https://github.ibm.com/api/v3/repos/GBS-AIC-MobileScale/WatsonTelephoneGame/deployments",
	    "created_at": 1484686125,
	    "updated_at": "2017-02-07T16:41:22Z",
	    "pushed_at": 1491338882,
	    "git_url": "git://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame.git",
	    "ssh_url": "git@github.ibm.com:GBS-AIC-MobileScale/WatsonTelephoneGame.git",
	    "clone_url": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame.git",
	    "svn_url": "https://github.ibm.com/GBS-AIC-MobileScale/WatsonTelephoneGame",
	    "homepage": null,
	    "size": 2913,
	    "stargazers_count": 0,
	    "watchers_count": 0,
	    "language": "Swift",
	    "has_issues": true,
	    "has_downloads": true,
	    "has_wiki": true,
	    "has_pages": false,
	    "forks_count": 0,
	    "mirror_url": null,
	    "open_issues_count": 0,
	    "forks": 0,
	    "open_issues": 0,
	    "watchers": 0,
	    "default_branch": "master",
	    "stargazers": 0,
	    "master_branch": "master",
	    "organization": "GBS-AIC-MobileScale"
	  },
	  "pusher": {
	    "name": "rlrodden",
	    "email": "rlrodden@us.ibm.com"
	  },
	  "organization": {
	    "login": "GBS-AIC-MobileScale",
	    "id": 42346,
	    "url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale",
	    "repos_url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale/repos",
	    "events_url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale/events",
	    "hooks_url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale/hooks",
	    "issues_url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale/issues",
	    "members_url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale/members{/member}",
	    "public_members_url": "https://github.ibm.com/api/v3/orgs/GBS-AIC-MobileScale/public_members{/member}",
	    "avatar_url": "https://avatars.github.ibm.com/u/42346?",
	    "description": null
	  },
	  "sender": {
	    "login": "rlrodden",
	    "id": 47417,
	    "avatar_url": "https://avatars.github.ibm.com/u/47417?",
	    "gravatar_id": "",
	    "url": "https://github.ibm.com/api/v3/users/rlrodden",
	    "html_url": "https://github.ibm.com/rlrodden",
	    "followers_url": "https://github.ibm.com/api/v3/users/rlrodden/followers",
	    "following_url": "https://github.ibm.com/api/v3/users/rlrodden/following{/other_user}",
	    "gists_url": "https://github.ibm.com/api/v3/users/rlrodden/gists{/gist_id}",
	    "starred_url": "https://github.ibm.com/api/v3/users/rlrodden/starred{/owner}{/repo}",
	    "subscriptions_url": "https://github.ibm.com/api/v3/users/rlrodden/subscriptions",
	    "organizations_url": "https://github.ibm.com/api/v3/users/rlrodden/orgs",
	    "repos_url": "https://github.ibm.com/api/v3/users/rlrodden/repos",
	    "events_url": "https://github.ibm.com/api/v3/users/rlrodden/events{/privacy}",
	    "received_events_url": "https://github.ibm.com/api/v3/users/rlrodden/received_events",
	    "type": "User",
	    "site_admin": false
	  }
	}
]
```
This endpoint receives a delivered payload from Github Enterprise on a push to a webhook enabled respository.

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
