![diagram](https://cdn.rawgit.com/evfurman/fastly-log-publisher/12b4282a/diagram.svg)

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

`sam deploy --template-file ./fastly-log-publisher.yaml --stack-name $STACK_NAME --capabilities CAPABILITY_IAM --parameter-overrides $(cat parameter-overrides.txt)`
