## ECR image
```sh
# login
aws ecr get-login-password --region XXX | docker login --username AWS --password-stdin XXX.dkr.ecr.XXX.amazonaws.com

# build
docker build -t XXX:dev .

# tag image
docker tag XXX:dev XXX.dkr.ecr.XXX.amazonaws.com/XXX:dev

# push
docker push XXX:dev XXX.dkr.ecr.XXX.amazonaws.com/XXX:dev
```

## ECS cluster
```sh
aws ecs create-cluster --cli-input-json file://aws/dev/cluster.json
```

## Target groups
```sh
# target group 1
aws elbv2 create-target-group --name dev-server-1 --protocol HTTP --port 443 --health-check-path /health --vpc-id vpc-XXX --target-type ip

# target group 2
aws elbv2 create-target-group --name dev-server-2 --protocol HTTP --port 443 --health-check-path /health --vpc-id vpc-XXX --target-type ip
```

## Security group
Check for security group on AWS console with rules allowing inbound traffic on ports
- 80, 8080
- 443, 8443

## Load balancer
Create application load balancer and add listeners

- Listener on port 80 should redirect to HTTPS 443
- Listener on port 443 should forward to target group created earlier
- Listener on port 8080 should redirect to HTTPS 8443
- Listener on port 8443 should forward to target group created earlier

## Task definition
- Create log group in CloudWatch
- Put log group name in task definition
- Create task definition
```sh
aws ecs register-task-definition --cli-input-json file://aws/dev/taskdef-dev.json
```

## Service
```sh
aws ecs create-service --service-name dev-server-service --cli-input-json file://aws/dev/task-service.json
```

## CodeDeploy application
```sh
# create app
aws deploy create-application --cli-input-json file://aws/dev/application.json

# create deployment group
aws deploy create-deployment-group --cli-input-json file://aws/dev/application-deploymentGroup.json
```

## CodeDeploy pipeline
```sh
# create pipeline
aws codepipeline create-pipeline --cli-input-json file://aws/dev/pipeline.json
```

Check detection options
1. Go to CodeDeploy on AWS console
2. Go to Pipelines
3. Select and edit pipeline
4. Click `Edit Stage`
5. Set `Change detection options` to AWS CloudWatch
6. Save

## S3
`artifact.zip` must contain:

- `appspec.yaml`
- `taskdef.json`

Deployment can be triggered if you upload `artifact.zip` to S3. It can be done manually or with bitbucket pipelines.

