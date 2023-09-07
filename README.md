## Serverless 

## This section explains the ```serverless.yml``` 

This YAML configuration is for the Serverless Framework.  It makes it easy to deploy serverless applications on cloud platforms like AWS.  This configuration would create a AWS Lambda function exposed by an HTTP endpoint, and other related AWS resources like an S3 bucket and an API Gateway.

It will also craete unique Function names like ```Group4-prod-Capstone``` and ```Group4-dev-Capstone``` which defines the service name, the stage where it was deployed and the unique function name.

![Screenshot 2023-09-05 at 11 14 06 PM](https://github.com/vincent8055/gp4-vincent/assets/127754761/25e1c2f6-5a3f-498e-b5c5-92762d48bd10)


<details>  


```
service: Group4
frameworkVersion: '3'

provider: 
 name: aws
 runtime: nodejs18.x
 region: ap-southeast-1
 deploymentBucket:
    name: cohort2.serverless.deploys

functions:
  Capstone:  
    handler: index.handler
    events:
    -  httpApi:
        path: /
        method: get
    environment:
      ACCESS_KEY: ${ssm:Group4-Parameter}

#plugins:
#  - serverless-offline

```

 ```service: Group4```

This defines the name of the serverless service.  It gives a unique name to this collection of functions, which is useful for deploying and referencing the stack.

```frameworkVersion: '3'```

The version of the Serverless frameework.  The framework knows which version's rules to follow when deploying the service.

```provider```

Beings the declaration for the cloud service provider-specifc configurations.  

```name: aws```
In this configuration, the spedified cloud provider is AWS and the serverless framework will deploy this service to AWS.

```runtime: nodejs18.x```

Tells the Serverless framework and AWS Lambda to use the Node.js 18.x runtime.

```region: ap-southeast-1```

This line specifies the AWS region for deployment.

```deploymentBucket```

Specify details about the S3 bucket used to deploy to.

```name: cohort2.serverless.deploys```

The name of the S3 bucket to use.  Deployment packages will be stored in this bucket during deployment.

```function```

Begins the declaration of functions in this service.  

```Capstone:```

The unique name for the service 

```handler: index.handler```

This line tells AWS Lambda the code is in the ```index``` file and the function is to execute is named ```handler```.

```events:```

Define triggers for the ```Capstone:``` functions.

```- httpApi:```

To specify that the function will respond will respond to HTTP requests.  

```path: /```

The API endpoint's path is the root.  The serverless framework will know the URL path to configure in AWS API Gateway.

```method: get```

This specifies which HTTP request type will trigger this function.

```environment: ```

This declares the declaration for environment variables for this function.

```ACCESS_KEY: $(ssm:Group4-Parameter)```

This will securely provide the function with a value from the AWS SSM Parameter Store.

</details>

