﻿# Cloud Formation
Trambo Cloud- Exercise with Lmbda, Dynamo DB and Api Gateway
### Author: Jhosef Omar Cáceres Aguilar

The architecture has a database in DynamoDB whit a table for register peoples, 3 lambda functions. The first Lambda function if for insert new item in database with parameter dpi and name, the second function is for get all items from database and the latest function if for delete specific item. The lambda functions was developed whit python and  AWS CLI


# DynamoDB
Template generate a table in DynamoDB

## Parameters

| Parameter | Description | Type 
| :--- | :---- | :----  
| TableName | Is the table name  | String    

## Resources

| Resource | Description | Type 
| :--- | :---- | :----  
| DynamoDBTable | Table in DynamoDB| AWS::DynamoDB::Table    

## Outputs

| Name | Description 
| :--- | :----   
| DynamoDBTable | A reference to the DynamoDB table containing all generated events 




# Lambda Functions
Template generate 3 lambda functions. The first Lambda function if for insert new item in database with parameter dpi and name, the second function is for get all items from database and the latest function if for delete specific item.




## Parameters

| Parameter | Description | Type 
| :--- | :---- | :----  
| TableName | Is the table name  | String    

## Resources

| Resource | Description | Type 
| :--- | :---- | :----  
| LambdaExecutionRole | Access from lambda function for work whit DynamoDB | AWS::IAM::Role   
| PostFunction | insert new item in database with parameter dpi and name| AWS::Lambda::Function  
| GetFunction | Get all items from database| AWS::Lambda::Function 
| DeleteFunction | delete specific item| AWS::Lambda::Function 

## Outputs

| Name | Description 
| :--- | :----   
| GetFunction | Function for get all items from DynamoDB
| ArnPostFunction | Arn the lambda function for insert
| ArnGetFunction | Arn the lambda function for get all items
| ArnDeleteFunction | Arn the lambda function for delete specific item

# Api Gateway
Template generate Api Gateway that act as a “front door” in our aplication 

## Parameters

| Parameter | Description | Type 
| :--- | :---- | :----  
| ArnPostFunction | Arn the lambda function for insert | string
| ArnGetFunction | Arn the lambda function for get all items | string
| ArnDeleteFunction | Arn the lambda function for delete specific  | string

## Resources

| Resource | Description | Type 
| :--- | :---- | :----  
| RestApi | Rest api| AWS::ApiGateway::RestApi    
| GetResource | Path for get items|AWS::ApiGateway::Resource   
| GetMethod |  Function for get all items from DynamoDB| AWS::ApiGateway::Method 
| PostResource | Path for insert| AWS::ApiGateway::Resource   
| PostMethod |  insert new item in database with parameter dpi and name| AWS::ApiGateway::Method  
| DeleteResource | Path for delete| AWS::ApiGateway::Resource   
| DeleteMethod | delete specific item| AWS::ApiGateway::Method   
| apiGatewayDeployment | Delevery in production eviroment | AWS::ApiGateway::Deployment
| ApiGatewayIamRole | permissions to acces lambda functions from api gateway| AWS::IAM::Role 




# Diagram of the architecture
![Diagram](AWS.png)
 
