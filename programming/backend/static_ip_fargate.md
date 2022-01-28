## Subnets
Create public and private subnets for each availability zone ex. us-west-2a, us-west-2b

## Private subnets for ECS tasks
- AWS console VPC
- Create subnets 
- Create private route table
- Go to `Subnet associations`, click edit and add your private subnets

## Public subnets for Application Load Balancer
- AWS console VPC
- Create subnets
- Create internet gateway to make subnet public
- Attach IG to ECS VPC
- Create public route table
- Select created route table and click `Edit routes`
- Add route `destination: 0.0.0.0/0`, `target: igw-xxxx`
- Go to `Subnet associations`, click edit and add your public subnets

## ECS cluster
[Follow this guide and spin up fargate containers and configure deployment](./blue_green_codedeploy.md)

> It is important to add your private subnets to `task-service.json` and `appspec.yaml` and also under network configuration make sure that assignPublicIp is `DISABLED`

## NAT Gateway
- AWS console VPC
- Create NAT gateway
- Attach public subnets to NAT
- Allocate Elastic IP
- Go to route tables
- Edit routes of your `private` route table
- Add route `destination`: `0.0.0.0/0`, `target`: `nat-xxxx`

## Overview
[Simple diagram to show how it works](https://viewer.diagrams.net/?highlight=0000ff&edit=_blank&layers=1&nav=1&title=fargateTask.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2Flxhan%2Fdiagrams%2Fmaster%2FfargateTask.drawio)
