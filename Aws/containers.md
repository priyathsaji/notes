---
title: Containers
date: "2020-09-06T18:47:00.000Z"
description: "Containers"
---


# ECS - Elastic Container Service
- launch docker containers on AWS
- you must provision and maintain the infrastructure
- aws take care or starting and stoping containers
- has integrations with application load balencer


# Fargate
- we dont need to explictly provission ec2 instances
- serverless offering
- aws run the containers based on cpu and ram you need
- an **ENI - Elastic Network Interface** is assigned to each task


## Ec2 Intance profile
- used by ecs agent running on ec2
- make api calls to ecs service
- send container logs to cloud watch logs
- pull docker image from ecr
- reference sensitive data in secret manager or ssm parameter store

## ECS task role
- allow each taks to have a specific role
- use different roles for the different ECS services you run
- defined in **Task definition**

> ECS task can be invoked by Event Bridge. usecase : if you want to invoke a fargate task on upload of object in s3
> - publish an event to amazon event bridge
> - event bridge rule to run ECS task


## ECS scalling
- two kinds of scalling
- services scalling
    - trigger a clound watch alarm based on cpu usage or other metric
    - use this alarm to deploy new task or remove tasks
- underlying instance scalling
 - in case of scalling if the instance cannot support calling
 - can use **ECS capacity provider** to start new ec2 instances via Autoscalling groups (ec2)
 - this is in case if we r not using fargate


 ## ECS Rolling updates
 - when updating version 1 to version 2, we can control how many tasks can be started and stopped and in which order
 - this can be done using 
    - minimum healthy percent
        - minimum percentage of tasks that has to be running during upgrade
    - maximum healthy percent
        - maximum percentage of new task can be started.

# EKS - Elastic Kubernetes Service
- to launch kubernetes cluster on aws
- kubernetes is open-source system for automatic deployment, scaling and management of containerized application
- alternative of ECS, similar goal to ECS
- EKS supports EC2 if you want to deploy works nodes or Fargate to deploy serverless containers









