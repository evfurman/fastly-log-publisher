![diagram](https://raw.githubusercontent.com/evfurman/fastly-log-publisher/master/diagram.jpg)

```mermaid
graph LR;
  fastly-logs[fa:fa-shower fastly access logs]-->s3-bucket[fa:fa-square s3 bucket];
  s3-bucket-->log-publisher-lambda[λ publish];
  log-publisher-lambda-->cw[fa:fa-cogs cloudwatch]

style s3-bucket fill:#FF3333
style fastly-logs fill:#FFFF00
style cw fill:#7ed15d
style log-publisher-lambda fill:#ff9900

```

**The following steps are automated as part of a Gitlab-CI pipeline, but you can also run them manually.**

## Install
The easiest way to install SAM CLI is using pip.  
  
`pip install aws-sam-cli`  
  
https://docs.aws.amazon.com/lambda/latest/dg/sam-cli-requirements.html  

## Validate
  
SAM provides a built-in syntax validator.  
  
`sam validate`  

## Deploy

`sam package --template-file template.yaml --s3-bucket $S3_BUCKET_NAME --output-template-file fastly-log-publisher.yaml`

`sam deploy --template-file ./.fastly-log-publisher.yaml --stack-name $STACK_NAME --capabilities CAPABILITY_IAM --parameter-overrides $(cat parameter-overrides.txt)`
