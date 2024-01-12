# ECS -get started

### Create a repository

Create a repository to store container images

```bash
aws ecr create-repository --repository-name web-application
```

List repositories

```bash
aws ecr describe-repositories
```

List images for a repository

```bash
aws ecr describe-images --repository-name flask-application
```

Delete repository

```bash 
aws ecr delete-repository --repository-name web-application
```

Delete an image tag

```bash
aws ecr batch-delete-image --repository-name web-application --image-ids imageTag=1.0
```

### Create ECS cluster

Create a cluster named `microservices`

```bash
aws  ecs create-cluster --cluster-name microservices
```

List ECS clusters

```bash
aws ecs list-clusters
```

List ECS container instances

```bash
aws ecs list-container-instances --cluster microservices

# describe container instances
aws ecs describe-container-instances --cluster microservices --container-instances <container_instance_id>
```

List task definitions

```bash
aws ecs list-task-definitions
```

List services

```bash
aws ecs list-services --cluster <value>
```


### Register a Task Definition

Before running a task on ECS cluster, must register a task definition.

The ECS Task Definition
```json
{
  "containerDefinitions": [
    {
      "name": "sleep",
      "image": "busybox",
      "cpu": 10,
      "command": [
        "sleep",
        "360"
      ],
      "memory": 10,
      "essential": true
    }
  ],
  "family": "sleep360"
}
```

Register a task definition
```bash
aws ecs register-task-definition --cli-input-json file://$HOME/tasks/sleep360.json

# or use json string
aws ecs register-task-definition --family sleep360 --container-definitions "[{\"name\":\"sleep\",\"image\":\"busybox\",\"cpu\":10,\"command\":[\"sleep\",\"360\"],\"memory\":10,\"essential\":true}]"
```

### Run a Task 

After registered a task and launched a container instance, you can run the registered task in your cluster.

```bash
aws ecs run-task --cluster default --task-definition sleep360:1 --count 1
```

