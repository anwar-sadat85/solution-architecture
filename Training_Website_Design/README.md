# Training website design

 - The following is a high level architecture of an AWS based solution for a training website

 - A headless CMS is used for creating content.

 - The CMS' webhook is used to create / update entires in a DynamoDB table whenever a content entry is created, edited or deleted. The DynamoDB table collects user generated content Eg., likes, comments.

 - Another table is used to stote user profile and prefernces specific to the application.

 - The website is built with Amplify with integrations to Amazon Cognito and Amazon API Gateway.

 - An IAM role based fine grained access is used to read items from the DynamoDB table. The role is assigned by Cognito Identity pool.

 - Cognito user pool is used as IdP and identity pool is used to assign roles to the authenticated user (through temporary credentials) to get and update items in the DynamoDB table.

 - Out of the box search API of the headless CMS is used to fetch the search results. The user generated content is surfaced from DynamoDB table

<img src="Training_Website.drawio.png" alt="Training Website solution" title="Training Website solution">

# AWS Services
 - DynamoDB with Multi AZ support. Data encrypted at rest.
 - DAX Cluster for faster reads.
 - Lambda functions for each service with Multi AZ support (choose same AZs as DynamoDB) inside a VPC in a public subnet 
 - Public subnet with VPC Endpoint for SQS and Gateway Endpoint for Dynamo DB to reduce latency
 - Secrets manager to store configuration parameters for Lambda functions (Eg., CMS API Key)
 - SQS to handle webhooks from Headless CMS - to create entries in DynamoDB for UGC
 - API Gateway
    - Integrations with Lambda functions for the services
        - Cognito Authorizers
    - Integration with SQS for the Headless CMS webhook
        - API Key based authentication
 - Amplify to host the front end app
 - Cognito for user authentication
 - Cloudfront for caching and content distribution
    - AWS Shield for DDoS protection 
 
