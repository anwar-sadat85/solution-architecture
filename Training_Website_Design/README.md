# Training website design

The following is a high level architecture of an AWS based solution for a training website

A headless CMS is used for creating content.

The CMS' webhook is used to create / update entires in a DynaboDB table whenever a content entry is created, edited or deleted. The DynamoDB table collects user generated content Eg., likes, comments.

The website is built with Amplify with integrations to Amazon Cognito and Amazon API Gateway.

An IAM role based fine grained access is used to read items from the DynamoDB table. The role is assigned by Cognito Identity pool.

Cognito user pool is used as IdP and identity pool is used to assign roles to the authenticated user (through temporary credentials) to get and update items in the DynamoDB table

Out of the box search API of the headless CMS is used to fetch the search results. The user generated content is surfaced from DynamoDB table

<img src="Training_Website.drawio.png" alt="Training Website solution" title="Training Website solution">
