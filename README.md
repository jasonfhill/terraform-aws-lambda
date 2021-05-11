# AWS Lambda

Deploy Lambda into VPC or outside of the vpc

## Usage example

Here's the gist of using it via github.

```terraform
module lambda {
  source  = "terraform-module/lambda/aws"
  version = "2.10.0"

  function_name      = "lambda-name-to-deploy"
  filename            = "${path.module}/lambda.zip"
  description        = "description should be here"
  handler            = "index.handler"
  runtime            = "nodejs12.x"
  memory_size        = "128"
  concurrency        = "5"
  lambda_timeout     = "20"
  log_retention      = "1"
  role_arn           = "some-role-arn"
  tracing_config      = { mode = "Active" }

  vpc_config = {
    subnet_ids         = ["sb-q53asdfasdfasdf", "sf-3asdfasdfasdf6"]
    security_group_ids = ["sg-3asdfadsfasdfas"]
  }

  environment = {
    Environment = "test"
  }

  tags = {
    Environment = "test"
  }
}
```
